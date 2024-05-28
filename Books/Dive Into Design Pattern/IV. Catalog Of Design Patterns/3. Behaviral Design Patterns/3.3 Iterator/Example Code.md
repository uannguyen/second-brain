
# Structure

```ts
// Interface iterator
interface IInterator<T> {
  getNext(): T | null;
  hasMore(): boolean;
}

// Concrete iterator
class ConcreteIterator<T> implements IInterator<T> {
  private collection: ConcreteCollection<T>;
  private position: number = 0;

  constructor(collection: ConcreteCollection<T>) {
    this.collection = collection;
  }

  public getNext(): T | null {
    if (this.hasMore()) {
      return this.collection.getItems()[this.position++];
    }
    return null;
  }

  public hasMore(): boolean {
    return this.position < this.collection.getItems().length;
  }
}

// Interface Iterable Collection
interface IterableCollection<T> {
  createIterator(): IInterator<T>;
}

// Concrete Collection
class ConcreteCollection<T> implements IterableCollection<T> {
  private items: T[] = [];

  public getItems(): T[] {
    return this.items;
  }

  public addItem(item: T): void {
    this.items.push(item);
  }

  public createIterator(): IInterator<T> {
    return new ConcreteIterator<T>(this);
  }
}

// Client Code
const collection = new ConcreteCollection<number>();
collection.addItem(1);
collection.addItem(2);
collection.addItem(3);

const iterator = collection.createIterator();

while (iterator.hasMore()) {
  console.log(iterator.getNext());
}

```


# Pseudocode

```ts
// The collection interface must declare a factory method for
// producing iterators. You can declare several methods if there
// are different kinds of iteration available in your program.
interface SocialNetwork {
  createFriendsIterator: (profileId: number) => ProfileIterator;
  createCoworkersIterator: (profileId: number) => ProfileIterator;
}

// The common interface for all iterators.
interface ProfileIterator {
  getNext: () => Profile;
  hasMore: () => boolean;
}

// Each concrete collection is coupled to a set of concrete
// iterator classes it returns. But the client isn't, since the
// signature of these methods returns iterator interfaces.
class Facebook implements SocialNetwork {
  // ... The bulk of the collection's code should go here ...

  createFriendsIterator(profileId) {
    return new FacebookIterator(this, profileId, "friends");
  }
  createCoworkersIterator(profileId) {
    return new FacebookIterator(this, profileId, "coworkers");
  }
}

// The concrete iterator class
class FacebookIterator implements ProfileIterator {
  // The iterator needs a reference to the collection that it
  // traverses.
  facebook: Facebook;
  profileId: string;
  type: string;

  // An iterator object traverses the collection independently
  // from other iterators. Therefore it has to store the
  // iteration state.
  currentPosition: number;
  cache: Profile[];

  constructor(facebook, profileId, type) {
    this.facebook = facebook;
    this.profileId = profileId;
    this.type = type;
  }

  private lazyInit() {
    if (this.cache == null) {
      this.cache = this.facebook.socialGraphRequest(this.profileId, this.type);
    }
  }

  hasMore(): boolean {
    this.lazyInit();
    return this.cache.length < this.currentPosition;
  }

  // Each concrete iterator class has its own implementation
  // of the common iterator interface.
  getNext() {
    if (this.hasMore()) {
      this.currentPosition++;
      return this.cache[this.currentPosition];
    }
  }
}

// Here is another useful trick: you can pass an iterator to a
// client class instead of giving it access to a whole
// collection. This way, you don't expose the collection to the
// client.
//
// And there's another benefit: you can change the way the
// client works with the collection at runtime by passing it a
// different iterator. This is possible because the client code
// isn't coupled to concrete iterator classes.
class SocialSpammer {
  send(iterator: ProfileIterator, message: string) {
    while (iterator.hasMore()) {
      profile = iterator.getNext();
      System.sendEmail(profile.getEmail(), message);
    }
  }
}

// The application class configures collections and iterators
// and then passes them to the client code.
class Application {
  network: SocialNetwork;
  spammer: SocialSpammer;

  config(social_type) {
    switch (social_type) {
      case "facebook":
        this.network = new Facebook();

        break;
      case "linkedin":
        this.network = new LinkedIn();

        break;

      default:
        this.spammer = new SocialSpammer();
        break;
    }
  }

  sendSpamToFriends() {
    iterator = network.createFriendsIterator(profile.getId());
    spammer.send(iterator, "Very important message");
  }

  sendSpamToCoworkers(profile) {
    iterator = network.createCoworkersIterator(profile.getId());
    spammer.send(iterator, "Very important message");
  }
}

```
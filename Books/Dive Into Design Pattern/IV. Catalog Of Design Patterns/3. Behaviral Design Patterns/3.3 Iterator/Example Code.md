
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
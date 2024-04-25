
# Structure

- Ví dụ cho việc caching

```ts
// Subject interface
interface Image {
    display(): void;
}

// RealSubject: Concrete implementation of Subject
class RealImage implements Image {
    private filename: string;

    constructor(filename: string) {
        this.filename = filename;
        this.loadFromDisk();
    }

    display(): void {
        console.log(`Displaying image ${this.filename}`);
    }

    private loadFromDisk(): void {
        console.log(`Loading image ${this.filename} from disk`);
    }
}

// Proxy: Proxy class that controls access to the RealSubject
class ProxyImage implements Image {
    private filename: string;
    private realImage: RealImage | null;

    constructor(filename: string) {
        this.filename = filename;
        this.realImage = null;
    }

    display(): void {
        if (!this.realImage) {
            this.realImage = new RealImage(this.filename);
        }
        this.realImage.display();
    }
}

// Client code
const image1 = new ProxyImage("image1.jpg");

// Image will be loaded from disk when display() is called for the first time
image1.display();

// Image will not be loaded again, it will be displayed directly
image1.display();

```

# Factory flyweight

```ts
// Flyweight interface: định nghĩa các phương thức chung cho các flyweight
interface Particle {
    draw(x: number, y: number): void;
}

// Concrete flyweight: cài đặt cụ thể của flyweight
class Bullet implements Particle {
    private color: string;
    private sprite: string;

    constructor(color: string, sprite: string) {
        this.color = color;
        this.sprite = sprite;
    }

    draw(x: number, y: number): void {
        console.log(`Drawing a ${this.color} bullet at (${x}, ${y}) with sprite ${this.sprite}`);
    }
}

// Flyweight factory
class ParticleFactory {
    private flyweights: { [key: string]: Particle } = {};

    getParticle(color: string, sprite: string): Particle {
        const key = `${color}_${sprite}`;
        if (!this.flyweights[key]) {
            this.flyweights[key] = new Bullet(color, sprite);
        }
        return this.flyweights[key];
    }
}

// Client code: sử dụng flyweight và flyweight factory
class Game {
    private particles: Particle[] = [];
    private particleFactory: ParticleFactory;

    constructor(particleFactory: ParticleFactory) {
        this.particleFactory = particleFactory;
    }

    createParticle(color: string, sprite: string, x: number, y: number): void {
        const particle = this.particleFactory.getParticle(color, sprite);
        particle.draw(x, y);
        this.particles.push(particle);
    }
}

// Usage
const particleFactory = new ParticleFactory();
const game = new Game(particleFactory);

// Tạo các hạt với cùng một màu sắc và sprite
game.createParticle('red', 'bullet_sprite', 10, 10);
game.createParticle('red', 'bullet_sprite', 20, 20);

// Tạo các hạt với màu sắc và sprite khác nhau
game.createParticle('blue', 'missile_sprite', 30, 30);
game.createParticle('green', 'shrapnel_sprite', 40, 40);

```


# Implement

## Behavior

```ts
// Flyweight interface
interface Rectangle {
    draw(x: number, y: number): void;
}

// Concrete flyweight: Rectangle implementation
class ConcreteRectangle implements Rectangle {
    private width: number;
    private height: number;
    private color: string;

    constructor(width: number, height: number, color: string) {
        this.width = width;
        this.height = height;
        this.color = color;
    }

    // This method is removed from ConcreteRectangle
    // draw(x: number, y: number): void {
    //     console.log(`Drawing a ${this.color} rectangle at (${x}, ${y}) with width ${this.width} and height ${this.height}`);
    // }
}

// Context class
class Context {
    private rectangle: Rectangle;

    constructor(rectangle: Rectangle) {
        this.rectangle = rectangle;
    }

    // Moved behavior to Context class
    drawRectangle(x: number, y: number): void {
        // Use flyweight as data object, and perform the operation here
    }
}

// Usage
const flyweight = new ConcreteRectangle(10, 20, 'blue');
const context = new Context(flyweight);
context.drawRectangle(100, 100); // Drawing a blue rectangle at (100, 100) with width 10 and height 20

```


# Pseudocode

```ts
// The flyweight class contains a portion of the state of a
// tree. These fields store values that are unique for each
// particular tree. For instance, you won't find here the tree
// coordinates. But the texture and colors shared between many
// trees are here. Since this data is usually BIG, you'd waste a
// lot of memory by keeping it in each tree object. Instead, we
// can extract texture, color and other repeating data into a
// separate object which lots of individual tree objects can
// reference.
class TreeType {
  name;
  color;
  texture;

  constructor(name, color, texture) {
    this.name = name;
    this.color = color;
    this.texture = texture;
  }

  draw(canvas, x, y) {
    // 1. Create a bitmap of a given type, color & texture.
    // 2. Draw the bitmap on the canvas at X and Y coords.
  }
}

// Flyweight factory decides whether to re-use existing
// flyweight or to create a new object.
class TreeFactory {
  static treeTypes: Record<string, TreeType> = {};

  static getTreeType(name, color, texture) {
    const key = `${name}_${color}_${texture}`;
    let type = TreeFactory.treeTypes[key];

    if (!type) {
      type = new TreeType(name, color, texture);
      TreeFactory.treeTypes[key] = type;
    }
    return type;
  }
}

// The contextual object contains the extrinsic part of the tree
// state. An application can create billions of these since they
// are pretty small: just two integer coordinates and one
// reference field.
class Tree {
  x;
  y;
  type: TreeType;
  constructor(x, y, type) {
    this.x = x;
    this.y = y;
    this.type = type;
  }

  draw(canvas) {
    this.type.draw(canvas, this.x, this.y);
  }
}

// The Tree and the Forest classes are the flyweight's clients.
// You can merge them if you don't plan to develop the Tree
// class any further.
class Forest {
  trees: Tree[] = [];

  plantTree(x, y, name, color, texture) {
    const type = TreeFactory.getTreeType(name, color, texture);
    const tree = new Tree(x, y, type);
    this.trees.push(tree);
  }

  draw(canvas) {
    this.trees.forEach((tree) => {
      tree.draw(canvas);
    });
  }
}

```
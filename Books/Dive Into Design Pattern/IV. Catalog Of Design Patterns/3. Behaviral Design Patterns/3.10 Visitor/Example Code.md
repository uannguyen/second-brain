
# Solution

```ts
class ExportVisitor implements Visitor {
  doForCity(City c) { 
    // ...
  }
  doForIndustry(Industry f) { 
    // ...
  }
  doForSightSeeing(SightSeeing ss) { 
    // ...
  }
}
```


# Pseudocode

```ts
// The element interface declares an `accept` method that
// takes the base visitor interface as an argument.
interface Shape {
  move(x: number, y: number): void;
  draw(): void;
  accept(v: Visitor): void;
}

// Each concrete element class must implement the `accept`
// method in such a way that it calls the visitor's method that
// corresponds to the element's class.
class Dot implements Shape {
  // Note that we're calling `visitDot`, which matches the
  // current class name. This way we let the visitor know the
  // class of the element it works with.
  accept(v: Visitor) {
    v.visitDot(this);
  }

  move(x: number, y: number) {
    // Move logic for Dot
  }

  draw() {
    // Draw logic for Dot
  }
}

class Circle implements Shape {
  accept(v: Visitor) {
    v.visitCircle(this);
  }
  move(x: number, y: number) {
    // Move logic for Circle
  }

  draw() {
    // Draw logic for Circle
  }
}

class Rectangle implements Shape {
  accept(v: Visitor) {
    v.visitRectangle(this);
  }

  move(x: number, y: number) {
    // Move logic for Rectangle
  }

  draw() {
    // Draw logic for Rectangle
  }
}

class CompoundShape implements Shape {
  accept(v: Visitor) {
    v.visitCompoundShape(this);
  }

  move(x: number, y: number) {
    // Move logic for CompoundShape
  }

  draw() {
    // Draw logic for CompoundShape
  }
}

// The Visitor interface declares a set of visiting methods that
// correspond to element classes. The signature of a visiting
// method lets the visitor identify the exact class of the
// element that it's dealing with.
interface Visitor {
  visitDot: (d: Dot) => void;
  visitCircle: (c: Circle) => void;
  visitRectangle: (r: Rectangle) => void;
  visitCompoundShape: (cs: CompoundShape) => void;
}

// Concrete visitors implement several versions of the same
// algorithm, which can work with all concrete element
// classes.
//
// You can experience the biggest benefit of the Visitor pattern
// when using it with a complex object structure such as a
// Composite tree. In this case, it might be helpful to store
// some intermediate state of the algorithm while executing the
// visitor's methods over various objects of the structure.
class XMLExportVisitor {
  visitDot(d: Dot) {
    // Export the dot's ID and center coordinates
  }
  visitCircle(c: Circle) {
    // Export the circle's ID, center coordinates and radius
  }
  visitRectangle(r: Rectangle) {
    // Export the rectangle's ID, left-top coordinates, width and height
  }
  visitCompoundShape(cs: CompoundShape) {
    // Export the shape's ID as well as the list of its children's IDs
  }
}

// The client code can run visitor operations over any set of
// elements without figuring out their concrete classes. The
// accept operation directs a call to the appropriate operation
// in the visitor object.
class Application {
  allShapes: Shape[];

  export() {
    const exportVisitor = new XMLExportVisitor();
    if (this.allShapes?.length) {
      this.allShapes.forEach((shape) => {
        shape.accept(exportVisitor);
      });
    }
  }
}

// Example usage:
const app = new Application();
app.allShapes = [new Dot(), new Circle(), new Rectangle(), new CompoundShape()];

app.export();

```
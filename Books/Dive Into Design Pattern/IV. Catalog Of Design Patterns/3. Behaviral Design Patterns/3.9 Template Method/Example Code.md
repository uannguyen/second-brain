
# Pseudocode

```ts
abstract class GameAI {
  builtStructures: any[] = [];
  scouts: any[] = [];
  warriors: any[] = [];
  enemy: any = null;

  // The template method defines the skeleton of an algorithm.
  turn() {
    this.collectResources();
    this.buildStructures();
    this.buildUnits();
    this.attack();
  }

  // Some of the steps may be implemented right in a base class
  collectResources() {
    for (const s of this.builtStructures) {
      s.collect();
    }
  }

  // And some of them may be defined as abstract.
  abstract buildStructures(): void;
  abstract buildUnits(): void;

  // A class can have several template methods.
  attack() {
    this.enemy = this.closestEnemy();
    if (this.enemy == null)
      this.sendScouts({
        x: 0,
        y: 0
      });
    else this.sendWarriors(this.enemy.position);
  }

  abstract sendScouts(position: { x: number; y: number }): void;
  abstract sendWarriors(position: { x: number; y: number }): void;

  closestEnemy(): any {
    // Placeholder logic to find the closest enemy
    return null; // Giả định rằng không có enemy nào gần
  }
}

// Concrete classes have to implement all abstract operations of
// the base class but they must not override the template method
// itself.
class OrcsAI extends GameAI {
  buildStructures() {
    console.log("Building farms, then barracks, then stronghold");
    // Build farms, then barracks, then stronghold
  }

  buildUnits() {
    console.log("Building peon, adding it to scouts group.");
    console.log("Building grunt, adding it to warriors group.");
    // Build peon, add it to scouts group.
    // Build grunt, add it to warriors group.
  }

  sendScouts(position: { x: number; y: number }) {
    if (this.scouts.length > 0) {
      console.log(`Sending scouts to position (${position.x}, ${position.y})`);
      // Send scouts to position
    }
  }

  sendWarriors(position: { x: number; y: number }) {
    if (this.warriors.length > 5) {
      console.log(
        `Sending warriors to position (${position.x}, ${position.y})`
      );
      // Send warriors to position.
    }
  }
}

// Subclasses can also override some operations with a default implementation.
class MonstersAI extends GameAI {
  collectResources() {
    console.log("Monsters don't collect resources.");
    // Monsters don't collect resources.
  }

  buildStructures() {
    console.log("Monsters don't build structures.");
    // Monsters don't build structures.
  }

  buildUnits() {
    console.log("Monsters don't build units.");
    // Monsters don't build units.
  }

  sendScouts(position: { x: number; y: number }) {
    console.log("Monsters send scouts to position");
    // Implementation for sending scouts by Monsters
  }

  sendWarriors(position: { x: number; y: number }) {
    console.log("Monsters send warriors to position");
    // Implementation for sending warriors by Monsters
  }
}

// Usage
const orcsAI = new OrcsAI();
orcsAI.turn();

const monstersAI = new MonstersAI();
monstersAI.turn();

```

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
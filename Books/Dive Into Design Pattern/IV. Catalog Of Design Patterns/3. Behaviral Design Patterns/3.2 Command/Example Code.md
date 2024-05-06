
# Structure

```ts
// Receiver: đối tượng đèn
class Light {
    turnOn(): void {
        console.log("Light is on");
    }

    turnOff(): void {
        console.log("Light is off");
    }
}

// Command interface
interface Command {
    execute(): void;
}

// Concrete command cho việc bật đèn
class TurnOnCommand implements Command {
    private light: Light;

    constructor(light: Light) {
        this.light = light;
    }

    execute(): void {
        this.light.turnOn();
    }
}

// Concrete command cho việc tắt đèn
class TurnOffCommand implements Command {
    private light: Light;

    constructor(light: Light) {
        this.light = light;
    }

    execute(): void {
        this.light.turnOff();
    }
}

// Sender (Invoker): Remote control
class RemoteControl {
    private command: Command;

    setCommand(command: Command): void {
        this.command = command;
    }

    pressButton(): void {
        console.log("Pressing the button on the remote control...");
        this.command.execute();
    }
}

// Client code
const light = new Light(); // Tạo đối tượng đèn
const turnOnCommand = new TurnOnCommand(light); // Tạo command để bật đèn và liên kết với đèn
const turnOffCommand = new TurnOffCommand(light); // Tạo command để tắt đèn và liên kết với đèn
const remoteControl = new RemoteControl(); // Tạo remote control

// Cấu hình remote control để bật đèn
remoteControl.setCommand(turnOnCommand);
// Nhấn nút trên remote control để thực hiện command bật đèn
remoteControl.pressButton();

// Cấu hình remote control để tắt đèn
remoteControl.setCommand(turnOffCommand);
// Nhấn nút trên remote control để thực hiện command tắt đèn
remoteControl.pressButton();

```
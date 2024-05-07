
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


# Pseudocode

```ts
// The base command class defines the common interface for all concrete commands.
abstract class Command {
  protected app: Application;
  protected editor: Editor;
  protected backup: string;

  constructor(app: Application, editor: Editor) {
    this.app = app;
    this.editor = editor;
  }

  // Make a backup of the editor's state.
  saveBackup() {
    this.backup = this.editor.text;
  }

  // Restore the editor's state.
  undo() {
    this.editor.text = this.backup;
  }

  /**
    The execution method is declared abstract to force all concrete commands to provide their own implementations.
    The method must return true or false depending on whether the command changes the editor's state.
  */
  abstract execute(): boolean;
}

// The concrete commands go here.
class CopyCommand extends Command {
  // The copy command isn't saved to the history since it doesn't change the editor's state.
  execute(): boolean {
    this.app.clipboard = this.editor.getSelection();
    return false;
  }
}

// The cut command does change the editor's state, therefore it must be saved to the history.
// And it'll be saved as long as the method returns true.
class CutCommand extends Command {
  execute(): boolean {
    this.saveBackup();
    this.app.clipboard = this.editor.getSelection();
    this.editor.deleteSelection();
    return true;
  }
}

class PasteCommand extends Command {
  execute(): boolean {
    this.saveBackup();
    this.editor.replaceSelection(this.app.clipboard);
    return true;
  }
}

class UndoCommand extends Command {
  execute(): boolean {
    this.app.undo();
    return false;
  }
}

// The global command history is just a stack.
class CommandHistory {
  private histories: Command[] = [];

  push(command: Command) {
    this.histories.push(command);
  }

  pop(): Command | undefined {
    return this.histories.pop();
  }
}

/**
 The editor class has actual text editing operations.
It plays the role of a receiver: all commands end up delegating execution to the editor's methods.
*/
class Editor {
  text: string = "";

  getSelection(): string {
    // Return selected text
    return this.text;
  }

  deleteSelection() {
    // Delete selected text.
  }

  replaceSelection(text: string) {
    // Insert the clipboard's contents at the current position
  }
}

class Button {
  private command: () => void;

  constructor() {
    this.command = () => {};
  }

  // Gán command cho nút
  setCommand(command: () => void) {
    this.command = command;
  }

  // Mô phỏng sự kiện nhấn nút
  click() {
    this.command();
  }
}

/**
 The application class sets up object relations. It acts as a
 sender: when something needs to be done, it creates a command object and executes it.
*/
class Application {
  clipboard: string = "";
  editors: Editor[] = [];
  activeEditor: Editor = new Editor();
  history: CommandHistory = new CommandHistory();

  //The code which assigns commands to UI objects may look like this.
  createUI() {
    const copy = () => {
      this.executeCommand(new CopyCommand(this, this.activeEditor));
    };

    copyButton.setCommand(copy);
    shortcuts.onKeyPress("Ctrl+C", copy);

    const cut = () => {
      this.executeCommand(new CutCommand(this, this.activeEditor));
    };
    cutButton.setCommand(cut);
    shortcuts.onKeyPress("Ctrl+X", cut);

    const paste = () => {
      this.executeCommand(new PasteCommand(this, this.activeEditor));
    };
    pasteButton.setCommand(paste);
    shortcuts.onKeyPress("Ctrl+V", paste);

    const undo = () => {
      this.executeCommand(new UndoCommand(this, this.activeEditor));
    };
    undoButton.setCommand(undo);
    shortcuts.onKeyPress("Ctrl+Z", undo);
  }

  // Execute a command and check whether it has to be added to the history.
  executeCommand(command: Command) {
    if (command.execute()) this.history.push(command);
  }

  /**
   Take the most recent command from the history and run its
  undo method. Note that we don't know the class of that
  command. But we don't have to, since the command knows
  how to undo its own action.
  */
  undo() {
    const command = this.history.pop();
    if (command) command.undo();
  }
}

```
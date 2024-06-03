# Pseudocode

```ts
// The originator holds some important data that may change over
// time. It also defines a method for saving its state inside a
// memento and another method for restoring the state from it.
class Editor {
  private text: string;
  private curX: number;
  private curY: number;
  private selectionWidth: number;

  setText(text: string) {
    this.text = text;
  }

  setCursor(curX: number, curY: number) {
    this.curX = curX;
    this.curY = curY;
  }

  setSelectionWidth(width: number) {
    this.selectionWidth = width;
  }

  // Saves the current state inside a memento.
  createSnapshot(): Snapshot {
    return new Snapshot(
      this,
      this.text,
      this.curX,
      this.curY,
      this.selectionWidth
    );
  }
}

// The memento class stores the past state of the editor.
class Snapshot {
  private editor: Editor;
  private text: string;
  private curX: number;
  private curY: number;
  private selectionWidth: number;

  constructor(
    editor: Editor,
    text: string,
    curX: number,
    curY: number,
    selectionWidth: number
  ) {
    this.editor = editor;
    this.text = text;
    this.curX = curX;
    this.curY = curY;
    this.selectionWidth = selectionWidth;
  }

  restore() {
    this.editor.setText(this.text);
    this.editor.setCursor(this.curX, this.curY);
    this.editor.setSelectionWidth(this.selectionWidth);
  }
}

// A command object can act as a caretaker. In that case, the
// command gets a memento just before it changes the
// originator's state. When undo is requested, it restores the
// originator's state from a memento.
class Command {
  private backup: Snapshot;
  private editor: Editor;

  constructor(editor: Editor) {
    this.editor = editor;
  }

  makeBackup() {
    this.backup = this.editor.createSnapshot();
  }

  undo() {
    if (this.backup != null) {
      this.backup.restore();
    }
  }
}

// Example usage:
const editor = new Editor();
const command = new Command(editor);

// Set editor state
editor.setText("Hello, world!");
editor.setCursor(0, 0);
editor.setSelectionWidth(5);

// Make a backup before changing state
command.makeBackup();

// Change editor state
editor.setText("New text");
editor.setCursor(10, 10);
editor.setSelectionWidth(3);

console.log("prev undo", editor);

// Undo changes
command.undo();

// Verify undo
console.log("after undo", editor);

```
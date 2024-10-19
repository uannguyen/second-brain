
# Pseudocode

```ts
// Giao diện subscriber.
interface EventListener {
  update(data: any): void;
}

// Lớp base publisher bao gồm mã quản lý đăng ký và các phương thức thông báo.
class EventManager {
  private listeners: { eventType: string; listener: EventListener }[] = [];

  subscribe(eventType: string, listener: EventListener) {
    this.listeners.push({ eventType, listener });
  }

  unSubscribe(eventType: string, listener: EventListener) {
    const index = this.listeners.findIndex(
      (item) => item.eventType === eventType && item.listener === listener
    );
    if (index !== -1) {
      this.listeners.splice(index, 1);
    }
  }

  notify(eventType: string, data: any) {
    this.listeners.forEach((item) => {
      if (item.eventType === eventType) {
        item.listener.update(data);
      }
    });
  }
}

// Lớp publisher cụ thể chứa logic kinh doanh thực tế mà một số subscribers quan tâm.
class Editor {
  public events: EventManager;
  private file: File;

  constructor() {
    this.events = new EventManager();
  }

  // Các phương thức logic kinh doanh có thể thông báo cho subscribers về các thay đổi.
  openFile(path: string) {
    this.file = new File(path);
    this.events.notify("open", this.file.name);
  }

  saveFile() {
    this.file.write();
    this.events.notify("save", this.file.name);
  }
}

// Các subscribers cụ thể phản ứng với các cập nhật do publisher phát hành mà họ được gắn vào.
class LoggingListener implements EventListener {
  private log: File;
  private message: string;

  constructor(log_filename: string, message: string) {
    this.log = new File(log_filename);
    this.message = message;
  }

  update(filename: string): void {
    // Giả sử hàm replace đã được định nghĩa ở đâu đó để thay thế %s bằng filename
    this.log.write(this.message.replace("%s", filename));
  }
}

class EmailAlertsListener implements EventListener {
  private email: string;
  private message: string;

  constructor(email: string, message: string) {
    this.email = email;
    this.message = message;
  }

  update(filename: string): void {
    // Giả lập gửi email
    console.log(
      `Email sent to ${this.email} with message: ${this.message.replace(
        "%s",
        filename
      )}`
    );
  }
}

// Ứng dụng có thể cấu hình các publishers và subscribers tại runtime.
class Application {
  config() {
    const editor = new Editor();
    const logger = new LoggingListener(
      "/path/to/log.txt",
      "Someone has opened the file: %s"
    );
    editor.events.subscribe("open", logger);

    const emailAlerts = new EmailAlertsListener(
      "admin@example.com",
      "Someone has changed the file: %s"
    );
    editor.events.subscribe("save", emailAlerts);

    // Mở và lưu tệp để kiểm tra thông báo.
    editor.openFile("/path/to/file.txt");
    editor.saveFile();
  }
}

// Chạy ứng dụng.
const app = new Application();
app.config();

```
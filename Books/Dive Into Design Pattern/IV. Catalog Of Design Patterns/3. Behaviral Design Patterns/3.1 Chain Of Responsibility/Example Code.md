# Pseudocode

```ts
// Định nghĩa một giao diện cho các xử lý yêu cầu trợ giúp
interface HelpHandler {
  showHelp(): void;
}

// Lớp cơ sở cho các thành phần đơn giản
abstract class SimpleComponent implements HelpHandler {
  tooltipText: string;

  showHelp(): void {
    console.log("================= go to showHelp - SimpleComponent");
    if (this.tooltipText) {
      console.log("Hiển thị tooltip: ", this.tooltipText);
    }
  }
}

// Lớp cơ sở cho các container
abstract class ContainerComponent implements HelpHandler {
  children: HelpHandler[] = [];

  add(child: HelpHandler): void {
    this.children.push(child);
  }

  showHelp(): void {
    console.log("================= go to showHelp - ContainerComponent");
    for (const child of this.children) {
      child.showHelp();
    }
  }
}

// Lớp Button triển khai HelpHandler cho các thành phần đơn giản
class Button extends SimpleComponent {}

// Lớp Panel triển khai HelpHandler cho các container
class Panel extends ContainerComponent {
  modalHelpText: string;

  showHelp(): void {
    console.log("================= go to showHelp - Panel");
    if (this.modalHelpText) {
      console.log("Hiển thị trợ giúp modal: ", this.modalHelpText);
    } else {
      super.showHelp();
    }
  }
}

// Lớp Dialog cũng triển khai HelpHandler cho các container
class Dialog extends ContainerComponent {
  wikiPageURL: string;

  showHelp(): void {
    console.log("================= go to showHelp - Dialog");
    if (this.wikiPageURL) {
      console.log("Mở trang trợ giúp Wiki: ", this.wikiPageURL);
    } else {
      super.showHelp();
    }
  }
}

// Client code.
class Application {
  // Mỗi ứng dụng cấu hình chuỗi xử lý khác nhau.
  createUI(): void {
    const dialog = new Dialog();
    dialog.wikiPageURL = "https://example.com";

    const panel = new Panel();
    panel.modalHelpText = "This panel does...";

    const OKBtn = new Button();
    OKBtn.tooltipText = "This is an OK button that...";

    const CANCELBtn = new Button();
    CANCELBtn.tooltipText = "This is an CANCEL button that...";

    panel.add(OKBtn);
    panel.add(CANCELBtn);
    dialog.add(panel);
    console.log("================ panel component", panel);
    console.log("================ dialog component", dialog);
  }

  // Giả sử có một hàm để lấy thành phần tại tọa độ chuột
  getComponentAtMouseCoords(): HelpHandler {
    // Giả sử đoạn mã để lấy và trả về thành phần tại tọa độ chuột ở đây
    return new Panel(); // Đây là giả định, bạn cần thay đổi thành mã thực tế.
  }

  // Khi phím F1 được nhấn
  onF1KeyPress(): void {
    const component = this.getComponentAtMouseCoords();
    component.showHelp();
  }
}

// Khởi tạo ứng dụng và sử dụng
const app = new Application();
app.createUI();
app.onF1KeyPress();

```
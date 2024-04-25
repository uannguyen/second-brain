
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


# Pseudocode

```ts
// The interface of a remote service.
interface ThirdPartyYoutubeLib {
  listVideos(): void;
  getVideoInfo(id): void;
  downloadVideo(id): void;
}

/*
  The concrete implementation of a service connector.
  Methods of this class can request information from YouTube.
  The speed of the request depends on a user's internet connection as well as YouTube's.
  The application will slow down if a lot of requests are fired at the same time,
   even if they all request the same information
 */
class ThirdPartyYoutubeClass implements ThirdPartyYoutubeLib {
  listVideos(): void {
    // Send an API request to YouTube
  }

  getVideoInfo(id: any): void {
    // Get metadata about some video
  }

  downloadVideo(id: any): void {
    // Download a video file from YouTube
  }
}

/*
 To save some bandwidth, we can cache request results and keep
 them for some time. But it may be impossible to put such code
 directly into the service class. For example, it could have
 been provided as part of a third party library and/or defined
 as `final`. That's why we put the caching code into a new
 proxy class which implements the same interface as the
 service class. It delegates to the service object only when
 the real requests have to be sent.
 */

class CachedYoutubeClass implements ThirdPartyYoutubeLib {
  service: ThirdPartyYoutubeClass;
  private listCache;
  private videoCache;
  needReset;

  constructor(service: ThirdPartyYoutubeLib) {
    this.service = service;
  }

  listVideos() {
    if (this.listCache == null || this.needReset)
      this.listCache = this.service.listVideos();
    return this.listCache;
  }

  getVideoInfo(id) {
    if (this.videoCache == null || this.needReset)
      this.videoCache = this.service.getVideoInfo(id);
    return this.videoCache;
  }

  downloadVideo(id) {
    // check video download is exists
    if (!downloadExists(id) || this.needReset) this.service.downloadVideo(id);
  }
}

/*
 The GUI class, which used to work directly with a service
 object, stays unchanged as long as it works with the service
 object through an interface. We can safely pass a proxy
 object instead of a real service object since they both
 implement the same interface
*/
class YoutubeManager {
  protected service: ThirdPartyYoutubeLib;
  constructor(service: ThirdPartyYoutubeLib) {
    this.service = service;
  }

  renderVideoPage(id) {
    const info = this.service.getVideoInfo(id);
    // Render the video page.
  }

  renderListPanel() {
    const list = this.service.listVideos();
    // Render the list of video thumbnails.
  }

  reactOnUserInput(id) {
    this.renderVideoPage(id);
    this.renderListPanel();
  }
}

// The application can configure proxies on the fly.
class Application {
  init() {
    const aYouTubeService = new ThirdPartyYoutubeClass();
    const aYouTubeProxy = new CachedYoutubeClass(aYouTubeService);
    const manager = new YoutubeManager(aYouTubeProxy);
    manager.reactOnUserInput(123);
  }
}
```


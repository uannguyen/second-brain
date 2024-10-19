
# Structure

```ts
// Subsystem: Quản lý phim
class MovieManager {
    public static getMovieDetails(movieId: string): string {
        // Logic để lấy thông tin phim từ database hoặc API
        return `Movie details for movie with ID ${movieId}`;
    }
}

// Subsystem: Quản lý suất chiếu
class ShowtimeManager {
    public static getShowtimes(movieId: string): string[] {
        // Logic để lấy thông tin các suất chiếu từ database hoặc API
        return [`Showtimes for movie with ID ${movieId}`];
    }
}

// Subsystem: Quản lý vé
class TicketManager {
    public static bookTicket(showtimeId: string): string {
        // Logic để đặt vé cho một suất chiếu cụ thể
        return `Ticket booked for showtime with ID ${showtimeId}`;
    }
}

// Facade: Quản lý đặt vé
class TicketBookingFacade {
    public static bookTicketForMovie(movieId: string): string {
        const movieDetails = MovieManager.getMovieDetails(movieId);
        const showtimes = ShowtimeManager.getShowtimes(movieId);
        const ticket = TicketManager.bookTicket(showtimes[0]); // Đặt vé cho suất chiếu đầu tiên

        return `${movieDetails}\n${ticket}`;
    }
}

// Client code
const movieId = "12345";
const bookingDetails = TicketBookingFacade.bookTicketForMovie(movieId);
console.log(bookingDetails);

```


# Pseudocode

```ts
/**
 These are some of the classes of a complex 3rd-party video
 conversion framework. We don't control that code, therefore
 can't simplify it
*/
class VideoFile {}
class OggCompressionCodec {}
class MPEG4CompressionCodec {}
class CodecFactory {}
class BitrateReader {}
class AudioMixer {}

/**
 We create a facade class to hide the framework's complexity
 behind a simple interface. It's a trade-off between
 functionality and simplicity
*/

class VideoConverter {
  convert(filename, format) {
    const file = new VideoFile(filename);
    let destinationCodec;

    const sourceCodec = new CodecFactory.extract(file);

    if (format == "mp4") destinationCodec = new MPEG4CompressionCodec();
    else destinationCodec = new OggCompressionCodec();

    const buffer = BitrateReader.read(filename, sourceCodec);

    const result = BitrateReader.convert(buffer, destinationCodec);

    result = new AudioMixer().fix(result);
    return new File(result);
  }
}

// Application classes don't depend on a billion classes
// provided by the complex framework. Also, if you decide to
// switch frameworks, you only need to rewrite the facade class.
class Application {
  main() {
    const convertor = new VideoConverter();
    const mp4 = convertor.convert("youtubevideo.ogg", "mp4");
    mp4.save();
  }
}

```
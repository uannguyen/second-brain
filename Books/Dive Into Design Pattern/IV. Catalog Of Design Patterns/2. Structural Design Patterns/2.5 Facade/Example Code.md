
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
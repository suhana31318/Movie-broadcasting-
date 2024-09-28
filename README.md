class Movie:
    def __init__(self, title):
        self.title = title

    def __str__(self):
        return self.title


class MovieBroadcasting:
    def __init__(self):
        self.movies = []
        self.broadcasting = []

    def add_movie(self, title):
        movie = Movie(title)
        self.movies.append(movie)
        print(f"Added movie: {movie}")

    def start_broadcast(self, title):
        for movie in self.movies:
            if movie.title.lower() == title.lower():
                if movie not in self.broadcasting:
                    self.broadcasting.append(movie)
                    print(f"Started broadcasting: {movie}")
                else:
                    print(f"{movie.title} is already broadcasting.")
                return
        print("Movie not found!")

    def stop_broadcast(self, title):
        for movie in self.broadcasting:
            if movie.title.lower() == title.lower():
                self.broadcasting.remove(movie)
                print(f"Stopped broadcasting: {movie}")
                return
        print("Movie not currently broadcasting!")

    def list_broadcasting(self):
        if not self.broadcasting:
            print("No movies currently broadcasting.")
        else:
            print("Currently broadcasting:")
            for movie in self.broadcasting:
                print(movie)


def main():
    broadcasting_system = MovieBroadcasting()

    while True:
        print("\nMovie Broadcasting System")
        print("1. Add Movie")
        print("2. Start Broadcast")
        print("3. Stop Broadcast")
        print("4. List Broadcasting Movies")
        print("5. Exit")
        choice = input("Choose an option: ")

        if choice == '1':
            title = input("Enter movie title: ")
            broadcasting_system.add_movie(title)

        elif choice == '2':
            title = input("Enter movie title to start broadcasting: ")
            broadcasting_system.start_broadcast(title)

        elif choice == '3':
            title = input("Enter movie title to stop broadcasting: ")
            broadcasting_system.stop_broadcast(title)

        elif choice == '4':
            broadcasting_system.list_broadcasting()

        elif choice == '5':
            print("Exiting the system.")
            break

        else:
            print("Invalid choice. Please try again.")

if __name__ == "__main__":
    main()

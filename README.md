class Passenger {
     String name;
    Passenger next;

    // Constructor
    public Passenger(String name) {
        this.name = name;
        this.next = null;
    }
   
}
public class Flight {
    private Passenger head = null;  // Menunjuk ke penumpang pertama di daftar

    // Metode untuk menambah penumpang di akhir daftar
    public void addPassenger(String name) {
        Passenger newPassenger = new Passenger(name);
        if (head == null) {
            head = newPassenger;  // Jika daftar kosong, penumpang baru menjadi head
        } else {
            Passenger current = head;
            while (current.next != null) {
                current = current.next;  // Mencari penumpang terakhir
            }
            current.next = newPassenger;  // Menambahkan penumpang baru di akhir
        }
        System.out.println("Passenger " + name + " added.");
    }

    // Metode untuk menghapus penumpang berdasarkan nama
    public void removePassenger(String name) {
        if (head == null) {
            System.out.println("No passengers to remove.");
            return;
        }

        if (head.name.equals(name)) {
            head = head.next;  // Menghapus penumpang pertama jika cocok
            System.out.println("Passenger " + name + " removed.");
            return;
        }

        Passenger current = head;
        while (current.next != null && !current.next.name.equals(name)) {
            current = current.next;
        }

        if (current.next == null) {
            System.out.println("Passenger " + name + " not found.");
        } else {
            current.next = current.next.next;  // Menghapus penumpang yang ditemukan
            System.out.println("Passenger " + name + " removed.");
        }
    }

    // Metode untuk menampilkan semua penumpang
    public void displayPassengers() {
        if (head == null) {
            System.out.println("No passengers in the flight.");
        } else {
            Passenger current = head;
            System.out.println("Passenger List:");
            while (current != null) {
                System.out.println(current.name);
                current = current.next;
            }
        }
    }

    public static void main(String[] args) {
        Flight flight = new Flight();

        // Menambah penumpang
        flight.addPassenger("John");
        flight.addPassenger("Doe");
        flight.addPassenger("Alice");
        flight.addPassenger("Bob");

        // Menampilkan daftar penumpang
        flight.displayPassengers();

        // Menghapus penumpang
        flight.removePassenger("Doe");

        // Menampilkan daftar penumpang lagi
        flight.displayPassengers();
    }
}

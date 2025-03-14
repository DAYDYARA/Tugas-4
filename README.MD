import java.util.ArrayList; // Mengimpor ArrayList, yang digunakan untuk menyimpan daftar task.
import java.util.Scanner; // Mengimpor Scanner, yang digunakan untuk membaca input dari pengguna.

public class TodoList2A {  //  Mendeklarasikan kelas TodoList2A.
    private ArrayList<String> todoList; // Membuat atribut todoList, yang merupakan ArrayList<String> untuk menyimpan daftar task.
    
    // Constructor to initialize the ArrayList
    public TodoList2A() {
        todoList = new ArrayList<>();
    } 
    // Menginisialisasi todoList sebagai ArrayList kosong.
    
    // Method to add a task
    public void addTask(String task) { // Metode addTask menerima string task sebagai parameter.
        todoList.add(task); // Menambahkan task ke todoList.
        System.out.println("Task added successfully!"); // Menampilkan pesan konfirmasi setelah task berhasil ditambahkan.
    }
    
    // Method to remove a task
    public void removeTask(String task) { //  Deklarasi method (removeTask) dalam bahasa Java.
        if (todoList.remove(task)) { // Mencari dan menghapus task berdasarkan nama.
            System.out.println("Task removed successfully!"); // Jika task ditemukan dan dihapus, menampilkan pesan sukses.
        } else {
            System.out.println("Task not found."); // Jika tidak ditemukan, menampilkan pesan task tidak ditemukan.
        }
    }
    
    // Method to display all tasks
    public void displayTasks() { //  Deklarasi method dalam Java yang bernama displayTasks().
        if (todoList.isEmpty()) { // Mengecek apakah todolist kosong atau tidak.
            System.out.println("No tasks available."); // Jika kosong maka menampilkan pesan task tidak tersedia.
        } else {
            System.out.println("\nTo-Do List:"); // Jika todolist tidak kosong atau ada.
            for (int i = 0; i < todoList.size(); i++) { //  Loop (perulangan) untuk menelusuri setiap elemen dalam todoList.
                System.out.println((i + 1) + ". " + todoList.get(i)); // todoList.get(i) : Mengambil tugas pada indeks i dari todoList. (i + 1) + ". " : Menambahkan angka urutan (karena indeks dimulai dari 0).
            }
        }
    }
    
    // fitur search task by index
    public void searchTaskByIndex(int index) { // metode dalam java untuk mencari task dari index.
        if (index >= 0 && index < todoList.size()) { // index >= 0 : Memastikan bahwa indeks tidak negatif (karena dalam Java, indeks array dimulai dari 0). index < todoList.size() : Memastikan bahwa indeks masih dalam batas daftar (todoList)
            System.out.println("Task at index " + (index + 1) + ": " + todoList.get(index)); // todoList.get(index) : Mengambil tugas yang ada pada indeks tersebut. (index + 1) : karena indeks dimulai dari 0.
        } else {
            System.out.println("Invalid index. No task found."); // Jika indeks tidak valid maka akan memunculkan pesan index tidak valid. task tidak ditemukan.
        }
    }
    
    // fitur remo task by index
    public void removeTaskByIndex(int index) { // metode dalam java untuk menghapus task dari indeks.
        if (index >= 0 && index < todoList.size()) { // index >= 0 : Memastikan bahwa indeks tidak negatif (karena dalam Java, indeks array dimulai dari 0). index < todoList.size() : Memastikan bahwa indeks masih dalam batas daftar (todoList)
            String removedTask = todoList.remove(index); // Menghapus tugas berdasarkan indeks.
            System.out.println("Task \"" + removedTask + "\" removed successfully!"); // Menampilkan pesan bahwa tugas berhasil dihapus.
        } else {
            System.out.println("Invalid index. Task not removed."); // Jika indeks tidak ditemukan maka akan muncul pesan index tidak valid. task tidak terhapus.
        }
    }
            
        
    
    
    
    public static void main(String[] args) { // Metode utama yang dieksekusi pertama kali saat program berjalan.
        TodoList2A app = new TodoList2A(); // Membuat objek TodoList2A
        Scanner scanner = new Scanner(System.in); //  Membuat objek Scanner untuk input dari pengguna
        boolean running = true; // Variabel running untuk kontrol loop utama.
    
        while (running) { // Loop ini akan berjalan selama nilai running bernilai true.
    
        // menampilkan menu.
            System.out.println("\nTo-Do List Application");
            System.out.println("1. Add Task");
            System.out.println("2. Remove Task By Task Name");
            System.out.println("3. Remove Task By Index");
            System.out.println("4. Search Task By index");
            System.out.println("5. Display Tasks");
            System.out.println("6. Exit");
            System.out.print("Enter your choice: ");
            
            // Menerima Input dari Pengguna
            int choice = scanner.nextInt();
            scanner.nextLine();  // Consume newline
        
            switch (choice) { //  Mengevaluasi nilai dari choice
        
                case 1:
                    System.out.print("Enter task to add: "); // Meminta pengguna memasukkan suatu nilai, yaitu tugas yang akan ditambahkan.
                    String taskToAdd = scanner.nextLine(); // Kode ini membaca input dari pengguna dan menyimpannya dalam variabel taskToAdd sebagai sebuah string.
                    app.addTask(taskToAdd); // Setelah mendapatkan input pengguna, tugas yang dimasukkan akan diproses oleh aplikasi menggunakan metode addTask() dari objek app.
                    break // break digunakan untuk keluar dari blok switch setelah kode di dalam case tersebut dieksekusi.
        
                case 2:
                    System.out.print("Enter task to remove: "); // Meminta pengguna memasukkan nama tugas yang ingin dihapus.
                    String taskToRemove = scanner.nextLine(); // Membaca input dari pengguna dan menyimpannya dalam variabel taskToRemove sebagai sebuah string.
                    app.removeTask(taskToRemove); // Setelah mendapatkan nama tugas yang ingin dihapus, kode ini memanggil metode removeTask() pada objek app, dan mengoper nilai taskToRemove sebagai argumennya. 
                    break // break digunakan untuk keluar dari blok switch setelah kode di dalam case tersebut dieksekusi.
        
                case 3:
                    System.out.print("Enter index to remove: "); // meminta pengguna untuk memasukkan indeks tugas yang ingin dihapus.
                    int indexToRemove = scanner.nextInt() - 1; // membaca input dari pengguna berupa angka (indeks tugas yang ingin dihapus).
                    app.removeTaskByIndex(indexToRemove); // Setelah mendapatkan indeks yang ingin dihapus, memanggil metode removeTaskByIndex() pada objek app, dan mengoper indeks (indexToRemove) untuk menghapus tugas pada indeks tersebut
                    break // break digunakan untuk keluar dari blok switch setelah kode di dalam case tersebut dieksekusi.
        
                case 4:
                    System.out.print("Enter index to search: "); // meminta pengguna memasukkan indeks tugas yang ingin dicari.
                    int indexToSearch = scanner.nextInt() - 1; //  untuk membaca input dari pengguna berupa angka yang merupakan indeks tugas yang ingin dicari.
                    app.searchTaskByIndex(indexToSearch); // Setelah mendapatkan indeks yang dicari, memanggil metode searchTaskByIndex() pada objek app untuk mencari tugas yang sesuai dengan indeks yang dimasukkan.
                    break // break digunakan untuk keluar dari blok switch setelah kode di dalam case tersebut dieksekusi.
        
                case 5:
                    app.displayTasks(); // memanggil metode displayTasks() dari objek app.
                    break // break digunakan untuk keluar dari blok switch setelah kode di dalam case tersebut dieksekusi.
        
                case 6:
                    running = false; // jika variabel running bernilai false maka akann menghentikan/keluar dari kode program.
                    System.out.println("Exiting the application..."); // memberitahu pengguna bahwa aplikasi sedang keluar atau berhenti.
                    break // break digunakan untuk keluar dari blok switch setelah kode di dalam case tersebut dieksekusi.
        
                default: // untuk menangani semua kasus yang tidak cocok dengan pilihan yang ditentukan dalam case sebelumnya.
                    System.out.println("Invalid choice. Please try again."); // memberitahu pengguna bahwa input yang mereka masukkan tidak valid atau tidak dikenali.
            }
        }
        scanner.close(); //  untuk menutup aliran input yang digunakan oleh objek scanner.
    }
}
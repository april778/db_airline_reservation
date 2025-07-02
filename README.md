# db_airline_reservation
Simple Airline Ticket Reservation SQL Database
# 🛫 Airline Reservation Database

Repository ini berisi skema database sederhana untuk sistem pemesanan tiket pesawat (Airline Reservation System) yang dibuat menggunakan MySQL. Struktur ini dirancang untuk mendukung proses reservasi penerbangan, manajemen pengguna, pembayaran, dan informasi penerbangan.

 Struktur Tabel

1. `users`
Menyimpan data pengguna yang melakukan pemesanan tiket.
- `user_id` (PK)
- `name`, `email`, `password`, `phone`

 2. `airlines`
Menyimpan data maskapai penerbangan.
- `airline_id` (PK)
- `airline_name`, `country`

 3. `flights`
Menyimpan informasi detail penerbangan.
- `flight_id` (PK)
- `airline_id` (FK ke `airlines`)
- `departure_city`, `arrival_city`, `departure_time`, `arrival_time`, `price`

 4. `bookings`
Mewakili transaksi pemesanan tiket yang dilakukan oleh pengguna.
- `booking_id` (PK)
- `user_id` (FK ke `users`)
- `flight_id` (FK ke `flights`)
- `booking_date`, `seat_number`, `status` (Pending, Confirmed, Cancelled)

 5. `payments`
Menyimpan informasi pembayaran dari pemesanan tiket.
- `payment_id` (PK)
- `booking_id` (FK ke `bookings`)
- `payment_date`, `amount`, `payment_method`, `status` (Paid, Unpaid)

 Relasi Antar Tabel
- `users` → `bookings` (1:N)
- `flights` → `bookings` (1:N)
- `bookings` → `payments` (1:1)
- `airlines` → `flights` (1:N)

 Cara Penggunaan
1. Import file `airline_reservation.sql` ke MySQL menggunakan phpMyAdmin atau command line:
   ```bash
   mysql -u root -p < airline_reservation.sql

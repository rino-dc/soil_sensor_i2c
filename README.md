Assalamualaikum wr wb

Kali ini kita coba baca sensor tanah dengan komunikasi i2c..

Soil sensor i2c..

saya carikan wujud sensornya...

seperti gambar disamping sensornya

parameter yang diukur

Deskripsi Sensor Tanah/Soil Sensor Industrial Grade untuk Suhu, Kelembaban, & EC
Sensor tanah untuk kelas industri. Cocok untuk perkebunan maupun lahan pertanian secara umum.

Keterangan:
1. Dust and waterproof (IP67)
2. Raspberry Pi compatible
3. Calibration functions for EC
4. Cable length : +-100 cm

Parameter yang diukur
a. Suhu tanah
	Range measurement : -20 to 60°C
b. Kelembaban tanah
	Range measurement : 0 – 100%
c. Electrical Conductivity (EC)
	Resolution: 0.01 dS/m

untuk kabelnya
1. merah = vcc 3.3v
2. hitam = gnd
3. hijau = SDA
4. putih = SCL

sambungkan ke port Nucleo-32 STM32L432KC


merah - vcc
hitam - gnd
hijau - PA10
putih - PA9

1. buka stm32cubeide nya..

2. buat project baru

3. tentukan USART2
	aktifkan, lalu koneksi pin:
		1 PA2 = TX
		2 PA15 = RX
		
4. tentukan Pin I2C 
	berdasarkan yang kita tentukan tadi
	1. PA10 = SDA
	2. PA9 = SCL

5. save all

6. buka main.c

7. masukkan register2 berikut
 	
static const uint8_t ADDR 				= 0x63<<1;
static const uint8_t REG_READ_START 	= 0x01;
static const uint8_t REG_READ_EC 		= 0x03;
static const uint8_t REG_READ_TEMP 		= 0x04;
static const uint8_t REG_READ_VWC 		= 0x05;

diantara USER CODE BEGIN PD */ 
dan USER CODE END PD */

8. tentukan variabel variabelnya

mulai dari buffer sampai variabel setiap parameter

9. masukkan fungsi untuk printf
	
10. masukkan syntax untuk melakukan checking(inisialisasi) sensor;

11. coba build..
	OOPS ada warning..
	oh.. tenang.. variabel tsb belum kita pakai..
	
12. Coba upload dulu ke Nucleo-32

13. tekan tombol reset di board..

14. keluar tulisan "SOIL SENSOR READY"
	artinya sensor terkoneksi dengan baik..

15. Selanjutnya kita buat program untuk membaca parameter sensor.

16. dimulai dari starting sensor dulu..

17. next kita baca soil volumetric water content (vwc)

18. disini kita perlu mengatur agar formating float bisa berjalan dengan baik fi printf
	klik kanan project > "Properties" > "C/C++ Build" > "Setting" > "Tool Settings" > Check di "Use float with printf ... " > "Apply" > "Apply and Close"
	
19. Coba kita jalankan dulu..

20. kita percepat delay lalu jalankan lagi..

21. coba saya pegang sensornya.
	terjadi pertambahan value
	
22. next kita coba baca temperaturenya
		caranya sama hanya beberapa yang perlu diganti.. kita copast aja biar cepet..

23. jalanin lagi..
	wkwk error... cb cek ah.. 
	ternyata kabelnya lepas.. HAHA
	sudah normal...
	
24. next kita baca Electrical Conductivity

25. coba kita jalankan lagi

26. oke data sudah didapatkan semua...

Sekian tutorial pembacaan soil sensor i2c, semoga bermanfaat, terimakasih...

Wassalamualaikum wr wb
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	


























































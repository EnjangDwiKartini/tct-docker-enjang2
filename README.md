# SIMULASI KATACODA
***
## Orchestration menggunakan Docker Compose
***
*  Mendefinisikan Container 
	Docker Compose didasarkan pada file docker-compose.yml. File ini mendefinisikan semua kontainer dan pengaturan yang diperlukan untuk meluncurkan kumpulan kluster.
	Format file didasarkan pada YAML. 
			
	~~~
	container_name:
	property: value
	- or options
	~~~
			
	Perintah mendefinisikan Container:
			
	~~~
	web:
	build: .
	~~~
			
	![alt text](https://github.com/EnjangDwiKartini/tct-docker-enjang2/blob/master/img/1.PNG "simulasi-docker")
			
			
* Mendefinisikan Pengaturan 
	Menautkan ke penampung sumber redis yang ditentukan dalam file yang sama dan menetapkan nama yang sama ke alias:
		
	~~~
	links:
		- redis
	~~~
			
	Format yang sama digunakan untuk properti lain seperti port
			
	~~~
	ports:
		- "3000"
		- "8000"
	~~~
			
	![alt text](https://github.com/EnjangDwiKartini/tct-docker-enjang2/blob/master/img/2.PNG "simulasi-docker")
		
* Mendefinisikan Container kedua 
	Pada langkah ini,  menggunakan image yang ada dari Docker Hub sebagai container kedua.
	Untuk menemukan wadah kedua cukup menggunakan format yang sama seperti sebelumnya pada baris baru. Format YAML cukup fleksibel untuk mendefinisikan beberapa kontainer dalam file yang sama.
			
	~~~
	redis:
		image: redis:alpine
		volumes:
		- /var/redis/data:/data
	~~~
			
	![alt text](https://github.com/EnjangDwiKartini/tct-docker-enjang2/blob/master/img/3.PNG "simulasi-docker")

* Docker Up
	Dengan dibuatnya file docker-compose.yml, kita dapat meluncurkan semua aplikasi dengan satu perintah ke atas. Argumen -d menyatakan untuk menjalankan container di latar belakang, mirip dengan ketika digunakan dengan menjalankan docker run. 
	Perintah yang digunakan :
			
	~~~
	docker-compose up -d
	~~~
			
	compose ==> server lebih dari 1
	Sumulasinya adalah seperti berikut :
			
	![alt text](https://github.com/EnjangDwiKartini/tct-docker-enjang2/blob/master/img/4.PNG "simulasi-docker")
		
* Docker Management
	Docker management : mengelola semua kontainer menggunakan satu perintah. 
	- melihat detail container yang diluncurkan :
			
		~~~
		docker-compose ps
		~~~
				
	![alt text](https://github.com/EnjangDwiKartini/tct-docker-enjang2/blob/master/img/5.PNG "simulasi-docker")
			
	- mengakses semua log melalui satu aliran
			
		~~~
		docker-compose logs
		~~~
				
	![alt text](https://github.com/EnjangDwiKartini/tct-docker-enjang2/blob/master/img/6.PNG "simulasi-docker")
				
	- perintah yang lain akan mengikuti pola yang sama dengan perintah :
			
		~~~
		docker-compose
		~~~
				
		![alt text](https://github.com/EnjangDwiKartini/tct-docker-enjang2/blob/master/img/7-1.PNG "simulasi-docker")

		![alt text](https://github.com/EnjangDwiKartini/tct-docker-enjang2/blob/master/img/7-2.PNG "simulasi-docker")
				
		![alt text](https://github.com/EnjangDwiKartini/tct-docker-enjang2/blob/master/img/7-3.PNG "simulasi-docker")
				
		![alt text](https://github.com/EnjangDwiKartini/tct-docker-enjang2/blob/master/img/7-4.PNG "simulasi-docker")
* Docker Scale 
	Docker scale = menskala jumlah container yang berjalan.
	Memungkinkan untuk  menentukan layanan dan  jumlah instance yang diinginkan. Jika angkanya lebih besar dari instance yang sudah berjalan, maka akan meluncurkan container tambahan. Jika jumlahnya kurang, maka akan menghentikan container yang tidak diinginkan.
	perintah menskala jumlah penampung web yang dijalankan :
		
	~~~
	docker-compose scale web=3
	~~~
		
	![alt text](https://github.com/EnjangDwiKartini/tct-docker-enjang2/blob/master/img/8.PNG "simulasi-docker")
		
	Mengembalikan :
		
	~~~
	docker-compose scale web=1
	~~~
		
	![alt text](https://github.com/EnjangDwiKartini/tct-docker-enjang2/blob/master/img/9.PNG "simulasi-docker")
		
* Docker Stop 
	Perintah untuk menghentikan container :
		
	~~~
	docker-compose stop
	~~~
		
	![alt text](https://github.com/EnjangDwiKartini/tct-docker-enjang2/blob/master/img/10.PNG "simulasi-docker")
		
	Perintah menghapus semua container :
		
	~~~
	docker-compose rm
	~~~
		
	![alt text](https://github.com/EnjangDwiKartini/tct-docker-enjang2/blob/master/img/11.PNG "simulasi-docker")
		
		
		
	
			
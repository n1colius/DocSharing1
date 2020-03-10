## Top 10 OWASP
Hal-hal yang perlu diperhatikan ketika coding/development  

__1. Injection__  
* Pastikan parameter2 yg masuk di validasi terlebih dahulu di phpnya  

    $var = (int) $this->get('CmbFilterProvince');  
    $var1 = filter_var($this->get('TextFilterID'),FILTER_SANITIZE_STRING);  
    $var2 = filter_var(preg_replace("([^0-9-])","",$this->get('DateBeginDateCollection')));  

__2. Broken Authentication__
* Ketika menggunakan authentication yg pakai token, harap bener2 aware agar token nya tidak bocor dan bisa diambil oleh user  
* Untuk diphp yg menggunakan SESSION, harus dijaga jangan sampai variable2 di SESSION bisa dimodif secara flow, variable SESSION tidak boleh di assign dengan menggunakan parameter inputan dari user  
* Ketika pemanggilan ke API harus bener2 dijaga, jangan sampai bisa lolos tanpa memakai authentication apapun

__3. Sensitive Data Exposure__  
* Data2 sensitif jangan sampai bocor atau terekspose ke public seperti data password user, data nomor kartu kredit, dll.  
* Data backup Database jangan sampai bisa terdownload oleh public, misalnya habis backup db tapi di taruh di tempat yg bisa di download semua orang  

__4. XML External Entities (XXE)__  
* Jangan pernah menerima upload dari user yg bertipe file XML  
* Untuk setiap tempat yang ada upload filenya, harusnya selalu dicek agar file yg diupload itu adalah tipe file yang sesuai. Kalau tempat upload gambar ya file yg masuk harus gambar, kalau upload excel, ya harus excel file yg masuk.  
* Server mungkin bisa di setting untuk tidak akan pernah bisa execute file XML  

__5. Broken Access Control__  
* Data user jangan sampai bisa dilihat oleh user lainnya yang tidak berhak untuk melihat, apalagi sampai bisa memodif data user lain yg tidak berhak    
* Hak akses user harus benar2 diperhatikan, jika user tidak bisa mengupdate data, harus dipastikan dia tidak bisa mengupdate, jangan sampai ada celah  

__6. Security Misconfiguration__  
* Ini bagian si edow  

__7. Cross-Site Scripting XSS__  
* Inputan/parameter yg masuk harus bener2 dicek agar tidak mengandung tag html yang bisa memanggil js dari website/domain lainnya yg tidak dikenal  

__8. Insecure Deserialization__  
* Pastikan ketika request2 ke API, parameter yang masuk harus di verifikasi dengan benar, sehingga API tidak mengeluarkan data yang tidak seharusnya, misalnya API untuk ambil data user, param userid yang harusnya 1 (user dia sendiri) diganti dengan dengan id lain jadi 3 misalnya, sehingga data yang muncul adalah data user 3 bukan user 1  

__9. Using Components with Known Vulnerabilities__  
* Pastikan library third party yg digunakan itu tidak memiliki vulnerabilities yang akan bisa dimanfaatkan untuk menjadi celah untuk masuk ke dalam sistem.  

__10. Insufficient Logging & Monitoring__  
* Jika tidak ada logging dan monitoring yang cukup, maka kita akan susah tau keadaan aplikasi yang berjalan, sehingga kemungkinan besar yang akan ketemu masalah duluan adalah user pemakai aplikasi nya, bukan kita.  
* Pastikan ada monitoring tools untuk monitor apakah aplikasi dan DB berjalan sebagaimana mestinya
* Pastikan juga aplikasi bisa log untuk kejadian2 yg mungkin akan terjadi diluar flow, sehingga jika ada problem akan lebih mudah trace dari log2 tersebut.

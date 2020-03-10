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


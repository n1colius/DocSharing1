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

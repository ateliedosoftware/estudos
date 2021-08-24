```php

<?php 

function telegram($method, $params){

    require_once './env.php';

    $curl = curl_init();

    curl_setopt_array($curl, array(
    CURLOPT_URL => "https://api.telegram.org/bot".$token."/$method",
    CURLOPT_RETURNTRANSFER => true,
    CURLOPT_MAXREDIRS => 10,
    CURLOPT_TIMEOUT => 30,
    CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
    CURLOPT_CUSTOMREQUEST => "GET",
    CURLOPT_POSTFIELDS => json_encode($params),
    CURLOPT_HTTPHEADER => array(
        "content-type: application/json"
    ),
    ));

    $response = curl_exec($curl);
    $err = curl_error($curl);

    curl_close($curl);

    if ($err) {
    return "cURL Error #:" . $err;
    }else{
    return $response;
    }
}


?>
```

```js
var request = require("request");
require('dotenv').config();


function telegram(method, param, cb){
    var options = {
        method: 'POST',
        url: `https://api.telegram.org/bot${process.env.TELEGRAM_TOKEN}/${method}`,
        json: true,
        formData: param
      };
      
      request(options, function (error, response, body) {
        if (error) throw new Error(error);
      
       if(cb) cb(body,response)
      });


}
module.exports.telegram  = telegram;
```
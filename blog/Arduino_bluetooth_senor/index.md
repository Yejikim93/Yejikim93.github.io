---
layout: post
title:  "Arduino: Bluetooth sensor (HC-06)"
subtitle: "HC-06 sensor"
type: "Development"
blog: true
text: true
author: "YejiKim"
post-header: true
header-img: "img/third_custom.jpg"
order: 6
---



# Information

- 블루투스 (HC-06) 센서 구입 - [[메카솔루션]](http://mechasolution.com/shop/main/index.php) 
- Bluetooth sensor : HC-06 [[센서 사양]](http://mechasolution.com/shop/goods/goods_view.php?goodsno=71794&category=)
- Feature : Android - bluetooth 2.0 (usually, pairing passward: 1234)  
- Arduino download [[download site]](https://www.arduino.cc/en/Main/Software) 


# Connection 
![BluetoothSensor](./img/Bluetooth_sensor.png) </p>

Arduino UNO----->HC-06 

`5V` --------------------> `+5V`     
`GND` -------------------> `GND`   
`2` --------------------> `RX`   
`~3` --------------------> `TX` 

# Code 
     
      #include <SoftwareSerial.h>
      #include <Wire.h>
      
      SoftwareSerial BTSerial(2, 3); // SoftwareSerial(RX, TX)
      byte buffer[1024]; // 데이터를 수신 받을 버퍼
      int bufferPosition; // 버퍼에 데이타를 저장할 때 기록할 위치


      void setup(){     

      Wire.begin();

      Wire.beginTransmission(MPU);
      Wire.write(0x6B);

      Wire.write(0);//MPU6050 을 동작 대기 모드로 변경

      Wire.endTransmission(true);

      // 블루투스
      BTSerial.begin(9600);
      Serial.begin(9600); 
      bufferPosition = 0; // 버퍼 위치 초기화
      }
 
      void loop(){
         num=1;
         BTSerial.println(num);       
      delay(10);
      } 
     
     

# Reference
[https://m.blog.naver.com/PostView.nhn?blogId=eros1092&logNo=221423757801&proxyReferer=https%3A%2F%2Fwww.google.co.kr%2F](https://m.blog.naver.com/PostView.nhn?blogId=eros1092&logNo=221423757801&proxyReferer=https%3A%2F%2Fwww.google.co.kr%2F)


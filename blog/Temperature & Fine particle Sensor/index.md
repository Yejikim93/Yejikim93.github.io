---
layout: post
title:  "Temperature & Fine particle Sensor" 
subtitle: "DHT22 & Nova PM Sensor SDS011"
type: "Raspberry pi"
blog: true
text: true
author: "YejiKim"
post-header: true
header-img: "img/third_custom.jpg"
order: 5
---

DHT22 

# Connection 

# installing 

  # Module 설치
  
  git clone https://github.com/adafruit/Adafruit_Python_DHT.git
  [git 이 설치되어 있지 않은경우 sudo apt-get install git]
  cd Adafruit_Python_DHT
  sudo apt-get update
  sudo apt-get install build-essential python-dev python-openssl
  sudo python setup.py install

  # 실행 py 언어 (temp.py) 로 저장

  import Adafruit_DHT as dht
  import datetime

  wtime = datetime.datetime.now()
  h,t = dht.read_retry(dht.DHT22, 4)
  print wtime, 'Temp={0:0.1f}*C  Humidity={1:0.1f}%'.format(t, h) 



  # 작동여부 Test
  sudo python temp.py
  예) 2016-02-17 20:40:02.125806 Temp=22.4*C  Humidity=34.6%

  Crontab 실행 후 아래 입력
  crontab -e


  #예제1 - 매 10분마다 온도를 기록
  */10 * * * * sudo python /var/www/html/temp.py >> /var/www/html/temp.txt

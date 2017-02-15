###### LAN
Local Area Network

###### WAN
Wide Area Network

###### Internet
TCP/IP 로 동작

###### Ethernet
CSMA/CD 로 동작

###### CSMA/CD
Carrier Sense Multiple Access/Collision Detection. “대충 알아서 눈치로 통신하자”

###### CSMA
- 우리 네트워크 자원을 쓰고 있는 PC나 서버, 즉 CARRIER 가 있는지를 확인해보는 것 (Carrier Sence)
- 네트워크 상에서 두 PC나 서버가 보낼 데이터를 가지고 눈치를 살피고 있었다고 가정하자. 그러다가 네트워크 상에서 통신이 일어나지 않고 있다는 것을 알아내고, 바로 자신의 데이터를 네트워크 상에 실어서 보냈다고 하자. 물론 두 PC나 서버가 동시에. 이 경우를 Multiple Access(다중 접
근)라고 한다.  

###### CD 
위와 같이 두 개의 장비들이 데이터를 동시에 보내려다 부딪치는 경우를 충돌(콜리전，Collision) 이 발생했다고 한다. 따라서 이더넷에서는 데이터를 네트워크에 실어서 보내고 나서도 혹시 다른 PC 때문에 콜리전이 발생하지 않았는지를 잘 점검해야 한다 (Collision Detection).
> 그러다 만약 콜리전이 발생하게 되면 데이터를 전송했던 PC들은 랜덤(Random)한 시간 동안 기다린 다음 다시 데이터를 전송하게 된다


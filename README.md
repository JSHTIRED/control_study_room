# -독서실 관리 시스템  

객체인식을 통해서 핸드폰을 인식하는 경우 DB에 저장하고 이를 기록하는 시스템  
또한 frozen_inference_graph.pb 파일을 별도로 다운을 받아야지 가능함  
(A system that stores and records in the DB when a mobile phone is recognized through object recognition  
Also, you must download the frozen_inference_graph.pb file separately.)
```py
pip install opencv-python
pip install mysql.connector
pip install numpy
```

Raspberry pi3에서 돌릴 수 있으나 fps가 1미만으로 측정됨.  
(It can be run on Raspberry Pi3, but the fps is measured as less than 1.)

![image](https://github.com/JSHTIRED/-/assets/143377935/59012e24-916c-42ce-8f2f-b4515a0decea)

![image](https://github.com/JSHTIRED/-/assets/143377935/69a084a0-ced0-4e99-9bc6-08ea4e91b192)



![image](https://github.com/JSHTIRED/-/assets/143377935/82fafbb0-9b53-43c9-b7fd-ad66fd613c1c)

--- 
정보보호를 위해서 핸드폰 감지시 가리는 사진  
(To protect information, photos are hidden when a cell phone is detected.)

![test](https://github.com/JSHTIRED/control_study_room/assets/143377935/f3bc5ca6-292b-4f16-ba91-b42ec80b6702)


```mermaid
sequenceDiagram
    participant server
    participant client
    participant DB
    participant user
loop if_detect_person
    client->>server : send image by TCP/ip or UDP
    server->>server : check cell_phone by mobilenet_v2 
    loop if_detect_cell_phone
      server->>DB : save object, time 
      server->>user : send message "he use phone"
    end
    loop if_user_want
      user->>DB : check himself
    end
end
```

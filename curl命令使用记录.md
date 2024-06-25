curl 'http://127.0.0.1:9700/api/publicRentalHouseQuery' \
-X POST --header 'Content-Type: application/json' \
-d '{
    "sign":"",
    "nonceStr":"",
    "receiverAccount":"3213",
    "busSerialNum":"",
    "encrypt":"",
    "appAuthToken":"",
    "appId":"1233",
    "timestamp":"",
    "channel": "ZJB_PAY",
    "data": "{\"senderHeader\":{\"sendDate\":\"20200718\",\"sendTime\":\"163801\",\"sendSeqNo\":\"20200718123223111111\",\"txUnitNo\":\"50102000000\",\"sendNode\":\"C51010\",\"txCode\":\"BDC308\",\"receiveNode\":\"C13010\",\"accountDate\":\"20200718\",\"operNo\":\"usr\",\"checkNo\":\"\",\"beginRec\":\"\",\"maxRec\":\"\",\"bk1\":\"\",\"bk2\":\"\"},\"senderBody\":{\"XingMing\":\"各个\",\"ZJLX\":\"01\",\"ZJHM\":\"52242718876667876\",\"XZQHBM\":\"54533\",\"ZLHTBH\":\"4345355\"}}",
    "txCode": "BDC308"
}'

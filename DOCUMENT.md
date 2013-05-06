How Eye-Fi works internally
===

Components
---
1. Hardware based Eye-Fi card
2. Eye-Fi Manager software
3. The website http://manager.eye.fi/

The Eye-Fi Manager is also known as the Eye-Fi agent. On Windows it is an executable program of approximately 4MB in size. The binary is digitally signed by Eye-Fi, Inc. The certificate is issued by “Thawte Code Signing CA”. When running, this program listens on TCP port 59278 for incoming connections. The protocol on port 59278 is HTTP. SOAP messages are used to communicate with the server.

    GET /WS-Proxy
    GET /Status?SOAPAction=
    Error code: 80004005 – The file was not found when trying to download the firmware from the server. The server returned a 404.
    Error code: 8102001C – 


Updating  Firmware
---

The following command tells the Eye-Fi Manager to start a firmware update:

1. URL: `http://127.0.0.1:59278/WS-Proxy?SOAPAction=urn:UpdateFirmware&data=<?xml version='1.0' encoding='utf-8'?><soap:Envelope xmlns:soap='http://schemas.xmlsoap.org/soap/envelope/'><soap:Body><UpdateFirmware xmlns='http://localhost/api/soap/card-config/v1'><MacAddress>00-18-56-03-04-f8</MacAddress><Version>2.0400</Version></UpdateFirmware></soap:Body></soap:Envelope>&key=&method=POST&url=/api/soap/card-config/v1&dojo.preventCache=1238007949245&id=dojo.io.script.jsonp_dojoIoScript23._jsonpCallback`
    
    Referrer: http://manager.eye.fi/app.php
    
    Don’t forget to set the referrer or you will get a 403 Not Authorized.

2. `http://api.eye.fi/api/rest/agent/1.0/?method=firmware.get&Mac=00-18-56-03-04-f9&Version=2.0400`

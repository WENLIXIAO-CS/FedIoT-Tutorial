# Tutorial for Fed-IoT


## A bit of Setup

### Set up Server
- A server can be any computing platform, including
  - **Laptop** (Recommanded)
  - Raspberry Pi
  - Jetson Nano
  - ...
- Install necessary python package

### Set up Client
- Note for Raspberry Pi
    
    - OS Installation
      
      Install  https://www.bilibili.com/read/cv4023024/

      Install system https://stepneverstop.github.io/burn-system2raspberry-in-macos.html

      Make Back-up https://blog.csdn.net/qq_33273956/article/details/87863553

      Enlarge storage https://blog.csdn.net/jumpingpig/article/details/105435543

      Install GUI https://my.oschina.net/yehun/blog/893241

    - Software Problems
      
      Solve the problem of load model https://stackoverflow.com/questions/43385565/importerrorsave-weights-requires-h5py/47856532
      
      WIFI configuration https://zhuanlan.zhihu.com/p/136463580
      
      Solve WIFI problem https://raspberrypi.stackexchange.com/questions/94178/wifi-wont-start
      
      Search for WLAN0 https://blog.csdn.net/zhqh100/article/details/103137477

    - Network Problems
      
      Teamviewer for Linux https://blog.csdn.net/realDonaldTrump/article/details/79694196
      
      VNC for Linux https://blog.csdn.net/u010900754/article/details/53048998
      
      Solve SSH Problem: `vim ~/.ssh/known_hosts`, remove corresponding IP



### Set up Network (WIFI)
1. Turn on WIFI router
2. Connect all devices to this WIFI (server + clients)
3. Address binding (optional)

    - Open browser, and enter URL: [IP OF ROUTER]

    - user: admin pwd: admin

    - PORT Management -> DHCP Setting

        - Scan devices under this wifi

        - Check device's connect by identity

    - VLAN: address binding
        
        - Bing address of server to a fix ip (192.168.43.2 in this program)

        - Fix IP of devices and note them


### Setup Data

1. Generate data
  ```
  data / DATASET / generate_..._.py
  ```
  set number of user `NUM_USER` ( default value is `4`).
  
2. ERROR Correction
  if meet the error " no such file ... / ... / .../ ", add corresponding folder to path

## Experiment

### Overview
run server 
`
python app.py --model server
`

run client
`
python app.py --model client
`

### FL-IoT workflow
Since the procedure of configuring IoT devices is tedious, we prepared two bash script to help automatically execute it by running scripts on server.

1. Preparation (install packages | create folder | sending latest code | others)
    
    - Edit `prepare.sh` on demand
    - Write down IP addresses of all clients in `HOSTS`, separated by spaces.
    - run script `sh prepare.sh`

2. run server 
    ```
    python app.py --model server
    ```
   
3. run clients
  
    - Write down IP addresses of all clients in `HOSTS`, separated by spaces.
    - run script `sh run.sh`

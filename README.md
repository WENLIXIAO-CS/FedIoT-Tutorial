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
- Install necessary python package

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

# The First Step:

1. ** First, let's get the machine's IP with the Nmap tool.**
    - Get our IP using `ifconfig` or `ip a`
      
    ![IP](https://github.com/user-attachments/assets/e6803901-ca25-4cab-8ee6-5ba73e4b0665)

    - Now we know our IP is `192.168.1.15`.
    - let's get the IP address of our machine by enumerating the network with Nmap.
      
          `nmap -sn 192.168.1.0/24`
      
     ![Machine IP](https://github.com/user-attachments/assets/abe2c890-11e1-466c-9d87-90845b5551d3)

2. **Next, let's enumerate the machine's ports.**
      - use RustScan to scan all the ports.
        
         ### Why RustScan Not Nmap?
        - RustScan is faster at scanning ports, which will save us time.
  
        `rustscan -r 1-65535 -a 192.168.1.4`
        
      ![Screenshot 2025-01-02 030347](https://github.com/user-attachments/assets/a02b77c7-e81f-4a30-b057-0bde8264161d)
      ![Screenshot 2025-01-02 030430](https://github.com/user-attachments/assets/b8599c33-0a47-4887-8ed6-4cff20202727)

      - As we can see, there are a lot of ports open.
      - Now, let's exploit as many as we can.
      - HAPPY HUNTING! :D

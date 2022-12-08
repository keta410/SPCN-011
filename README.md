# SPCN-011
การสร้าง VM ใน proxmox
![proxmox](https://user-images.githubusercontent.com/104758471/206357786-c48a7b22-47b1-4cfa-82f8-a81a3c0828b1.jpg)

## 1) Create master vm [ ubuntu-22.04 ]
 *  Create VM
    * Click Create VM จากนั้นทำการตั้งค่าที่กำหนด ใช้ระบบปฏิบัติการ Ubuntu
 ![createvt](https://user-images.githubusercontent.com/104758471/206357279-35fde840-736b-443d-9f98-7b37f89708d9.jpg)
    * VM (Ubuntu)
    ![vm-master](https://user-images.githubusercontent.com/104758471/205892750-70aab375-03b5-425f-bb5c-6809cd387458.png)

 * Clone Master VM Then Make To Template [ 1 vm ]
    * Click right vm(master) > clone
    * Click rignt clone vm(ตัวที่เรา clone มาจาก master)> Convert to template
        * VM (Ubuntu) clone template
![cloneVM-master-template](https://user-images.githubusercontent.com/104758471/205887748-770e5d9e-e69b-412c-a25c-a9341955de53.png)

 * Clone From Template [ 2 vm ]
 ![clone](https://user-images.githubusercontent.com/104758471/206358858-8986f898-e0e5-485b-96dc-198880d321ce.jpg)

    * Change Hostname
        ```
        ->sudo hostnamectl set-hostname [set name]
        ->bash //for start shell again
        ```
    * Set Local Time 
        ```
        ->sudo timedatectl set-timezone Asia/Bangkok
        ```
    * Check Date 
        ```
        ->sudo date
        ```
    * Command of Machine-ID
        * Check Machine-ID
        ```
        ->cat /etc/machine-id
        ->ls -l /var/lib/dbus/machine-id       //ดูเส้นทางของ machine-id
        ```
        * Change Machine-ID (Make in Root)
        ```
        ->sudo -i       //เปลี่ยนมาเป็น root
        ->nano /etc/machine-id       //คำสั่งที่ใช้เข้าไปในที่เก็บ machine-id
        ```
        เมื่อเข้าไปแล้วให้ทำการ <delete> machine-id จากนั้น Ctl+X(เพื่อ Save) และกด Y เพื่อยืนยันในการทำ
        ```
        ->cat /etc/machine-id
        ->ln -s /etc/machine-id /var/lib/dbus/machine-id      //คำสั่งที่ใช้ link เชื่อมต่อ machine-id
        ->reboot 
        ```

    * Summary of clone from template (clone1)
    ![clone-from-tem1](https://user-images.githubusercontent.com/104758471/205889238-db89e9f4-e1d6-49fb-bca6-7838e583d964.png)
    * Summary of clone from template (clone2)
    ![clone-from-tem2](https://user-images.githubusercontent.com/104758471/205890235-e36a6132-942f-4676-bdf2-b9707181f11f.png)

## 2) Create vm form other os [ kali ]
* Click Create VM จากนั้นทำการตั้งค่าที่กำหนด ใช้ระบบปฏิบัติการ Kali
 * Summary Screen of Kali
![vm-kali](https://user-images.githubusercontent.com/104758471/205692921-a4357c79-0a88-4809-9d3c-98afe67ac459.png)
        
## 3) Create container template
 * Create CT
    * Click Create CT
![createct](https://user-images.githubusercontent.com/104758471/206357654-95d886eb-8be1-40ea-8e51-d5563d48ffc0.jpg)
 * Summary And Console Screen
    * Summary Screen of CT
![ct_summary-ep1](https://user-images.githubusercontent.com/104758471/205688606-4131772b-1f1f-499f-acde-acf7c846b83d.png)
    * Console Screen of CT
![ct_console-ep1](https://user-images.githubusercontent.com/104758471/205689184-0b5bc6d6-7793-4d41-bd1d-92ffbe941108.png)

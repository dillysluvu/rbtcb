
#  1. Cơ khí :                                                                                                                                                                                                                                                                                                                                                                                                                                  
-  Thiết kế bộ khung 3D cho Robot bằng các phần mềm như Fusion 360…                                                                                                                                                                                                                                                                                                                                                                                                      
-  Cố định các linh kiện vào khung Robot.                                                                                                                                                                                                                                                                                                                                                                                                     
# 2. Điện tử :                                                                                                                                                                                                                                                                                                                                                                                                                                 
##   - Linh kiện chính:                                                                                                                                                                                                                                                                                                                                                                                                                           
  -   Arduino Uno R3                                                                                                                                                                                                                                                                                                                                                                                                                               
  -   Động Cơ DC Giảm Tốc V1 Dual Shaft Plastic Geared TT Motor                                                                                                                                                                                                                                                                                                                                                                                    
  -   Cảm Biến gia tốc GY-521 6DOF IMU MPU6050
  -   Pin Sạc 18650 Li-Ion Rechargeable Battery 3.7V 2500mAh 5C                                                                                                                                                                                                                                                                                                                                                                                    
  -   2 X 18650 Battery Holder                                                                                                                                                                                                                                                                                                                                                                                                                     
  -   Module điều khiển động cơ l298n                                                                                                                                                                                                                                                                                                                                                                                                              
  -   Bánh Xe TT Motor Plastic Wheel 65mm                                                                                                                                                                                                                                                                                                                                                                                                          
## -  Các bước lắp đặt :                                                                                                                                                                                                                                                                                                                                                                                                                          
  -   Lắp đặt bộ khung, motor và bánh xe                                                                                                                                                                                                                                                                                                                                                                                                       
  -   Lắp mạch Arduino và Module điều khiển động cơ                                                                                                                                                                                                                                                                                                                                                                                            
  -   Lắp đặt cảm biến gia tốc theo thiết kế đã vẽ                                                                                                                                                                                                                                                                                                                                                                                           
  -   Điều chỉnh biến trở trên cảm biến nhằm tăng độ chính xác                                                                                                                                                                                                                                                                                                                                                                                 
## -  Sơ đồ nối dây :                                                                                                                                                                                                                                                                                                                                                                                                                             
![](https://scontent.fhan2-4.fna.fbcdn.net/v/t1.15752-9/439874518_945107760620865_6261747267592226966_n.png?_nc_cat=105&ccb=1-7&_nc_sid=5f2048&_nc_ohc=2Mz2zodEO-cAb7LzYIB&_nc_ht=scontent.fhan2-4.fna&oh=03_Q7cD1QFk5oHW3apKuqSf8DKbVrkEe5kDM7L4-rbaJgbke6_2ng&oe=6656E485)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                
# 3. Nguyên lý hoạt động                                                                                                                                                                                                                                                                                                                                                                                                                       

- Trái tim của chú Robot tự cân bằng chính là những viên pin Lithium-ion. Viên pin này đóng vai trò cung cấp năng lượng cho hoạt động của các linh kiện điện tử, giống như nguồn cung cấp "sự sống" giúp con Robot có thể vận hành được.
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           
-  Để giữ được thăng bằng khi di chuyển, Robot được trang bị cảm biến gia tốc MPU6050 - một linh kiện kỳ diệu kết hợp giữa gia tốc kế và con quay hồi chuyển. Nhờ vậy, cảm biến có khả năng đo lường chính xác gia tốc và vận tốc góc theo 3 trục toạ độ X, Y, Z. Dựa trên những dữ liệu này, cảm biến sẽ phát hiện ra bất kỳ chuyển động hay góc nghiêng nào của Robot hiện tại để tính toán và điều khiển, giúp Robot luôn giữ vững trạng thái thăng bằng.
                                                                                                                                                                                                                                                                                                                                                                                                                                            
-  Mọi dữ liệu từ cảm biến MPU6050 sẽ được gửi tới Arduino - bộ não điều khiển của Robot. Ở đây, Arduino sẽ phân tích và tính toán chính xác góc nghiêng cũng như tín hiệu điều khiển cần thiết để Robot có thể lấy lại trạng thái cân bằng. Những tín hiệu điều khiển này sau đó sẽ được truyền tới module L298N.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       
-  Module L298N chính là bộ phận chịu trách nhiệm điều khiển hai động cơ then chốt giúp Robot di chuyển. Khi nhận được tín hiệu từ Arduino rằng Robot đang nghiêng, L298N sẽ linh hoạt điều chỉnh vận tốc của hai bánh xe để Robot lấy lại trạng thái thăng bằng. Nhờ vậy, dù di chuyển đi đâu, chú Robot vẫn luôn duy trì được tư thế đứng thẳng thăng bằng một cách tốt nhất.

# 4. Thư viện sử dụng  :
-  [PID_v1.h](https://github.com/br3ttb/Arduino-PID-Library/blob/master/PID_v1.h)                          
-  [I2Cdev.h](https://github.com/jrowberg/i2cdevlib/blob/master/Arduino/I2Cdev/I2Cdev.h)
-  [MPU6050_6Axis_MotionApps20.h](https://github.com/jrowberg/i2cdevlib/blob/master/Arduino/MPU6050/MPU6050_6Axis_MotionApps20.h)



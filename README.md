# ASCIS-2023-WarmUp_WritreUp
- Do server đã đóng nên mình không thể lưu flag hoàn chỉnh được mong mn thông cảm.
- Thêm vào việc không có src làm cho mình khó có thể dựng lại chall
## A big Blue Whale 
- Đầu tiên, với những chall blackbox, mình thường hày dùng dirsearch để có thể tìm những path bị ẩn.
- Ở đây mình tìm được ```/Dockerfile```
- Truy cập vào thì ta sẽ được một file như hình.

![image](https://github.com/TooBunReal/ASCIS-2023-WarmUp_WritreUp/assets/89735990/0b7bd2f1-3f3b-47be-8ac6-c0bafd6fb83e)

- File này có một dòng rất đáng chú ý đó là ```FROM sectigo1/webbase:latest```
- Từ đây mình sẽ dùng lệnh ```git pull sectigo1/webbase:latest``` để check xem thế nào.
- Đến bước này có nhiều cách để bạn có thể lấy flag. Dưới đây mình sẽ giới thiệu 2 cách của mình.
- Cách 1:
  + Sau khi đã pull về mình dùng lệnh ```docker run sectigo1/webbase``` để chạy image.
  + Tiếp theo đó check id của image và dùng lệnh ```docker exec -it -u root (id) sh``` để có thể chạy một shell dưới quyền root.
  + Sau khi có sh việc của mình chỉ đơn giản là vào root và cat flag.txt.
      ![image](https://github.com/TooBunReal/ASCIS-2023-WarmUp_WritreUp/assets/89735990/cc52d917-0e0e-4ccf-a1f7-c5d4d5a61623)
- Cách 2:
  + Cách này hơi lowtech nhưng mà nó khá nhanh =))
  + Bạn bật docker desktop lên vào phần file và đọc flag thôi :>
       ![image](https://github.com/TooBunReal/ASCIS-2023-WarmUp_WritreUp/assets/89735990/6dabe453-a106-4600-9524-b5d9086493e0)
Flag: ```ASCIS{1t_R3a114_30rks_0n_m4_m@chin3}```

## Hide and Seek! 
- Mình khá trigger với chall này khi tìm mọi cách vẫn không fuzz được flag và bất cứ dữ kiện gì.
- Sau khi đọc kỹ lại Res và Req thì mình phát hiện ra vài điều.

  ![image](https://github.com/TooBunReal/ASCIS-2023-WarmUp_WritreUp/assets/89735990/802a9e23-ae71-4ade-a9e5-820928567ef9)

  ![image](https://github.com/TooBunReal/ASCIS-2023-WarmUp_WritreUp/assets/89735990/26174398-558a-4569-9461-b5dfe5763fb9)
- Ở đây mình cũng không rõ cái nginx-proxy hoặc động như nào, nhưng mình nghi ngờ nó liên quan tới vitual host.
- Sau đó mình đã thử gửi request đến host là 127.0.0.1:18000
- Check lại req thì quả là có flag thật.
- Sau vài lần brute force thì mình nhận ra chỉ cần đổi port là giá trị trả về của flag nó sẽ khác.
- Đây là flag hoàn chỉnh: ```ASCIS{0ppp!_Y0u-Rand0mly-F0und_M3_Gre@t!}```

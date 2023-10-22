# ASCIS-2023-WarmUp_WritreUp
- Do server đã đóng nên mình không thể lưu flag hoàn chỉnh được mong mn thông cảm.
- Thêm vào việc không có src làm cho mình khó có thể dựng lại chall
## A big Blue Whale 
- Đầu tiên, với những chall blackbox, mình thường hày dùng dirsearch để có thể tìm những path bị ẩn.
- Ở đây mình tìm được ```/Dockerfile```
- Truy cập vào thì ta sẽ được một file như hình.

  ![image](https://github.com/TooBunReal/ASCIS-2023-WarmUp_WritreUp/assets/89735990/478c2bbd-0e00-4472-b775-4fc2568f813d)


- File này có một dòng rất đáng chú ý đó là ```FROM sectigo1/webbase:latest```
- Từ đây mình sẽ dùng lệnh ```git pull sectigo1/webbase:latest``` để check xem thế nào.
- Đến bước này có nhiều cách để bạn có thể lấy flag. Dưới đây mình sẽ giới thiệu 2 cách của mình.
- Cách 1:
  + Sau khi đã pull về mình dùng lệnh ```docker run sectigo1/webbase``` để chạy image.
  + Tiếp theo đó check id của image và dùng lệnh ```docker exec -it -u root (id_docker) sh``` để có thể chạy một shell dưới quyền root.
  + Sau khi có sh việc của mình chỉ đơn giản là vào root và cat flag.txt.
  
      ![image](https://github.com/TooBunReal/ASCIS-2023-WarmUp_WritreUp/assets/89735990/a9eac522-1f70-4694-b0ab-77b71637b8e4)

- Cách 2:
  + Cách này hơi lowtech nhưng mà nó khá nhanh =))
  + Bạn bật docker desktop lên vào phần file và đọc flag thôi :>
       ![image](https://github.com/TooBunReal/ASCIS-2023-WarmUp_WritreUp/assets/89735990/79a58583-29ca-47a5-930d-cc3b5071e458)

Flag: ```ASCIS{1t_R3a114_30rks_0n_m4_m@chin3}```

## Hide and Seek! 
- Mình khá trigger với chall này khi tìm mọi cách vẫn không fuzz được flag và bất cứ dữ kiện gì.
- Sau khi đọc kỹ lại Res và Req thì mình phát hiện ra vài điều.

  ![image](https://github.com/TooBunReal/ASCIS-2023-WarmUp_WritreUp/assets/89735990/d0759aee-7909-49bd-95b8-0182c6cf5d40)

- Ở đây mình cũng không rõ cái nginx-proxy hoặc động như nào, nhưng mình nghi ngờ nó liên quan tới vitual host.
- Sau đó mình đã thử gửi request đến host là 127.0.0.1:18000

  ![image](https://github.com/TooBunReal/ASCIS-2023-WarmUp_WritreUp/assets/89735990/97dbb025-c787-42d3-aed1-b921fa03bd31)


- Check lại req thì quả là có flag thật.
- Sau vài lần brute force thì mình nhận ra chỉ cần đổi port là giá trị trả về của flag nó sẽ khác.
- Đây là flag hoàn chỉnh: ```ASCIS{0ppp!_Y0u-Rand0mly-F0und_M3_Gre@t!}```

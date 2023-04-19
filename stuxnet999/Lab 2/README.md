## Chall src: https://mega.nz/file/ChoDHaja#1XvuQd49c7-7kgJvPXIEAst-NXi8L3ggwienE1uoZTk

Nốt con lab 2 rồi bế quan 1 tuần chạy deadline 😫.

#### Flag 1:

- Dựa vào description: `He is supposedly a very popular "environmental" activist`. Nhà hoạt động môi trường,.... nhưng mà lại note cái environmental, giống với cái
sample Lab 0, check biến môi trường bằng plugin `envars` và bú flag đầu thôi.

Để ý mỗi proc, NEW_TMP đều có phần path như này: *C:\Windows\ZmxhZ3t3M2xjMG0zX1QwXyRUNGczXyFfT2ZfTDRCXzJ9*

B64decode directory đích ra, ăn flag 1 :) : `flag{w3lc0m3_T0_$T4g3_!_Of_L4B_2}`

#### Flag 2:

- Des: `he told us that his go to applications are browsers, his password managers etc.` =)) Khả năng là giống Lab 1 rồi. Run `cmdline` và thấy ngay:

![image](https://user-images.githubusercontent.com/113530029/232977352-00042cb6-6d88-4e50-8ba1-a62b3bad3822.png)

:v Chuẩn luôn nhé, extract ra như lab 1 thôi.

![image](https://user-images.githubusercontent.com/113530029/232977767-12eded09-f141-4c9b-844c-4e96053bdbb2.png)

Giờ cần tìm pass của file kdbx nữa, để ý des này "his password managers etc". Tìm thử bằng grep:

![image](https://user-images.githubusercontent.com/113530029/232978130-f9dc5a32-8ec1-4a24-917d-4e149da1a211.png)

Có 1 file `Password.png` rất sus này, extract ra và xem thử:

![image](https://user-images.githubusercontent.com/113530029/232978410-05bdc53b-a328-452e-9c8f-2210b3b2b73e.png)

Pass ở góc kìa =)) : ***P4SSw0rd_123*** . Mở kdbx bằng app `Keepass2` và bú flag thôi.

Lần mò vào thùng rác thấy có username tên Flag, edit Entry và có flag 2 :> :

![image](https://user-images.githubusercontent.com/113530029/232979300-d1649bec-f657-4cde-861a-b3f8697f9a70.png)

-> `flag{w0w_th1s_1s_Th3_SeC0nD_ST4g3_!!}`


#### Flag 3:

- Dựa vào des tiếp: `he told us that his go to applications are browsers`. Vậy là browser sẽ là cái ta tập trung tiếp theo. Nhìn vào pstree:

![image](https://user-images.githubusercontent.com/113530029/232975605-3e37a118-3776-4590-9d10-27173e04a751.png)

Ở dưới nữa thì chả có gì đâu :v . Nhìn vào là thấy được browser được nhắc tới ở đây là chrome rồi. Sau 1 hồi mày mò thì mình biết là volatility community build rất nhiều plugin đặc thù. Ở đây mình sử dụng bộ plugin: https://github.com/superponible/volatility-plugins

Dùng plugin `chromehistory` để xem lịch sử duyệt web:

![image](https://user-images.githubusercontent.com/113530029/232976350-21db0ac8-0d77-4d5c-8428-c4da83278605.png)

Để ý có link mega giống với lúc download lab về, mở ra xem nào.

![image](https://user-images.githubusercontent.com/113530029/232979763-51d470f9-4d89-4bdd-abdd-e1433e1a8171.png)

`Important.zip` à....Ok sắp tới đích rồi đấy. Down zip về và mở ra xem:

![image](https://user-images.githubusercontent.com/113530029/232979965-51ff84b0-f04f-4e61-be34-ab39bf887be0.png)

Rồi, SHA1 hash cái flag 3 của lab 1 là đc pass, mở ra và bú flag 3:

![image](https://user-images.githubusercontent.com/113530029/232980098-57d07f9a-6e4f-4945-8b6c-8cc97bdbf8ef.png)

-> `flag{oK_So_Now_St4g3_3_is_DoNE!!}`

++ Clear lab 2.

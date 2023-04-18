## Chall src: https://mega.nz/#!6l4BhKIb!l8ATZoliB_ULlvlkESwkPiXAETJEF7p91Gf9CWuQI70

Theo đề thì nó có 3 flag, bắt đầu tìm nào :D

Tác giả cho đề khá nhiều dữ kiện rồi. WU này mình sẽ viết theo thứ tự flag chứ không theo quá trình mình làm nhé.

Volatility và đấm thôi. Chall này mình giải full bằng Vol 2.

Đầu tiên dùng plugin `imageinfo` để check profile:

![image](https://user-images.githubusercontent.com/113530029/232861654-4d9f4083-e094-46ee-9c1d-c5d61e690746.png)

Vậy là window, thêm profile vào và run plugin `pstree`:

![image](https://user-images.githubusercontent.com/113530029/232863000-2f75f072-6f7f-4e13-97a8-3b8891150327.png)

#### Với Flag 1:

Dựa vào Description: 

- `we suddenly saw a black window pop up with some thing being executed`. Vậy ta có thể hiểu black window ở đây là `cmd`.

Xem `pstree` như trên thì dump file có mỗi 1 proc `cmd` thôi :v, nên ta sẽ tập trung luôn vào proc này.

Hmm, cmd execute gì? dùng plugin `consoles`:

![image](https://user-images.githubusercontent.com/113530029/232864910-9df3ae06-94dc-4a93-a8ea-bbd16f91fab0.png)

Heh, ta thấy cmd execute 1 lệnh tên là `St4G3$1`. Vậy đây chính là hướng tới flag 1 rồi :> . Cmd execute lệnh và trả ra 1 dòng base64: `ZmxhZ3t0aDFzXzFzX3RoM18xc3Rfc3Q0ZzMhIX0=`

Decode ra và ta có flag của stage 1: `flag{th1s_1s_th3_1st_st4g3!!}`

#### Tiếp là Flag 2 nào:

Dựa vào Description:

- `When the crash happened, she was trying to draw something`. Vẽ vời gì à, nhìn vào process tree ở trên, ắt hẳn là `mspaint.exe` rồi. Ngoài ra nó cũng là process con hoạt động cùng parent với cmd ở trên, đủ sus để ta suy xét đến.

Khá tò mò là bà chị ấy vẽ gì nhỉ, tiến hành retrieve lại nhé.

Dump process đó ra bằng command này:

![image](https://user-images.githubusercontent.com/113530029/232868963-995f8c04-e8f9-4268-a7f8-e3dcb5595cbd.png)

File dump ra thay extension thành ".data", rồi mở bằng GIMP:

![image](https://user-images.githubusercontent.com/113530029/232869454-7c9088e8-5cd4-4bfa-aa7c-4ef4b89e1503.png)

Yup, chỉnh lại Height, Width, Offset, tới khi thấy text thôi. Hơi ngố nhưng mà mình không biết cách khác logic hơn :/

![image](https://user-images.githubusercontent.com/113530029/232870091-39957bf3-2198-4289-b65d-d4a15633ebc6.png)

Mirror lại theo 2 chiều là thấy text của flag stage 2 thôi, chữ xấu vl: `flag{G00d_BoY_good_girL}`.

#### Flag 3:

Dựa vào Description: 

- `Your job is get all her important files from the system.` Hmm...tìm file gì quan trọng của bà đó. Nếu sử dụng plugin `filescan` để mò thì khá là Eye Lỏd với mình ở thời điểm viết WU này =))

Hên là từ mục flag 1, mình có sử dụng plugin `cmdline`, và thấy bà chị này đã mở file "quan trọng" đó: 

![image](https://user-images.githubusercontent.com/113530029/232872288-29d1d339-480a-4916-9e2e-0520c4dd89ed.png)

Độ quan trọng thể hiện ở cái tên của file rồi đó :v extract ra xem có gì nào.

Scan để tìm offset của file Rar:

![image](https://user-images.githubusercontent.com/113530029/232873383-555911d4-ee1f-4a26-98e0-5c2eabd565e3.png)

Sau đó extract ra:

![image](https://user-images.githubusercontent.com/113530029/232873524-57b62744-39ac-43f0-a33b-8769478a7674.png)

Ban đầu mở file dump đó bằng Linux thì chả có gì khác ngoài file `flag.png` bị lock, nhưng mà mở bằng winrar thì có comment này:

![image](https://user-images.githubusercontent.com/113530029/232874406-54e72e6c-b1f6-4b2b-b8a9-33d775babee0.png)

Oh, biết pass là gì luôn rồi. Cứ thế mà lấy pass thôi. Sử dụng plugin `hashdump`:

![image](https://user-images.githubusercontent.com/113530029/232875802-6432d99d-c7f2-4f56-8c7c-7930658da625.png)

Lưu trữ hash này ở form `tên:ID:account:pass:::`

Lấy hash của pass và chuyển thành uppercase, mở Rar bằng upperhash đó (F4FF64C8BAAC57D22F22EDC681055BA6) và múc flag thôi :v :

![image](https://user-images.githubusercontent.com/113530029/232877822-356c6608-46f3-42c1-8bf0-7cbe8f6a055d.png)

Flag stage 3: `flag{w3ll_3rd_stage_was_easy}`

++ Oke, clear lab rồi :3.

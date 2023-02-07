Đầu tiên e check `file` 2 ảnh, thấy `1.png` đuôi png nhưng lại là jpg, nên e check hex data với 1 vài tool xem chunk trên mạng, nhưng cả 2 cái không có lỗi, không có comment hay data thừa. Nên e bỏ qua hướng này.

Lúc sau e để ý cả 2 ảnh cùng size, nhìn lại giống hệt nhau nên khả năng là giấu trong màu, và tìm bằng cách so sánh màu 2 ảnh.

So sánh xong e được 1 dãy như này:
```
(111, 24, 15) (70, 0, 0)
(104, 17, 8) (108, 0, 0)
(106, 19, 10) (97, 0, 0)
(108, 21, 12) (103, 0, 0)
(107, 20, 11) (123, 0, 0)
(106, 19, 10) (72, 0, 0)
(106, 19, 10) (49, 0, 0)
(107, 20, 11) (100, 0, 0)
(108, 21, 12) (49, 0, 0)
(107, 20, 11) (110, 0, 0)
(107, 20, 11) (54, 0, 0)
(107, 20, 11) (95, 0, 0)
(107, 20, 11) (56, 0, 0)
(107, 20, 11) (51, 0, 0)
(107, 20, 11) (55, 0, 0)
(107, 20, 11) (119, 0, 0)
(107, 20, 11) (51, 0, 0)
(107, 20, 11) (51, 0, 0)
(109, 22, 13) (110, 0, 0)
(110, 23, 14) (95, 0, 0)
(109, 22, 13) (83, 0, 0)
(107, 20, 11) (85, 0, 0)
(105, 18, 9) (78, 0, 0)
(105, 18, 9) (42, 0, 0)
(106, 19, 10) (95, 0, 0)
(101, 14, 5) (49, 0, 0)
(103, 16, 7) (109, 0, 0)
(106, 19, 10) (52, 0, 0)
(109, 22, 13) (54, 0, 0)
(111, 24, 15) (101, 0, 0)
(111, 24, 15) (53, 0, 0)
(110, 23, 14) (95, 0, 0)
(109, 22, 13) (49, 0, 0)
(103, 16, 7) (53, 0, 0)
(104, 17, 8) (95, 0, 0)
(105, 18, 9) (115, 0, 0)
(106, 19, 10) (48, 0, 0)
(107, 20, 11) (95, 0, 0)
(108, 21, 12) (99, 0, 0)
(109, 22, 13) (48, 0, 0)
(109, 22, 13) (79, 0, 0)
(106, 19, 10) (108, 0, 0)
(107, 20, 11) (125, 0, 0)
```
nhìn bên màu của `2.png` hơi bị đặc biệt (g, b bằng 0 hết), cộng thêm nhìn nó giống ASCII encode, với cả đề tên "Blood" SUN* :v nên e lấy giá trị red ra, decode và được flag:

FLAG: `Flag{H1d1n6_837w33n_SUN*_1m46e5_15_s0_c0Ol}`


#Solve
```
from PIL import Image
img1 = Image.open("D:/temporary/1.png")
pix1 = img1.load()
img2 = Image.open("D:/temporary/2.png")
pix2 = img2.load()

for x in range(img1.size[0]):
    for y in range(img1.size[1]):
        if pix1[x, y] != pix2[x, y]:
            r, g, b = pix2[x, y]
            print(chr(r), end = "")
```

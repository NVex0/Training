Code để Solve của mình :D, chall này dễ ác. Coding tí thôi chứ chả có gì đặc sắc.
```
with open(r"D:\TEST\riffle", "rb") as f:
    origin = f.read()
index = 0
endidentifier = [73, 69, 78, 68, 174, 66, 96, 130]
pic1 = []
pic2 = []
pic3 = []
pic4 = []
check1 = True
check2 = True
check3 = True
check4 = True

def check(Ls):
    if Ls[-8:] == endidentifier:
        return False
    return True
        
while index < len(origin):
    check1 = check(pic1)
    check2 = check(pic2)
    check3 = check(pic3)
    check4 = check(pic4)
    if check1:
        pic1.append(origin[index])
        index += 1
    if check2:
        pic2.append(origin[index])
        index += 1
    if check3:
        pic3.append(origin[index])
        index += 1
    if check4:
        pic4.append(origin[index])
        index += 1

with open(r"D:\TEST\pic1.png", "wb") as p:
    p.write(bytearray(pic1))
with open(r"D:\TEST\pic2.png", "wb") as p:
    p.write(bytearray(pic2))
with open(r"D:\TEST\pic3.png", "wb") as p:
    p.write(bytearray(pic3))
with open(r"D:\TEST\pic4.png", "wb") as p:
    p.write(bytearray(pic4))
```

Sau khi chạy code được 4 ảnh con King trong bộ bài, nó chứa flag luôn.

FLAG: `HACKLABS{You'v3_got_to_know_wh3n_to_hold'3m_6bb24d9c}`

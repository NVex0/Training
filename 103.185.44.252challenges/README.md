#Full code của mình ở đây, ngồi cài module pycryptodome lỗi lên lỗi xuống nên làm lâu vãi chưởng :D

```
from PIL import Image
from number import long_to_bytes
img = Image.open("D:\Downloads\hekleb.png")
pix = img.load()

def check(string):
    count1 = 0
    count0 = 0
    for i in string:
        if i == '1':
            count1 += 1
        elif i == '0':
            count0 += 1
    if count1 + count0 == len(string):
        return True
    return False

out = ""
try:
    for x in range(img.size[0]):
        for y in range(img.size[1]):
            val = (pix[x, y])
            for channel in range(0, 3):
                out += str(val[channel])
    index1 = 0
    index2 = 16
    while index2 < len(out):
        tmp = out[index1 : index2]
        fin = tmp[8:] + tmp[:8]
        if check(fin):
            fin = int(fin, 2)
            fin = long_to_bytes(fin)
            print(str(fin)[2:-1], end = "")
        index1 += 16
        index2 += 16
except Exception as e:
    print("Cause: ", e)
```
Flag : hacklabs{My_d0g_steps_On_a_LS_Bee_&_sw4pped}

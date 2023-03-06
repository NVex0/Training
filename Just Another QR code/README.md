```Reverse img:
with open(r"D:\ZZTask\reversed.bmp", "r") as f:
    data = f.read()
index = 0
with open(r"D:\ZZTask\nonrev.bmp", "w") as f:
    while index < len(data):
        out = ""
        if index + 3 < len(data):
            out += data[index + 2] + data[index + 1] + data[index]
            index += 3
        else:
            out += data[index]
            index += 1
        f.write(out)```

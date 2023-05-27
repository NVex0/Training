Dùng volatility, plugin `filescan`, để ý phần Desktop có nhiều file khá hay. Dùng command sau để lọc:

`python2 vol.py -f ~/Desktop/MemoryDump_Lab3.raw --profile=Win7SP1x86 filescan | grep Desktop`

Dump ra 3 file:

+ 1 file ảnh.
+ 1 file text.
+ 1 file python.

Dựa vào file python, ta biết được file text là kết quả của strings xor với 03, xor cái text đã có với 03 sẽ ra nửa đầu flag: 
![image](https://github.com/NVex0/Training/assets/113530029/ee4efaa5-79f7-4a1a-b5dd-c08aae136269)
Đề nói rằng phải có part 1 mới có part 2 + thêm note về steghide, decrypt steghide cái file ảnh với pass là nửa đầu flag thôi:
![image](https://github.com/NVex0/Training/assets/113530029/0aac801e-8979-44fb-88cd-e188446ce714)

Flag: `inctf{0n3_h4lf_1s_n0t_3n0ugh}`

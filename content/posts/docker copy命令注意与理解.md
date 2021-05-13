copy dir1 ./

结果并不是
./
    dir1

而是
./ 
    dir1里的文件与目录



---
第二

COPY dir1/*  ./ 

结果并不是
./   
   dir1
          xxx/file.txt

而是
./
   file.txt

也就是dir1的目录结构不会复制。*号是将所有目录/包括子目录下的文件复制而已

---



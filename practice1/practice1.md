## Task 2

```bash
man top
```
![[Pasted image 20230304234544.png]]

## Task 3
```bash
pwd
$ /home/sirazetdinov/Desktop

mkdir foo foo/folder
cd foo/folder

mkdir bronze bronze/files bronze/media
mkdir silver silver/files silver/media
mkdir gold gold/files gold/media
mkdir tmp

tree > foo/folder/tmp/struct.txt
[mv struct.txt foo/folder/tmp]
```

**struct.txt**
```txt
.
├── foo
│   └── folder
│       ├── bronze
│       │   ├── files
│       │   └── media
│       ├── gold
│       │   ├── files
│       │   └── media
│       ├── silver
│       │   ├── files
│       │   └── media
│       └── tmp
└── struc.txt

13 directories, 1 file
```


## Task 4
```bash
cd foo/folder/tmp

touch empty_file.txt && echo -e "hello world\n hello world again" >> empty_file.txt

bat empty_file.txt
```
![[Pasted image 20230305000953.png]]
```bash
du empty_file.txt
$ 4        empty_file.txt
```

## Task 5
```bash
cd foo/folder/tmp
wget https://github.com/qwerty29544/BigDataEssentials/raw/main/Practice1_LinuxCommands/data.tar.gz 

tar -xf data.tar.gz -C foo/folder/tmp
[tar -xvf data.tar.gz]

ls -la
```

## Task 6
```bash
mv *(.eps|.png|.jpg) foo/folder/bronze
du foo/folder/bronze

mv MIREA_Gerb_Color.jpg MIREA_RGB.jpg
```

## Task 7
```bash
head MIREA_RGB.jpg
```
![[Pasted image 20230305010103.png]]

## Task 8
```bash
mv *(.txt|.TXT|.csv|.db) ~/Desktop/foo/folder/bronze/files

head TNVED1.TXT
file -i TNVED1.TXT
iconv -f CP866 -t UTF-8//TRANSLIT tnved1_utf.txt -o tnved1_utf.txt
head tnved1_utf.txt

iconv -f CP866 -t UTF-8//TRANSLIT TNVED3.TXT -o tnved3_utf.txt
head tnved1_utf.txt

iconv -f CP866 -t UTF-8//TRANSLIT TNVED2.TXT -o tnved2_utf.txt
head tnved1_utf.txt

mv *utf.txt ~/Desktop/foo/folder/silver/files
```

## Task 9
```vim
:%s/|/||/g
```

```bash
bat tnved1_utf.txt
tree >> final.txt
```

final.txt
```txt
.
├── bronze
│   ├── files
│   │   ├── GAZ.csv
│   │   ├── okato.csv
│   │   ├── oksm.csv
│   │   ├── pizza_orders.db
│   │   └── TNVED1.TXT
│   ├── linux_logo.jpg
│   ├── media
│   ├── MIREA_Gerb_Colour.eps
│   ├── MIREA_Gerb_Colour.png
│   └── MIREA_RGB.jpg
├── empty_file.txt
├── final.txt
├── gold
│   ├── files
│   └── media
├── silver
│   ├── files
│   │   └── tnved1_utf.txt
│   └── media
└── tmp
    ├── data
    │   ├── TNVED2.Txt
    │   └── TNVED3.Txt
    ├── data.tar.gz
    └── struct.txt
```

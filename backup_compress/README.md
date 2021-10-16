# GNU / Linux 各種壓縮與解壓縮指令

##### 目錄 

[.tar]](#tar)  
[.gz]](#gz) 

<a name="tar"/>

### TAR 指令 (僅打包，無壓縮)

- 套件名稱：tar。
- 後綴：.tar

#### 常用參數

| 參數 | 說明                                                             |
| ---- | ---------------------------------------------------------------- |
| -c   | 建立打包檔案，可搭配 -v 來觀看打包過程。                         |
| -C   | 目錄。打包或壓縮目錄可省略。解開打包或解壓縮用來指定放置的目錄   |
| -v   | 在打包或壓縮的過程中顯示檔案。                                   |
| -t   | 檢視已打包檔案的內容含有哪些檔案。                               |
| -x   | 解開已打包的檔案、或解壓縮檔案。                                 |
| -z   | 使用 gzip 壓縮或者解壓縮，建議使用副檔名 .tar.gz 方便識別。      |
| -j   | 使用 bzip2 壓縮或者解壓縮，建議使用副檔名 .tar.bz2 方便識別。    |
| -J   | 使用 xz 壓縮或者解壓縮，建議使用副檔名 .tar.xz                   |
| -f   | 被處理的檔名。此參數使用要立即接檔名，建議單獨使用。             |
| -p   | 保留備份資料的原始權限與屬性。                                   |
| -P   | 保留絕對路徑。被打包檔案結構含有根目錄。                         |
| -N   | 比對日期。比此參數後面接的日期 (yyyy/mm/dd) 還要新的才會被打包。 |

- 打包：
  > [ jonny@linux ~ ]
  >
  > FileName.tar DirName
- 解包：
  > [ jonny@linux ~ ]
  >
  > FileName.tar


<a name="gz"/>

### .gz


- 套件名稱：gzip。
- 壓縮
  > [ jonny@linux ~ ]
  >
  > FileName
- 解壓縮 1：
  > [ jonny@linux ~ ]
  >
  > FileName.gz
- 解壓縮 2：
  > [ jonny@linux ~ ]
  >
  > FileName.gz

### .tar.gz

- 套件名稱：gzip。
- 壓縮：
  > [ jonny@linux ~ ]
  >
  > FileName.tar.gz DirName
- 解壓縮：
  > [ jonny@linux ~ ]
  >
  > FileName.tar.gz

### .bz

- 壓縮：unkown。
- 解壓縮 1：
  > [ jonny@linux ~ ]
  >
  > FileName.bz
- 解壓縮 2：
  > [ jonny@linux ~ ]
  >
  > FileName.bz

### .tar.bz

- 壓縮：unkown。
- 解壓縮：
  > [ jonny@linux ~ ]
  >
  > FileName.tar.bz

### .bz2

- 套件名稱：bzip2。
- 壓縮：
  > [ jonny@linux ~ ]
  >
  > FileName
- 解壓縮 1：
  > [ jonny@linux ~ ]
  >
  > FileName.bz2
- 解壓縮 2：
  > [ jonny@linux ~ ]
  >
  > FileName.bz2

### .tar.bz2

- 套件名稱：bzip2。
- 壓縮：
  > [ jonny@linux ~ ]
  >
  > FileName.tar.bz2 DirName
- 解壓縮：
  > [ jonny@linux ~ ]
  >
  > FileName.tar.bz2

### .tar.bz2 (parallel)

- 套件名稱：lbzip2。
- 壓縮：
  > [ jonny@linux ~ ]
  >
  > FileName.tar.bz2 DirName

### .xz

- 套件名稱：xz-utils。
- 壓縮：
  > [ jonny@linux ~ ]
  >
  > FileName
- 解壓縮：
  > [ jonny@linux ~ ]
  >
  > FileName.xz

### .tar.xz

- 套件名稱：xz-utils。
- 壓縮：
  > [ jonny@linux ~ ]
  >
  > FileName.tar.xz DirName
- 解壓縮：
  > [ jonny@linux ~ ]
  >
  > FileName.tar.xz

### .Z

- 壓縮：
  > [ jonny@linux ~ ]
  >
  > FileName
- 解壓縮：
  > [ jonny@linux ~ ]
  >
  > FileName.Z

### .tar.Z

- 壓縮：
  > [ jonny@linux ~ ]
  >
  > FileName.tar.Z DirName
- 解壓縮：
  > [ jonny@linux ~ ]
  >
  > FileName.tar.Z

### .tgz

- 套件名稱：gzip。
- 壓縮：
  > [ jonny@linux ~ ]
  >
  > FileName.tgz FileName
- 解壓縮：
  > [ jonny@linux ~ ]
  >
  > FileName.tgz

### .tar.tgz

- 套件名稱：gzip。
- 壓縮：
  > [ jonny@linux ~ ]
  >
  > FileName.tar.tgz FileName
- 解壓縮：
  > [ jonny@linux ~ ]
  >
  > FileName.tar.tgz

### .7z

- 套件名稱：p7zip-full。
- 壓縮：
  > [ jonny@linux ~ ]
  >
  > FileName.7z FileName
- 使用密碼 (PASSWORD) 壓縮：
  > [ jonny@linux ~ ]
  >
  > FileName.7z FileName
  >
  > PASSWORD
- 解壓縮：
  > [ jonny@linux ~ ]
  >
  > FileName.7z

### .zip

- 套件名稱：zip。
- 壓縮：
  > [ jonny@linux ~ ]
  >
  > FileName.zip DirName
- 解壓縮：
  > [ jonny@linux ~ ]
  >
  > FileName.zip

### .rar

- 套件名稱：rar, unrar。
- 壓縮：
  > [ jonny@linux ~ ]
  >
  > FileName.rar DirName
- 解壓縮 1：
  > [ jonny@linux ~ ]
  >
  > FileName.rar
- 解壓縮 2：
  > [ jonny@linux ~ ]
  >
  > FileName.rar
- 解壓縮 3：在指定目錄內解壓縮。
  > [ jonny@linux ~ ]
  >
  > FileName.rar DirName

### .lha

- 套件名稱：lha。
- 壓縮：
  > [ jonny@linux ~ ]
  >
  > FileName.lha FileName
- 解壓縮：
  > [ jonny@linux ~ ]
  >
  > FileName.lha

### .zst

- 套件名稱：zstd。
- 壓縮：
  > [ jonny@linux ~ ]
  >
  > FileName
- 解壓縮：
  > [ jonny@linux ~ ]
  >
  > FileName.zst

### .tar.zst

- 套件名稱：zstd。
- 壓縮：
  > [ jonny@linux ~ ]
  >
  > FileName.tar.zst DirName
  >
  > FileName.tar.zst File1 File2
- 解壓縮：
  > [ jonny@linux ~ ]
  >
  > FileName.tar.zst
  [GNU / Linux 各種壓縮與解壓縮指令](http://note.drx.tw/2008/04/command.html)

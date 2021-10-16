# GNU / Linux 各種壓縮與解壓縮指令

##### 目錄

| 目錄              |                       |                       |                               |
| ----------------- | --------------------- | --------------------- | ----------------------------- |
| [ar](#ar)         | [bunzip2](#bunzip2)   | [bzip2](#bzip2)       | [bzip2recover](#bzip2recover) |
| [gunzip](#gunzip) | [unarj](#unarj)       | [compress](#compress) | [cpio](#cpio)                 |
| [dump](#dump)     | [uuencode](#uuencode) | [gzexe](#gzexe)       | [gzip](#gzip)                 |
| [lha](#lha)       | [restore](#restore)   | [tar](#tar)           | [uudecode](#uudecode)         |
| [unzip](#unzip)   | [zip](#zip)           | [zipinfo](#zipinfo)   |                               |

---

<a id="ar">

### ar


---

<a id="bunzip2">

### bunzip2

---

<a id="bzip2">

### bzip2

---

<a id="bzip2recover">

### bzip2recover

---

<a id="gunzip">

### gunzip

---

<a id="unarj">

### unarj

---

<a id="compress">

### compress

---

<a id="cpio">

### cpio

---

<a id="dump">

### dump

---

<a id="uuencode">

### uuencode

---

<a id="gzexe">

### gzexe

---

<a id="gzip">

### gzip

---

<a id="lha">

### lha

---

<a id="restore">

### restore

---

<a id="tar">

### tar

- 套件名稱：tar。

#### 參數

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

#### 基本使用

- 打包：

```shell
tar cvf FileName.tar DirName
```

- 解包：

```shell
tar xvf FileName.tar
```

---

<a id="uudecode">

### uudecode

---

<a id="unzip">

### unzip

---

<a id="zip">

### zip

---

<a id="zipinfo">

### zipinfo

---




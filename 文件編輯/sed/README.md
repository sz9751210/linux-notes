# sed(stream editor)

- 用途：用於處理文件，字串取代、複製、刪除等功能，進行處理時並不會改變當前的檔案，而是將處理過程存放在[模式空間]的緩衝區，結束目前的指令後輸出，接著再處理下一個指令直到結束

## 語法

```shell
sed [OPTIONS] script or inputfile
```

## 參數(常用)

| 參數                             | 說明                                 |
| -------------------------------- | ------------------------------------ |
| -n, --quiet, --silent            | 沈默模式                             |
| -e script, --expression=script   | 直接在命令模式設定好script來進行編輯 |
| -f script檔案, --file=script檔案 | 使用指定的script檔案來進行編輯       |
| -i                               | 修改檔案，常用於自動化腳本           |

| 動作 | 說明                                                                               |
| ---- | ---------------------------------------------------------------------------------- |
| a    | 新增，在指定的行數的「下一行」插入字串。未指定行數的話則是在「每一行」之後插入字串 |
| c    | 取代，替換指定行數為預替換的字串                                                   |
| d    | 刪除，刪除指定的行。常與`-i`選項搭配，用來修改檔案時移除不需要的行                 |
| i    | 插入，與`a`相同，差別在於`a`指令是在指定行數之後插入，`i`是在指定行數之前插入      |
| p    | 列印，通常搭配`-n`選項做使用，只列印出受影響的行數                                 |
| s    | 取代，支持正則表達式，用來取代字串                                                 |


| flags | 說明                                                                                                      |
| ----- | --------------------------------------------------------------------------------------------------------- |
| [0-9]  | 數字表示只搜尋或者取代第 N 個數字所指示的那個樣板字串                                                     |
| g     | 全部取代                                                                                                  |
| I     | 忽略大小寫                                                                                                |
| w     | 把符合的結果寫入檔案。和加了 -n 選項搭配 p 旗標的結果一樣。此旗標如果有和其它旗標搭配使用，必須放在最後面 |
## 基本操作
### 參數
搭配文件sed.txt
```text
I have a pen, I have an apple
Ah
Apple pen
I have a pen, I have pineapple
Ah
Pineapple pen
Apple pen
Pineapple pen
Ah
Pen Pie Pineapple Apple Pen
Pen Pie Pineapple Apple Pen
```

1. 使用`-n`沈默模式
```shell
# 使用s取代每一行第一次出現的have修改成had
sed -n 's/have/had/1p' sed.txt
# 透過沈默模式修改文件，默認不會印出東西，需搭配p則會顯示有修改的行
```

2. 使用`-e`設定規則
```shell
# 把檔案中每行第一次出現的的pen換成pencil並存到sed_output.txt，-e為默認選項，可加可不加
sed -e 's/pen/pencil/' sed.txt > sed_output.txt

# 多條件方式，有-e不需要分號分隔，無-e則需要做分隔
sed -e 's/pen/pencil/' -e 's/have/had/' sed.txt
sed 's/pen/pencil/; s/have/had/' sed.txt
```

3. 使用`-f`指定script檔案進行修改

假設有個script檔案`sed_command.txt`如下
```shell
s/pen/pencil/
s/have/had/
```

```shell
# 將每一行第一次出現的pen以及have做替換
sed -f sed_command.txt sed.txt 
```

4.  使用`-i`直接修改檔案
```shell
sed -i 's/pen/pencil/' sed.txt
```
### 動作
1. 使用a新增字串
```shell
# 在第一行之後新增字串
sed '1a I have both' sed.txt

# 多行新增，在第一行到第四行這四行的後面都新增字串
sed '1,4a I have both' sed.txt
```
2. 使用c做字串替換
```shell
# 取代第二行，改為I have both
sed '2c I have both' sed.txt

# 多行取代，將1到5行壓縮為一行並改為字串
sed '1,5c I have both' sed.txt
```
3. 使用d進行刪除指定行或字串行
```shell
# 刪除第一行
sed 1d sed.txt

# 刪除一到五行
sed 1,5d sed.txt

# 刪除pen出現的行
sed '/pen/d' sed.txt
```

4. 使用i進行插入
```shell
# 在第一行之前插入字串
sed '1i I have both' sed.txt

# 在第一到第三行的每行之前插入字串
sed '1,3i I have both' sed.txt
```
5. 使用p進行列印出影響行，通常配合`-n`選項搭配使用
```
# 將have取代為had並列印出來
sed -n 's/have/had/1p' sed.txt
```

6. 使用s做字串取代

語法格式
```
s/regexp/replacement/[flags]
```

## 參考資料
* https://www.gnu.org/software/sed/manual/sed.html
* https://www.runoob.com/linux/linux-comm-sed.html
* https://iter01.com/458869.html
* https://terryl.in/zh/linux-sed-command/

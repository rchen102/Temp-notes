## File

参考
[codecademy Learn Python3](https://www.codecademy.com/learn/learn-python-3)



### File
使用`with`打开文件无需手动close文件


#### Read file
```py
# read all file content in a single string
with open('fileName.txt') as fn:
    fn_contents = fn.read()
print(fn_contents)

# read file in lines
with open('fileName.txt') as fn:
    for line in fn.readlines():
        print(line)

# read file line by line
with open('fileName.txt') as fn:
    first_line = fn.readline()
    second_line = fn.readline()
    # return "" if read to the end of file
```

#### Write file
```py
# write a file with write-mode
with open('fileName.txt', 'w') as fn:
    fn.write("What an incredible file!")
    # 'w'代表write mode, 'r'为默认的read-mode
    # 若fileName.txt已经存在，则会先清空文件内容再写

# write a file with append-mode
with open('fileName.txt', 'a') as fn:
    fn.write("What an incredible file!")
    # 'a'代表append-mode
    # 会在文件结尾处继续写入内容

# write a file with list of string
with open('fileName.txt', 'w') as fn:
    alist = ['first line\n', 'second_line']
    fn.writelines(alist)
    # 换行需要手动添加\n
```

### CSV File
CSV stands for Comma-Separated Values
CSV files are usually the way that data from spreadsheet software (like Microsoft Excel or Google Sheets) is exported into a portable format

#### Read CSV
```csv
Name,Username,Email Roger Smith,rsmith,wigginsryan@yahoo.com Michelle Beck,mlbeck,hcosta@hotmail.com Ashley Barker,a_bark_x,a_bark_x@turner.com Lynn Gonzales,goodmanjames,lynniegonz@hotmail.com
```

```py
# read csv with help of csv module
import csv

list_of_email_addresses = []
with open('users.csv', newline='') as users_csv:
    user_reader = csv.DictReader(users_csv)
    for row in user_reader:
        list_of_email_addresses.append(row['Email'])
    # DictReader 会将csv以字典形式读入，返回一个csv.DictReader Object
    # 除了csv第一行，其余每行都是一个字典(row)，字典的key为第一行的值
```
为什么使用`newline=''`: [python doc](https://docs.python.org/3/library/csv.html#id3)

实际上随着发展，CSV并不仅仅指由逗号作为分割符(delimiter)的文件，也包含了使用其他分割符的文件
```csv
Name;Address;Telephone Donna Smith;126 Orr Corner Suite 857\nEast Michael, LA 54411;906-918-6560 Aaron Osborn;6965 Miller Station Suite 485\nNorth Michelle, KS 64364;815.039.3661x42816 Jennifer Barnett;8749 Alicia Vista Apt. 288\nLake Victoriaberg, TN 51094;397-796-4842x451 Joshua Bryan;20116 Stephanie Stravenue\nWhitneytown, IA 87358;(380)074-6173 Andrea Jones;558 Melissa Keys Apt. 588\nNorth Teresahaven, WA 63411;+57(8)7795396386 Victor Williams;725 Gloria Views Suite 628\nEast Scott, IN 38095;768.708.3411x954
```

```py
import csv

with open('addresses.csv', newline='') as addresses_csv:
  address_reader = csv.DictReader(addresses_csv, delimiter=';')
  for row in address_reader:
    print(row['Address'])
```

#### Write CSV
```py
big_list = [{'name': 'Fredrick Stein', 'userid': 6712359021, 'is_admin': False}, {'name': 'Wiltmore Denis, 'userid': 2525942, 'is_admin': False}, {'name': 'Greely Plonk', 'userid': 15890235, 'is_admin': False}] 

import csv
with open('output.csv', 'w') as output_csv:
    fields = ['name', 'userid', 'is_admin']
    output_writer = csv.DictWriter(output_csv, fieldnames=fields)

    output_writer.writeheader()
    for item in big_list:
        output_writer.writerow(item)

```

### JSON File

#### Read
JSON stands for JavaScript Object Notation

```json
{
  'user': 'ellen_greg',
  'action': 'purchase',
  'item_id': '14781239',
}
```

#### Read JSON

```py
import json

with open('purchase_14781239.json') as purchase_json:
  purchase_data = json.load(purchase_json) # dict

print(purchase_data['user'])
# Prints 'ellen_greg'
```

#### Write JSON
```py
turn_to_json = {
  'eventId': 674189,
  'dateTime': '2015-02-12T09:23:17.511Z',
  'chocolate': 'Semi-sweet Dark',
  'isTomatoAFruit': True
}

import json

with open('output.json', 'w') as json_file:
  json.dump(turn_to_json, json_file)

```
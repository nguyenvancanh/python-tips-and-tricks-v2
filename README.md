# python-tips-and-tricks-v2

Trong bất kỳ ngôn ngữ lập trình nào, Nếu chúng ta nắm được càng nhiều tips & tricks trong người, thì việc code một chức năng, một ứng dụng với ngôn ngữ lập trình đó sẽ trở lên vô cùng đơn giản và nhanh chóng. Với nhưng tips & tricks đơn giản, nhưng đôi khi có thể giúp chúng ta thay thế được đoạn code vô cùng phức tạp. Đôi khi chúng ta có thể không cần dùng tới những vòng lặp cũng có thể giải quyết được vấn đề. Nói như vậy để mọi người đủ hiểu rằng, sức mạnh cũng như tầm quan trọng của các típ & tricks trong các ngôn ngữ lập trình. Khi mới học một ngôn ngữ lập trình nào mới mẻ, tôi khuyên mọi người ngoài việc tìm hiểu cách thức để code thì hãy nên giành thời gian để tìm hiểu về các tips & tricks của ngôn ngữ lập trình đó. Nó sẽ vô cùng hữu ích cho chính bản thân các bạn trong quá trình làm việc sau này. 

Tiếp nối seri về típs & tricks trong python, hôm nay tôi sẽ giới thiệu tới các bạn những tips và tricks tiếp theo

## 1. Đo lường thời gian thực hiện của một đoạn code

Việc đo đạc một dòng code, đoạn code, hay 1 function chạy hết trong bao lâu là vô cùng quan trọng. Với kết quả đo lường được sẽ quyết định tới hành động tiếp theo của mỗi chúng ta (có thể cần cải thiện performance, refactor lại code, ... ). Để làm được điều này thì ý tưởng vô cùng đơn giản, chúng ta chỉ cần đo thời gian từ start -> end của đoạn code mình muốn đo là xong. Trong python thì thực hiện như sau

```
import time

startTime = time.time()

# write your code or functions calls

endTime = time.time()
totalTime = endTime - startTime

print("Total time required to execute code is= ", totalTime)

```

Kết quả trả về cho chúng ta 2 nội dung : 

```
Executed in: Đơn vị đo lường là sec (s)
Memory: Đơn vị đo lường là kilobyte
```

# 2. Lấy ra các phần tử khác nhau của 2 mảng

Bài toán đặt ra là nếu bạn đang có 2 danh sách sau

```
list1 = ['Tao', 'Man', 'Le', 'Dao', 'Mit']
list2 = ['Tao', 'Le', 'Mit']

```

Bài toán đặt ra là bạn cần lấy ra những loại quả có trong danh sách 1 mà k có trong danh sách 2. Dễ thấy output của chúng ta cần có là list3 = [ 'Man', 'Dao']. Trong python, để tránh việc sử dụng vòng lặp và check. Chúng ta làm như sau

```
list1 = ['Scott', 'Eric', 'Kelly', 'Emma', 'Smith']
list2 = ['Scott', 'Eric', 'Kelly']

set1 = set(list1)
set2 = set(list2)

list3 = list(set1.symmetric_difference(set2))
print(list3)
```
 
# 3. Tính toán memory sẽ xử dụng cho một object

Khi chúng ta tiến hành code một function hay 1 đoạn code, tôi cũng khá chắc chắn rằng khi các bạn khai báo 1 biến, 1 mảng hay 1 object các bạn chưa quan tâm tới việc bộ nhớ sẽ tốn bao nhiêu để lưu trữ biến bạn vừa khai báo. Việc này đối với chúng ta có thể rất bình thường, nhưng đôi với những người lập trình viên chuyên nghiệp, họ thường xuyên kiểm tra xem việc khai báo biến của mình ảnh hưởng gì tới memory hay không ? Và thường xuyên sau khi dùng xong bất kỳ biến nào đó, họ sẽ giải phóng biến đó ra khỏi bộ nhớ. Trong python, để làm được điuề này thì các bạn làm như sau

```
import sys

list1 = ['Scott', 'Eric', 'Kelly', 'Emma', 'Smith']
print("size of list = ",sys.getsizeof(list1))

name = 'pynative.com'
print("size of name = ",sys.getsizeof(name))
```

Output của đoạn chương trình trên là

```
('size of list = ', 112)
('size of name = ', 49)
```

Có một lưu ý là hàm sys.getsizeof không trả về chính xác các object của bên thứ 3

# 4. Remove duplicate item in list

Có nhiều trường hợp chúng ta cần xóa hoặc tìm những phần tử trùng nhau trong danh sách. Hay xem python sẽ giải quyết bài toán này như thế nào nhé

```
listNumbers = [20, 22, 24, 26, 28, 28, 20, 30, 24]
print("Original= ", listNumbers)

listNumbers = list(set(listNumbers))
print("After removing duplicate= ", listNumbers)

```

Output của đoạn code trên là

```
'Original= ', [20, 22, 24, 26, 28, 28, 20, 30, 24]
'After removing duplicate= ', [20, 22, 24, 26, 28, 30]
```

# 5. Kiểm tra nếu tất các các phần tử trong danh sách đều bằng nhau

Ý tưởng của việc kiểm tra này là chúng ta sẽ lấy phần tử đầu tiên trong danh sách, rồi lặp lại từ đầu tới cuối dánh sách, kiểm tra các phần tử vs phần tử đầu tiên, nếu bằng nhau hoàn toàn thì trả về true, nếu không thì trả về false. Với python việc này sẽ đơn giản hơn nhiều. Chỉ cần gọi hàm count(phần tử đầu tiên) là mọi việc được giải quyết. 

```
listOne = [20, 20, 20, 20]
print("All element are duplicate in listOne", listOne.count(listOne[0]) == len(listOne))

listTwo = [20, 20, 20, 50]
print("All element are duplicate in listTwo", listTwo.count(listTwo[0]) == len(listTwo))
```

Output của đoạn code trên là

```
'All element are duplicate in listOne', True
'All element are duplicate in listTwo', False

```

# 6. So sách 2 danh sách chưa được sắp xếp

Bài toán đặt ra là bạn có 2 danh sách, giá trị các phần tử trong từng danh sách thì giống hệt nhau, nhưng thứ tự của các phần tử này đang khác nhau

```
one = [33, 22, 11, 44, 55]
two = [22, 11, 44, 55, 33]
```
Hãy xem python sẽ làm thế nào để compare 2 mảng này có bằng nhau hay không nhé

- Với danh sách chưa được săp xếp : collections.Counter
- Với danh sách đã được sắp xếp : sorted()

```
from collections import Counter

one = [33, 22, 11, 44, 55]
two = [22, 11, 44, 55, 33]

print("is two list are b equal", Counter(one) == Counter(two))
```

Output thu được 

``` 
'is two list areb equal', True
```

# 7. Check tất cả phần tử trong danh sách tồn tại duy nhất

Đoạn code sau đây sẽ giúp bạn check được tất cả các phàn tử trong danh sách có phải là duy nhất hay không

```
def isUnique(item):
    tempSet = set()
    return not any(i in tempSet or tempSet.add(i) for i in item)

listOne = [123, 345, 456, 23, 567]
print("All List elemtnts are Unique ", isUnique(listOne))

listTwo = [123, 345, 567, 23, 567]
print("All List elemtnts are Unique ", isUnique(listTwo))
```
Output thu được là

```
All List elemtnts are Unique  True
All List elemtnts are Unique  False
```

# 8. Convert Byte sang string

Cách đơn giản nhất là chúng ta chỉ cần decode by sang charset mình mong muốn

```
byteVar = b"pynative"
str = str(byteVar.decode("utf-8"))
print("Byte to string is" , str )
```

Output

```
Byte to string is pynative
```

# 9.Merge 2 object băng một biểu thức duy nhất

Bây giờ, nếu bạn có 2 object như sau

```
currentEmployee = {1: 'Scott', 2: "Eric", 3:"Kelly"}
formerEmployee  = {2: 'Eric', 4: "Emma"}
```

Bạn đang mong muốn là sẽ merged chúng thành 1, hãy xem python xử lý thế nào nhé. 

```
// Python 3.5
currentEmployee = {1: 'Scott', 2: "Eric", 3:"Kelly"}
formerEmployee  = {2: 'Eric', 4: "Emma"}

allEmployee = {**currentEmployee, **formerEmployee}
print(allEmployee)
```

```
Python 3.4 & 2

currentEmployee = {1: 'Scott', 2: "Eric", 3:"Kelly"}
formerEmployee  = {2: 'Eric', 4: "Emma"}

def merge_dicts(dictOne, dictTwo):
    dictThree = dictOne.copy()
    dictThree.update(dictTwo)
    return dictThree
    
print(merge_dicts(currentEmployee, formerEmployee))
```

# 10. Convert 2 danh sách vào 1 dictionary

Bây giờ, nếu bạn có 2 danh sách, trong đó, 1 danh sách chứa key, danh sách còn lại chưa value. Bạn muốn đưa nó về thành 1 dictionary dạng key : value, hãy xem python làm điều này thế nào nhé

```
ItemId = [54, 65, 76]
names = ["Hard Disk", "Laptop", "RAM"]

itemDictionary = dict(zip(ItemId, names))

print(itemDictionary)
```

# 11. Format number type float

Nếu bạn luôn muốn số dạng float của mình được format hiển thị dưới dạng 2 số sau dấu , thì sẽ làm như sau

```
number= 88.2345
print('{0:.2f}'.format(number))
```

# 12. Một function trả về nhiều gía trị

```
def multiplication_Division(num1, num2):
  return num1*num2, num2/num1

product, division = multiplication_Division(10, 20)
print("Product", product, "Division", division)
```

# 14. Check value tồn tại trong array

Bạn chỉ cần nhớ tới package numpy

```
import numpy

arraySample = numpy.array([[1, 2], [3, 4], [4, 6], [7, 8]])

if value in arraySample[:, col_num]:
    print(value)
```

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

#3. Tính toán memory sẽ xử dụng cho một object




Date: 00:44 2021-04-08

# The Life of a SystemVerilog Variable

### Reviewer: #Alexander

### Tags: #Basics #SV #Variables

### Rates - 25
- Usefulness - 8 на сколько идея может быть полезна в использовании
- Applicability - 9 на сколько идея применима
- Innovativeness - 1 на сколько идея нова
- Availability - 7 на сколько идея доступно и понятно изложена

### Reasons to read
Было несколько случаев, когда значение после инициализации не совпадало с ожидаемым. Инициализация и присваивание переменной в конструкторе.

### Abstract
The life of a SystemVerilog variable may seem like a mundane topic, but there are nuances that get overlooked leading to issues that are difficult to debug. Some of the most common issues are how and when variables get initialized, how concurrent threads interact with the same variable, and how certain variable lifetimes interact with other SystemVerilog features in terms of performance considerations. This paper presents a background on the

В статье описывается время жизни переменных для разных скоупов. Когда именно они инициализируются. Static, automatic. Как влияет время жизни на различные свойства SV.


### Main
-   Есть 3 различных типа name space (module, block, compilation-unit)   
-   Static initialization order fiasco. Нельзя узнать порядок инициализации статических переменных, так как они все инициализируются на стадии элаборации
-   Методы в модулях по дефолту статические и переменных в них тоже
-   Форки не начинаются до того момента, пока родительский процесс не закончился или не приостановился. Поэтому нужно использовать automatic в лупе

### Summary
Нового откровенно мало, но стоит прочитать, чтобы освежить в памяти какие есть особенности при использовании переменных. На причину чтения, статья, ответа не дала:(

### Article References
1. 
"IEEE Standard for SystemVerilog--Unified Hardware Design, Specification, and Verification Language," in
IEEE Std 1800-2017 (Revision of IEEE Std 1800-2012) , 22 Feb. 2018, doi: 10.1109/IEEESTD.2018.8299595.
2. "IEEE Standard Verilog Hardware Description Language," in IEEE Std 1364-2001, 28 Sept. 2001, doi:
10.1109/IEEESTD.2001.93352.
3. 
“Why is Java Knows as a Safe Language”, Armin Zirak, 16 Nov. 2018,
https://medium.com/@armin.zirak97/why-is-java-known-as-a-safe-language-be7a9cc42707
4. 
“The Go Programming Language Specification”, Google, Retrieved 11 Dec 2020, https://golang.org/ref/spec
5. 
“What is the static initialization order fiasco?”, Marshal Cline, 4 Jul 2012,

### Other LInks
[edaplayground](https://www.edaplayground.com/x/jGF3)
### Article
![[The Life of a SystemVerilog Variable.pdf]]
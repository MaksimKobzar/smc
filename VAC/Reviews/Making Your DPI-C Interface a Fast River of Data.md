Date: 13:41 2021-04-08

# Making Your DPI-C Interface a Fast River of Data

### Reviewer: #Alexander 

### Tags: #TAG0 #TAG-1

### Rates - 23
- Usefulness - 7 на сколько идея может быть полезна в использовании
- Applicability - 8 на сколько идея применима
- Innovativeness - 1 на сколько идея нова
- Availability - 7 на сколько идея доступно и понятно изложена

### Abstract
Abstract-SystemVerilog DPI-C enables functional verification teams to leverage C  for modeling, checking and utility functions. The simple "C" style call interface allows fast adoption and easy integration. This paper explains the workings of the integration and provides data type mapping examples and some hints on optimizing the calls for maximum performance

### Reasons to read
Много приходилось работать с си кодом и не было понимания, что за типы данных передаются в си функции в качестве аргументов.

### Main
-   Существует файл *svdpi.h* Для каждого тула свой. Этот файл содержит различные типы данных, которыми могут обмениваться sv и c. Пример: */sw/Tools\_Eval/Synopsys/VCS-MX/VCS-MX2018.09-SP2-3/include/svdpi.h*
-   Как и в sv можно передавать аргументы копируя их или по ссылке, но в случае несовпадения поддерживаемых типов все равно произойдет копирование. (например при передаче вектора (bit ~ svBit))
-   Для передачи типа logic в c используется тип данных svLogic который является uint8\_t. То есть одноразрядный logic будет преобразован как 8 битный вектор.
-   Чтобы распечатать logic из c он преобразуется в char.
-   Можно передавать структуры в качестве аргумента, но для этого нужно также затайпдефить структуру в c.
-   Можно поместить time consuming sv task в с task. Следует использовать automatic tasks.
-   DPI-C call перформанс сравним с C call перформансом
-   Для оптимизации: *sv input -> const int \*i*

### Article References
1.  SystemVerilog LRM, “1800-2017 - IEEE Standard for SystemVerilog--Unified Hardware Design, Specification, and Verification Language”, https://ieeexplore.ieee.org/document/8299595
2.  Using SystemVerilog Now With DPI, DVCON 2005, Rich Edelman

### Other LInks
[edaplayground](https://www.edaplayground.com/x/8wmF)

### Article
![[Making Your DPI-C Interface a Fast River of Data.pdf]]
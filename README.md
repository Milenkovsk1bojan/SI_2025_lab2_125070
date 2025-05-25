# SI_2025_lab2_125070
Laboratoriska Zadaca 2 po Softversko Inzenerstvo 
Име:  Бојан
Презиме:  Миленковски
Индекс:  125070

Барање:1
Кодот е преземен.



Барање:2
Pishan sistem na CFG:
     [1] Почеток
       |
     [2] if (allItems == null) → true → [X] throw
       | false
     [3] sum = 0
       |
     [4] for (i < allItems.size())
       |
     [5] if (item name null/empty) → true → [X] throw
       | false
     [6] if (price > 300 || discount > 0 || quantity > 10)
       | true → [7] sum -= 30
       | false → skip
     [8] if (discount > 0)
       | true → [9] sum += price * (1 - discount) * quantity
       | false → [10] sum += price * quantity
     → next item in loop (back to [4])
       ↓
     [11] if (cardNumber != null && length == 16) → false → [X] throw
       | true
     [12] for (char in cardNumber)
       |
     [13] if (char not in digits) → true → [X] throw
       | false → continue
       ↓
     [14] return sum
     [15] Крај



Барање:3
Cyclomatic Complexity (Цикломатска комплексност)

Формула:
M=E−N+2PM=E−N+2P
M: Cyclomatic complexity
E: Number of edges (стрелки)
N: Number of nodes (јазли)
P: Number of connected components (обично 1 за една функција)

Броење по логички услови (едноставно правило):
Секојa if, for, while, &&, || услов додава една точка.

Во checkCart имам:

    if (allItems == null)
    for (i < allItems.size())
    if (item.getName() == null || item.getName().length() == 0) → 1 услов + 1 логичка OR → +2
    if (item.getPrice() > 300 || item.getDiscount() > 0 || item.getQuantity() > 10) → +3
    if (item.getDiscount() > 0)
    if (cardNumber != null && cardNumber.length() == 16) → 1 услов + 1 логичка AND → +2
    for (char c in cardNumber)
    if (allowed.indexOf(c) == -1)

Вкупно, тотал:

    Условни изрази = 11
    Цикломатска комплексност = M = 11 + 1 = 12
**ОДГОВОР имаме 12.**
    
Барање:4 Every Statement Criterion
    Мислам дека условот беше да се направи секоја наредба, барем еднаш.
    Минимален број на тест случаи:
    Тестови за да се покријат сите if, else, и for патишта најмалку 3 тест случаи:
TestCase1: Happy Path
List<Item> items = List.of(new Item("Apple", 1, 100, 0.0));
String cardNumber = "1234567890123456";

TestCase2: Invalid item name
List<Item> items = List.of(new Item("", 1, 100, 0.0));
String cardNumber = "1234567890123456";

TestCase3: Discount active + - 30 rule
List<Item> items = List.of(new Item("Milk", 2, 500, 0.1));
String cardNumber = "1234567890123456";



Барање:5 Multiple Condition Criterion
Мислам дека ова беше на секоја наредба/услови(statement) да има барем 3 под услови
Пример:
    if (item.getPrice() > 300 || item.getDiscount() > 0 || item.getQuantity() > 10)
Имаме 3 под-услови → минимално 2^3 = 8 комбинации.
Price > 300	Discount > 0	Quantity > 10	Expected outcome
false	false	false	No -30
true	false	false	Yes -30
false	true	false	Yes -30
false	false	true	Yes -30
true	true	false	Yes -30
true	false	true	Yes -30
false	true	true	Yes -30
true	true	true	Yes -30
ОДГОВОР: 8


Барање:6

Барање:7
Барање:3

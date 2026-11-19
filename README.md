# Dart OOP Assignment: Kigali Bus Card
**Name:** ISAMELDIN MOHAMED OSMAN ELYAS
**Student ID:** 25298/2024

## My numbers
- **D =** 98 **L =** 8
- **Starting balance =** 1980 RWF
- **Bus fare =** 298 RWF
- **Student discount =** 18%

## Output of main.dart
    Error: name too short
    Owner: ISAMELDIN | Balance: 1980 RWF
    Owner: ISAMELDIN MOHAMED OSMAN ELYAS | Balance: 1980 RWF
    Error: top-up must be 500 to 50000 RWF
    Topped up 2000 RWF
    Paid 298 RWF
    Paid 298 RWF
    Owner: ISAMELDIN MOHAMED OSMAN ELYAS | Balance: 3384 RWF
    Student discount: 53 RWF
    Paid 245 RWF
    Owner: ISAMELDIN MOHAMED OSMAN ELYAS | Balance: 1735 RWF
    Student card: 18% off

## Part 1: Why no setter for balance?
Because if there were a public setter for `_balance`, anyone could directly change the balance to any arbitrary amount (e.g., `card.balance = 999999`) without actually paying or following validation rules. By keeping `_balance` private and only allowing changes through `topUp()` and `pay()`, we protect the data and enforce business rules (like top-up limits and checking for sufficient funds).

## Part 2: What does ~/ do?
The `~/` operator performs integer division (truncating division). It divides two numbers and discards any decimal remainder to return an `int`.

- `237 * 17 / 100` uses standard division and returns `40.29` (a `double`).
- `237 * 17 ~/ 100` uses integer division and returns `40` (an `int`), dropping `.29` so the result can be stored in an `int` variable.

## Part 4: Bug table

| Bug | The line | Why it is wrong (your words) | Your fix |
| :--- | :--- | :--- | :--- |
| **1** | `String _brand;` and `int _battery;` | Non-nullable fields must be initialized with a starting value when declared (just like in `BusCard`), otherwise Dart throws a null-safety error. | Initialize them to `String _brand = '';` and `int _battery = 0;`. |
| **2** | `String system = '';` and `_system = system;` | The field was declared as `system` instead of `_system`, so `_system` does not exist when assigned in the constructor. | Rename the field declaration to `String _system = '';`. |
| **3** | `SmartPhone (String brand, int battery, String system) {` | `SmartPhone` inherits from `Phone`, which requires `brand` and `battery` to be passed to its constructor via `super`. | Add `: super(brand, battery)` to the `SmartPhone` constructor header. |
| **4** | `@override` above `void restart()` | `@override` can only be used if the parent class (`Phone`) already defines a `restart()` method, which it does not. | Remove the `@override` annotation above `void restart()`. |
| **5** | `p.battery = 100;` and `print(p.battery());` | `Phone` has no `battery` setter so `p.battery = 100;` fails, and `battery` is a getter (accessed like a property, not called like a function with `()`). | Add `set battery(int value)` (accepting 0 to 100) in `Phone`, and change `print(p.battery());` to `print(p.battery);`. |
| **Not a bug** | `Phone p = new Phone ('Tecno', 50);` | Why is this line fine? Using the `new` keyword when creating an object is optional in Dart, not an error—it still works normally. | (none) |

## Part 5
**My prediction:**
-5
-2

**Real output:**
    1
    5

**Was I right?**
No, my prediction was incorrect. For `Bag a`, `a.add()` sets `_items` to `1`, and `a.items = -5` is ignored because the setter only allows values `>= 0`, so it prints `1`. For `BigBag b`, calling `b.add()` twice calls `super.add()` four times (`_items` becomes `4`), and `b.items = b.items + 1` makes it `5`.
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

* `237 * 17 / 100` uses standard division and returns `40.29` (a `double`).
* `237 * 17 ~/ 100` uses integer division and returns `40` (an `int`), dropping `.29` so the result can be stored in an `int` variable.

## Part 4: Bug table

## Part 5
My prediction:
Real output:
Was I right?
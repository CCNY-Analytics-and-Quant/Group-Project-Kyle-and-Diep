```python
#homework 1.2
```


```python
import pandas as pd
```


```python
#inputs and variables

current_age = int(input(" What is your age? "))

retire_age = 67

rate_of_return = float(input("What was the average S&P 500 return rate in the last 10 years?"))

promo_raise = float(input("What is your expected annual raise?"))

annual_contrib = 20500

inflation = 0.02

annual_match = float(input("What is your 401k matching rate?"))
```

     What is your age?  22
    What was the average S&P 500 return rate in the last 10 years? 0.10
    What is your expected annual raise? 0.05
    What is your 401k matching rate? 0.035



```python
#number of biweekly periods

biweekly_count = 365/14
print(biweekly_count)
```

    26.071428571428573



```python
#annual raise to biweekly rate

biweekly_rate = ((1 + promo_raise) ** (1 / biweekly_count)) - 1
print(biweekly_rate)
```

    0.0018731557256548292



```python
#annual contribution to biweekly contribution

biweekly_contrib = annual_contrib / biweekly_count
print(biweekly_contrib)
```

    786.3013698630136



```python
#401k matching

biweekly_matching = (annual_contrib * annual_match) / biweekly_count
print(biweekly_matching)
```

    27.520547945205482



```python
#years until retirement

years_to_retire = retire_age - current_age
print(years_to_retire)
```

    45



```python
#checks to recieve

num_of_checks = round(years_to_retire * biweekly_count)
print(num_of_checks)
```

    1173



```python
balance = 0

for num_of_checks in range(1, num_of_checks + 1):
    balance += biweekly_contrib
    balance +=(biweekly_rate + 1)
    balance += biweekly_matching
    balance += (inflation + 1)
    
print(num_of_checks, round(balance, 2))
```

    1173 956984.77


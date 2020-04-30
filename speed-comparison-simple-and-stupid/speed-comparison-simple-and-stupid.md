

# Speed table

Lang/Implementation | Time taken to execute our stupid program (s)
-------------------- | --------------------------------------------
nodejs | 1.188
php | 3.399
PyPy (Python) | 10.590
CPython (Python) | 69.188


# Our stupid program:

```nodejs tab="NodeJS"
function randomIntFromInterval(min, max) { // min and max included 
  return Math.floor(Math.random() * (max - min + 1) + min);
}
let i = 0;
while(i<123456789){
    i + randomIntFromInterval(0, 2);
    i++;
}
```


```php tab="PHP"
$i = 0;
while($i<123456789){
    $i + rand(0, 2);
    $i++;
}
echo $i;
```


```python tab="PyPy (Python)"
import random

i = 0
while i < 123456789:
    i + random.randrange(0, 3)
    i = i + 1
print(i)
```


```python tab="CPython (Python)"
import random

i = 0
while i < 123456789:
    i + random.randrange(0, 3)
    i = i + 1
print(i)
```

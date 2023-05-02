
# Row Major

```python
rows = 4
cols = 5

for i in range(rows):
    for j in range(cols):
        index = i * cols + j
        print(index)
    print()
```


# Column Major

```python
rows = 4
cols = 5

for i in range(cols):
    for j in range(rows):
        index = j * cols + i
        print(index)
    print()
```
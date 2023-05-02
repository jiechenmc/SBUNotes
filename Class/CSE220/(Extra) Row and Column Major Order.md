
# Row Major

```python
rows = 4
cols = 4

for i in range(rows):
    for j in range(cols):
        index = i * cols + j
        print(index)
    print()
```


# Column Major

```python
rows = 3
cols = 10

for i in range(rows):
    for j in range(cols):
        index = j * rows + i
        print(index)
    print()
```
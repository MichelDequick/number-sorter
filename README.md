# Number Sorter

This short python script reads a given file containing numbers, sorts the numbers and writes them to a file of your choosing.

## Getting Started
Clone the script in a python enviroment:
  ```
  git clone https://github.com/MichelDequick/number-sorter.git
  ```

## Using the script
```
python number_sorter.py file_in 
                        [file_out] 
                        [-h] 
                        [-d DELIMITER] 
                        [-o {ascending,descending}]
                        [-s {bubble,insertion,selection}]
                    
```


positional arguments:
```
file_in               file containing unsorted numbers
file_out              file to write sorted number to (optional)
```

optional arguments:
```
-h, --help            show this help message and exit

-d, --delimiter DELIMITER
                        specify what delimiter to use (default: '/n')

-o, --order {ascending,descending}
                        specify how numbers should be ordered (default: ascending)

-s, --sorting-algorithm {bubble,insertion,selection}
                        specify what sorting algorithm to use (default: selection)
```

## Examples
Our example file, `example.txt` contains the following:
```
6, 9, 3, 4, 1, 7, 2, 5, 8
```
Running following command will sort our example file in descending order using the selection sort algorithm.
```
python number_sorter.py example.txt sorted_examples.txt -d ', ' -o descending -s selection
```
The resulting `sorted_examples.txt` will contain the following:
```
9, 8, 7, 6, 5, 4, 3, 2, 1
```




## Inner workings

### Bubble sort 
![](https://upload.wikimedia.org/wikipedia/commons/c/c8/Bubble-sort-example-300px.gif)
[Source](https://en.wikipedia.org/wiki/Bubble_sort)

```python
def sort_bubble(numbers):
  for sorted in reversed(range(len(numbers[1:]))):
      for index in range(len(numbers[:sorted])):
          if numbers[index] > numbers[index + 1]:
            numbers[index], numbers[index + 1] = numbers[index + 1], numbers[index]
  return numbers
```



### Selecton sort
![](https://upload.wikimedia.org/wikipedia/commons/9/94/Selection-Sort-Animation.gif)
[Source](https://en.wikipedia.org/wiki/Selection_sort)

```python
def sort_selection(numbers):
  for index in range(len(numbers)):
        index_min = index + numbers[index:].index(min(numbers[index:]))
        numbers[index], numbers[index_min] = numbers[index_min], numbers[index]
  return numbers
```


### Insertion sort
![](https://upload.wikimedia.org/wikipedia/commons/0/0f/Insertion-sort-example-300px.gif)
[Source](https://en.wikipedia.org/wiki/Insertion_sort)

```python
def sort_insertion(numbers):
  for index in range(1, len(numbers)):
    for i in reversed(range(index)):
      if numbers[index] < numbers[i]:
        numbers[index], numbers[i] = numbers[i], numbers[index]
      else: break
  return numbers
```



## Authors

* **Michel Dequick** - [GitHub](https://github.com/MichelDequick), [LinkedIn](https://www.linkedin.com/in/michel-dequick-839927144/)

See also the list of [contributors](https://github.com/MichelDequick/number-sorter/contributors) who participated in this project.

## License

This project is licensed under the Apache 2.0 License - see the [LICENSE](LICENSE) file for details



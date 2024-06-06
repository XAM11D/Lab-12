# Lab-12
Лабораторна робота 12: Робота з матрицями у Python

Мета роботи:
Мета цієї лабораторної роботи - навчитися працювати з матрицями у Python та виконувати над ними різноманітні операції. Завдання включають створення класу для роботи з матрицями, додавання елементів, обчислення суми рядків, транспонування, множення, перевірку на симетрію, поворот на 90 градусів вправо, згортку в одновимірний масив, створення матриці з списку списків та отримання діагоналі. Очікувані результати включають написання та тестування методів, що виконують ці завдання.

Опис завдання:
Реалізувати клас Matrix.
Написати методи для наступних операцій:
Додавання елементів до матриці.
Обчислення суми рядків.
Транспонування матриці.
Множення двох матриць.
Перевірка симетричності матриці.
Поворот матриці на 90 градусів вправо.
Згортка матриці в одновимірний масив.
Створення матриці з списку списків.
Отримання діагоналі матриці.

Виконання роботи:

Завдання 1: Реалізувати клас Matrix
class Matrix:
    def __init__(self, rows, columns):
        self.rows = rows
        self.columns = columns
        self.data = [[0] * columns for _ in range(rows)]

    def add_element(self, row, column, value):
        self.data[row][column] = value
Приклад використання:
matrix1 = Matrix(3, 3)
matrix1.add_element(0, 0, 5)
print(matrix1.data)  # Виведе: [[5, 0, 0], [0, 0, 0], [0, 0, 0]]

Завдання 2: Обчислення суми рядків
def sum_of_rows(self):
    return [sum(row) for row in self.data]
    
Приклад використання:
matrix1 = Matrix(3, 3)
matrix1.add_element(0, 0, 5)
print(matrix1.sum_of_rows())  # Виведе: [5, 0, 0]

Завдання 3: Транспонування матриці
def transpose(self):
    transposed_data = [[self.data[j][i] for j in range(self.rows)] for i in range(self.columns)]
    transposed_matrix = Matrix(self.columns, self.rows)
    transposed_matrix.data = transposed_data
    return transposed_matrix
    
Приклад використання:
matrix1 = Matrix(2, 3)
matrix1.add_element(0, 0, 1)
matrix1.add_element(0, 1, 2)
matrix1.add_element(0, 2, 3)
matrix1.add_element(1, 0, 4)
matrix1.add_element(1, 1, 5)
matrix1.add_element(1, 2, 6)
transposed = matrix1.transpose()
print(transposed.data)  # Виведе: [[1, 4], [2, 5], [3, 6]]

Завдання 4: Множення двох матриць
def multiply_by(self, other):
    if self.columns != other.rows:
        raise ValueError("Number of columns in the first matrix must be equal to the number of rows in the second matrix.")

    result = Matrix(self.rows, other.columns)

    for i in range(self.rows):
        for j in range(other.columns):
            for k in range(self.columns):
                result.data[i][j] += self.data[i][k] * other.data[k][j]

    return result
    
Приклад використання:
matrix1 = Matrix(2, 3)
matrix1.add_element(0, 0, 1)
matrix1.add_element(0, 1, 2)
matrix1.add_element(0, 2, 3)
matrix1.add_element(1, 0, 4)
matrix1.add_element(1, 1, 5)
matrix1.add_element(1, 2, 6)

matrix2 = Matrix(3, 2)
matrix2.add_element(0, 0, 7)
matrix2.add_element(0, 1, 8)
matrix2.add_element(1, 0, 9)
matrix2.add_element(1, 1, 10)
matrix2.add_element(2, 0, 11)
matrix2.add_element(2, 1, 12)

product = matrix1.multiply_by(matrix2)
print(product.data)  # Виведе: [[58, 64], [139, 154]]

Завдання 5: Перевірка симетричності матриці
def is_symmetric(self):
    return self.data == self.transpose().data
    
Приклад використання:
matrix1 = Matrix(3, 3)
matrix1.add_element(0, 0, 1)
matrix1.add_element(0, 1, 2)
matrix1.add_element(0, 2, 3)
matrix1.add_element(1, 0, 2)
matrix1.add_element(1, 1, 4)
matrix1.add_element(1, 2, 5)
matrix1.add_element(2, 0, 3)
matrix1.add_element(2, 1, 5)
matrix1.add_element(2, 2, 6)

print(matrix1.is_symmetric())  # Виведе: True

Завдання 6: Поворот матриці на 90 градусів вправо
def rotate_right(self):
    self.data = [[self.data[i][j] for i in range(self.rows - 1, -1, -1)] for j in range(self.columns)]
    
Приклад використання:
matrix1 = Matrix(2, 3)
matrix1.add_element(0, 0, 1)
matrix1.add_element(0, 1, 2)
matrix1.add_element(0, 2, 3)
matrix1.add_element(1, 0, 4)
matrix1.add_element(1, 1, 5)
matrix1.add_element(1, 2, 6)

matrix1.rotate_right()
print(matrix1.data)  # Виведе: [[4, 1], [5, 2], [6, 3]]

Завдання 7: Згортка матриці в одновимірний масив
def flatten(self):
    return [element for row in self.data for element in row]
    
Приклад використання:
matrix1 = Matrix(2, 2)
matrix1.add_element(0, 0, 1)
matrix1.add_element(0, 1, 2)
matrix1.add_element(1, 0, 3)
matrix1.add_element(1, 1, 4)

print(matrix1.flatten())  # Виведе: [1, 2, 3, 4]

Завдання 8: Створення матриці з списку списків
@staticmethod
def from_list(list_of_lists):
    rows = len(list_of_lists)
    columns = len(list_of_lists[0])
    matrix = Matrix(rows, columns)
    for i in range(rows):
        for j in range(columns):
            matrix.data[i][j] = list_of_lists[i][j]
    return matrix
    
Приклад використання:
list_of_lists = [[1, 2, 3], [4, 5, 6]]
matrix = Matrix.from_list(list_of_lists)
print(matrix.data)  # Виведе: [[1, 2, 3], [4, 5, 6]]

Завдання 9: Отримання діагоналі матриці
def diagonal(self):
    if self.rows != self.columns:
        raise ValueError("Matrix must be square to extract the diagonal.")

    return [self.data[i][i] for i in range(self.rows)]
    
Приклад використання:
matrix1 = Matrix(3, 3)
matrix1.add_element(0, 0, 1)
matrix1.add_element(0, 1, 2)
matrix1.add_element(0, 2, 3)
matrix1.add_element(1, 0, 4)
matrix1.add_element(1, 1, 5)
matrix1.add_element(1, 2, 6)
matrix1.add_element(2, 0, 7)
matrix1.add_element(2, 1, 8)
matrix1.add_element(2, 2, 9)
print(matrix1.diagonal())  # Виведе: [1, 5, 9]

Приклади виводу програм:

Додавання елементів до матриці:
[[5, 0, 0], [0, 0, 0], [0, 0, 0]]
Обчислення суми рядків:
[5, 0, 0]
Транспонування матриці:
[[1, 4], [2, 5], [3, 6]]
Множення двох матриць:
[[58, 64], [139, 154]]
Перевірка симетричності матриці:
True
Поворот матриці на 90 градусів вправо:
[[4, 1], [5, 2], [6, 3]]
Згортка матриці в одновимірний масив:
[1, 2, 3, 4]
Створення матриці з списку списків:
[[1, 2, 3], [4, 5, 6]]
Отримання діагоналі матриці:
[1, 5, 9]

Переконайтеся, що у вас встановлений Python 3.x.

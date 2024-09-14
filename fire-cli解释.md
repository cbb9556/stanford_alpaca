`fire`是一个用于自动生成命令行界面（CLI）的 Python 库。它可以根据函数的参数自动生成命令行参数，并将命令行参数解析为函数参数，从而方便地创建命令行工具。

以下是`fire`的基本用法：

1. 安装`fire`库：

   ```
   pip install fire
   ```

2. 基本示例：

   创建一个名为`example.py`的文件，内容如下：

   ```python
   import fire

   def add_numbers(x, y):
       return x + y

   def multiply_numbers(x, y):
       return x * y

   if __name__ == '__main__':
       fire.Fire()
   ```

   在命令行中运行以下命令：

   ```
   python example.py add_numbers 3 4
   ```

   输出：`7`

   ```
   python example.py multiply_numbers 3 4
   ```

   输出：`12`

3. 使用对象和方法：

   创建一个名为`example2.py`的文件，内容如下：

   ```python
   import fire

   class Calculator:
       def add(self, x, y):
           return x + y

       def multiply(self, x, y):
           return x * y

   if __name__ == '__main__':
       fire.Fire(Calculator)
   ```

   在命令行中运行以下命令：

   ```
   python example2.py add 3 4
   ```

   输出：`7`

   ```
   python example2.py multiply 3 4
   ```

   输出：`12`

4. 命令行参数和选项：

   创建一个名为`example3.py`的文件，内容如下：

   ```python
   import fire

   def greet(name, greeting='Hello'):
       return f'{greeting}, {name}!'

   if __name__ == '__main__':
       fire.Fire()
   ```

   在命令行中运行以下命令：

   ```
   python example3.py greet John --greeting Hi
   ```

   输出：`Hi, John!`

5. 嵌套命令：

   创建一个名为`example4.py`的文件，内容如下：

   ```python
   import fire

   class Math:
       def add(self, x, y):
           return x + y

       def multiply(self, x, y):
           return x * y

   class Greeting:
       def say(self, greeting='Hello'):
           return greeting

   def main():
       return {
           'math': Math(),
           'greeting': Greeting()
       }

   if __name__ == '__main__':
       fire.Fire(main)
   ```

   在命令行中运行以下命令：

   ```
   python example4.py math add 3 4
   ```

   输出：`7`

   ```
   python example4.py greeting say --greeting Hi
   ```

   输出：`Hi`

通过以上示例，可以看出`fire`库能够快速、方便地创建命令行工具，并且具有很高的灵活性。可以根据具体需求自定义命令行参数和选项，以及使用对象和方法、嵌套命令等功能。
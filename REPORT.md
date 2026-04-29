## Lab03 Анисимов Иван

Представьте, что вы стажер в компании "Formatter Inc.".
### Задание 1
Вам поручили перейти на систему автоматизированной сборки **CMake**.
Исходные файлы находятся в директории [formatter_lib](formatter_lib).
В этой директории находятся файлы для статической библиотеки *formatter*.
Создайте `CMakeList.txt` в директории [formatter_lib](formatter_lib),
с помощью которого можно будет собирать статическую библиотеку *formatter*.  
[CMakeLists для formatter](https://gist.github.com/OpasnyPingvin/674c007663f98cae09dcf1c4c6ecb26c)

### Задание 2
У компании "Formatter Inc." есть перспективная библиотека,
которая является расширением предыдущей библиотеки. Т.к. вы уже овладели
навыком созданием `CMakeList.txt` для статической библиотеки *formatter*, ваш 
руководитель поручает заняться созданием `CMakeList.txt` для библиотеки 
*formatter_ex*, которая в свою очередь использует библиотеку *formatter*.  
[CMakeLists для formatter_ex](https://gist.github.com/OpasnyPingvin/15ee3fb3b6caf3ddbf5bb7f8d379f263)

### Задание 3
Конечно же ваша компания предоставляет примеры использования своих библиотек.
Чтобы продемонстрировать как работать с библиотекой *formatter_ex*,
вам необходимо создать два `CMakeList.txt` для двух простых приложений:
* *hello_world*, которое использует библиотеку *formatter_ex*;
* *solver*, приложение которое испольует статические библиотеки *formatter_ex* и *solver_lib*.  
  
[CMakeLists для solver_lib](https://gist.github.com/OpasnyPingvin/b3a098897275d5ae25b05932b1444785)  
[CMakeLists для solver](https://gist.github.com/OpasnyPingvin/f8f38f487087fff5a9d886854ea5d7d0)  
[CMakeLists для hello_world](https://gist.github.com/OpasnyPingvin/980924703ff65b2d9c2ea991e728858d)

### Сборка всех файлов
Сборка formatter lib:  
`$ cmake -H. -Bbuild`
[Вывод](https://gist.github.com/OpasnyPingvin/4b77474bbc2500fb01f21fec83525086)
```
$ cmake --build build
[ 50%] Building CXX object CMakeFiles/formatter.dir/formatter.cpp.o
[100%] Linking CXX static library libformatter.a
[100%] Built target formatter
```

Сборка formatter_ex lib:  
`$ cmake -H. -Bbuild`
[Вывод](https://gist.github.com/OpasnyPingvin/29ce41486f79c3f9ddf2229967fd73de)
```
$ cmake --build build
[ 25%] Building CXX object formatter_build/CMakeFiles/formatter.dir/formatter.cpp.o
[ 50%] Linking CXX static library libformatter.a
[ 50%] Built target formatter
[ 75%] Building CXX object CMakeFiles/formatter_ex.dir/formatter_ex.cpp.o
[100%] Linking CXX static library libformatter_ex.a
[100%] Built target formatter_ex
```

Сборка solver_lib:  
`$ cmake -H. -Bbuild`
[Вывод](https://gist.github.com/OpasnyPingvin/e95df5591569ce7cf8bd5a04d2d6539c)
```
$ cmake --build build
[ 50%] Building CXX object CMakeFiles/solver_lib.dir/solver.cpp.o
[100%] Linking CXX static library libsolver_lib.a
[100%] Built target solver_lib
```

Сборка hello_world:  
`$ cmake -H. -Bbuild`
[Вывод](https://gist.github.com/OpasnyPingvin/7af180f35a170e3ca17fb54fd20d976a)
```
$ cmake --build build
[ 50%] Building CXX object CMakeFiles/hello_world.dir/hello_world.cpp.o
[100%] Linking CXX executable hello_world
[100%] Built target hello_world
```
Проверка:  
```
$ ./build/hello_world
-------------------------
hello, world!
-------------------------
```

Сборка solver:  
`$ cmake -H. -Bbuild`
[Вывод](https://gist.github.com/OpasnyPingvin/49f2297023342f0750485e69bda3a724)
```
$ cmake --build build
[ 12%] Building CXX object solver_lib_build/CMakeFiles/solver_lib.dir/solver.cpp.o
[ 25%] Linking CXX static library libsolver_lib.a
[ 25%] Built target solver_lib
[ 37%] Building CXX object formatter_build/CMakeFiles/formatter.dir/formatter.cpp.o
[ 50%] Linking CXX static library libformatter.a
[ 50%] Built target formatter
[ 62%] Building CXX object formatter_ex_build/CMakeFiles/formatter_ex.dir/formatter_ex.cpp.o
[ 75%] Linking CXX static library libformatter_ex.a
[ 75%] Built target formatter_ex
[ 87%] Building CXX object CMakeFiles/solver.dir/equation.cpp.o
[100%] Linking CXX executable solver
[100%] Built target solver
```

Проверка:  
```
$ ./build/solver
1 -3 2
-------------------------
x1 = 1.000000
-------------------------
-------------------------
x2 = 2.000000
-------------------------
```

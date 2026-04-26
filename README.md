# Get Next Line

![Score](https://img.shields.io/badge/score-125%2F100-success)
![C](https://img.shields.io/badge/language-C-blue)
![File I/O](https://img.shields.io/badge/concept-File%20I%2FO-success)

## 📌 Overview
**Get Next Line (GNL)** is a function that reads a file descriptor line by line. Created as part of the 1337 (42 Network) curriculum, this project introduces the concept of static variables and buffer management in C.

Reading from a file descriptor efficiently without knowing its size beforehand is a common requirement in software engineering, especially in network programming or parsing configuration files. This project ensures I can handle arbitrary buffer sizes while avoiding memory leaks.

## 💡 Core Concepts Explored
### Static Variables & Buffered I/O
**Definition:** Static variables in C preserve their state between function calls. Buffered I/O involves reading chunks of data from a stream into a temporary memory buffer rather than reading byte-by-byte.
**Problem Solved:** It solves the problem of efficiently reading continuous streams of text from a file descriptor of unknown length, maintaining the reading position across multiple function calls without losing unread data.

## 🚀 Features
- Reads dynamically from any valid file descriptor.
- Works securely with varying `BUFFER_SIZE` during compilation.
- Handles multiple file descriptors seamlessly (Bonus part).
- Strictly leak-proof, ensuring memory is cleanly freed upon EOF or error.

## 📥 How to Clone
To clone this project, use the following command:
```bash
git clone git@github.com:Anasqabbal/get_next_line.git
cd get_next_line
```

## 🛠️ Usage
Compile the project with your desired buffer size:
```bash
gcc -Wall -Wextra -Werror -D BUFFER_SIZE=42 get_next_line.c get_next_line_utils.c main.c
./a.out
```
Inside your `main.c`:
```c
#include "get_next_line.h"
#include <fcntl.h>
#include <stdio.h>

int main(void) {
    int fd = open("test.txt", O_RDONLY);
    char *line;
    while ((line = get_next_line(fd)) != NULL) {
        printf("%s", line);
        free(line);
    }
    close(fd);
    return 0;
}
```

## 🧠 What I Learned
- Intimate knowledge of memory management, dangling pointers, and static variables.
- Reading and manipulating continuous streams of data efficiently.
- Writing robust error-handling logic for unpredictable I/O operations.

## 🌐 Connect with me
[![GitHub](https://img.shields.io/badge/GitHub-black?logo=github)](https://github.com/Anasqabbal)
[![LinkedIn](https://img.shields.io/badge/-IN-0A66C2?logo=linkedin&logoColor=0a66c2)](https://www.linkedin.com/in/anasqabbal/)


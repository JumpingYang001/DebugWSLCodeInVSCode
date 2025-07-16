# DebugWSLCodeInVSCode
Debug WSL C/C++ code in VSCode


/home/myusername/.vscode/launch.json

```
{
    "version": "0.2.0",
    "configurations": [
        {
            "name": "Debug Simple C Program",
            "type": "gdb",
            "request": "launch",
            "target": "/home/myusername/myrepo/simple_program",
            "cwd": "/home/myusername/myrepo",
            "valuesFormatting": "parseText",
            "preLaunchTask": "build simple C program"
        },
        {
            "name": "Debug Simple C Program (with GDB commands)",
            "type": "gdb",
            "request": "launch",
            "target": "/home/myusername/myrepo/simple_program",
            "cwd": "/home/myusername/myrepo",
            "valuesFormatting": "parseText",
            "preLaunchTask": "build simple C program",
            "gdbpath": "/usr/bin/gdb",
            "debugger_args": [
                "-nx"
            ]
        }
    ]
}

/home/myusername/.vscode/tasks.json

```
{
	"version": "2.0.0",
	"tasks": [
		{
			"label": "build simple C program",
			"type": "shell",
			"command": "gcc",
			"args": [
				"-g",
				"-O0",
				"-Wall",
				"-Wextra",
				"-o",
				"simple_program",
				"simple_program.c"
			],
			"group": "build",
			"isBackground": false,
			"problemMatcher": [
				"$gcc"
			],
			"options": {
				"cwd": "/home/myusername/myrepo"
			}
		}
	]
}
```

/mnt/d/Repo01/myrepo/simple_program.c
```
#include <stdio.h>
#include <stdlib.h>

int add_numbers(int a, int b) {
    return a + b;
}

int main() {
    int x = 10;  // <-- Set a breakpoint here
    int y = 20;
    int result;
    int i;
    
    printf("Starting simple math program...\n");
    printf("x = %d, y = %d\n", x, y);
    
    result = add_numbers(x, y);
    
    printf("Result: %d + %d = %d\n", x, y, result);
    
    // Let's add a loop for more debugging fun
    for (i = 0; i < 5; i++) {
        printf("Loop iteration %d\n", i);
    }
    
    printf("Program finished!\n");
    return 0;
}
```

# C / C++

将 C 添加至环境变量，打开应用商店，输入 `C/C++` 并安装，安装完成后打开工作区中的 C 文件或 C++ 文件，使用快捷键 `F5` ，然后选择 `C++ (GDB/LLDB)` ，选择 `gcc.exe build and debug active file` ，之后会在当前工作区中的 `.vscode` 文件夹中自动生成 `launch.json` 配置文件。

```json
{
    "version": "0.2.0",
    "configurations": [
        {
            "name": "gcc.exe build and debug active file",
            "type": "cppdbg",
            "request": "launch",
            "program": "${fileDirname}\\${fileBasenameNoExtension}.exe",
            "args": [],
            "stopAtEntry": false,
            "cwd": "${workspaceFolder}",
            "environment": [],
            "externalConsole": true,
            "MIMode": "gdb",
            "miDebuggerPath": "当前环境中 gdb.exe 的执行路径",
            "setupCommands": [
                {
                    "description": "为 gdb 启用整齐打印",
                    "text": "-enable-pretty-printing",
                    "ignoreFailures": true
                }
            ],
            "preLaunchTask": "gcc.exe build active file"
        }
    ]
}
```

编辑好 `launch.json` 配置文件后保存，返回到工作区中的 C 文件或 C++ 文件，重新使用快捷键 `F5` ， Visual Studio Code 会弹出错误窗口并提示 `找不到任务"gcc.exe build active file"` ，选择 `配置任务` ，选择 `C/C++: gcc.exe build active file` ，会在当前工作区中的 `.vscode` 文件夹中自动生成 `tasks.json` 配置文件。

```json
{
    "version": "2.0.0",
    "tasks": [
        {
            "type": "shell",
            "label": "gcc.exe build active file",
            "command": "C:\\Project\\mingw64\\bin\\gcc.exe",
            "args": [
                "-g",
                "${file}",
                "-o",
                "${fileDirname}\\${fileBasenameNoExtension}.exe"
            ],
            "options": {
                "cwd": "C:\\Project\\mingw64\\bin"
            },
            "problemMatcher": [
                "$gcc"
            ],
            "group": "build"
        }
    ]
}
```

编辑好 `tasks.json` 配置文件后保存，再次返回到工作区中的 C 文件或 C++ 文件，此时再次使用快捷键 `F5` 即可看到运行结果。
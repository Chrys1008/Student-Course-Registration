# Student Course Registration

A C++ project containing two separate executables (`admin_app` and `student_app`) built with CMake and backed by SQLite.

## Project Structure

```text
.
├── Admin/
│   └── main.cpp
├── Student/
│   └── main.cpp
├── sqlite/          # Optional: place sqlite3.c and sqlite3.h here if using the amalgamation
├── CMakeLists.txt
└── README.md
```

## Prerequisites

- **C++17** compatible compiler (`g++`, `clang++`, or MSVC)
- **CMake** 3.16 or higher
- **SQLite3** (either the SQLite C amalgamation in `sqlite/` or a system-installed `SQLite3` package)

## Build Instructions

1. **Configure the project:**
   ```bash
   cmake -B build
   ```

2. **Compile both executables:**
   ```bash
   cmake --build build
   ```

## Running the Applications

On **Linux / macOS**:
```bash
./build/admin_app
./build/student_app
```

On **Windows (PowerShell)**:
```powershell
.\build\admin_app.exe
.\build\student_app.exe
```

*(Note: If you are using Visual Studio / MSVC multi-config builds, look inside `.\build\Debug\` or `.\build\Release\`.)*


# NullHandler

NullHandler is a tiny Windows executable that does absolutely nothing.

It exists to provide an explicit, intentional “do nothing” file association for Windows —
useful when a file type is accidentally assigned to the wrong application and you want a
safe, reversible alternative to editing the registry.

---

## Why?

Windows does not provide a built-in way to intentionally assign *no operation* as a file
handler.

- Removing an association causes repeated prompts
- Assigning a real application causes unintended behavior
- Editing the registry is risky and error-prone

NullHandler allows you to deliberately define:

> When this file type is opened, do nothing.

Not an error.  
Not a prompt.  
An intentional no-op.

---

## Inspiration

Inspired by IBM mainframe utility **IEFBR14 (1960s)** —
a program that has reliably done nothing for over half a century.

Some ideas outlive the platforms they run on.

---

## What it does

- Starts
- Returns 0
- Exits immediately

No file access.  
No registry access.  
No network activity.  
No UI.  
No console window.

---

## Source

The entire program is below.

```cpp
#include <windows.h>

int WINAPI WinMain(HINSTANCE, HINSTANCE, LPSTR, int)
{
    return 0;
}

## Build

Build as a **Windows subsystem (GUI)** executable so no console window appears.

### Visual Studio
- Create an Empty C++ Project
- Add the source above
- Set:
  - Linker → System → Subsystem: **Windows**
- Build Release

### MinGW
```bash
gcc NullHandler.cpp -o NullHandler.exe -mwindows -s


---

## Where to place the executable

Place `NullHandler.exe` in a stable location and do not move it after setting file
associations.

Recommended locations:

- `C:\Program Files\NullHandler\` (system-wide)
- `C:\Users\<you>\Programs\NullHandler\` (per-user)

Do **not** place it in `C:\Windows` or `System32`.

Windows file associations store the full path to the executable. If the file is moved
later, the association will break.

---

## Typical use cases

- Accidental “Always use this app” assignments
- Proprietary or intermediate file formats
- Log or data files not meant to be opened directly
- Intentional suppression of double-click behavior

---

## License

MIT — because doing nothing should be easy to reuse.


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

# Terminal Colors (ANSI Escape Codes)

## Color Codes

```text
31 = Red
32 = Green
33 = Yellow
34 = Blue
35 = Magenta
36 = Cyan
37 = White

0 = Reset Color
```

---

# Logic

```text
\033[COLOR_CODEm Text \033[0m
```

- `\033[` = Start color
- `COLOR_CODE` = Color number
- `m` = Apply color
- `\033[0m` = Reset back to normal

---

# macOS / Linux

```bash
echo -e "\033[31mError\033[0m"
echo -e "\033[32mSuccess\033[0m"
echo -e "\033[33mWarning\033[0m"
```

Output:

```text
Error    → Red
Success  → Green
Warning  → Yellow
```

---

# Example

```bash
echo -e "\033[36mApp Started\033[0m"
```

Output:

```text
App Started   (Cyan)
```
# C

- Compile c code and paste the executable file in bin set global

File Name : app.c
- 1:

```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

#define MAX_LINE 1024

void trim(char *str)
{
    char *start = str;

    while (*start == ' ' || *start == '\t')
        start++;

    if (start != str)
        memmove(str, start, strlen(start) + 1);

    char *end = str + strlen(str) - 1;

    while (end >= str &&
          (*end == ' ' ||
           *end == '\t' ||
           *end == '\n' ||
           *end == '\r'))
    {
        *end = '\0';
        end--;
    }
}

int main(int argc, char *argv[])
{
    if (argc < 2)
    {
        printf("Usage: myrun <command>\n");
        return 1;
    }

    FILE *fp = fopen(".run", "r");

    if (fp == NULL)
    {
        printf(".run file not found\n");
        return 1;
    }

    char line[MAX_LINE];

    while (fgets(line, sizeof(line), fp))
    {
        char *equal = strchr(line, '=');

        if (equal == NULL)
            continue;

        *equal = '\0';

        char *key = line;
        char *value = equal + 1;

        trim(key);
        trim(value);

        if (strcmp(key, argv[1]) == 0)
        {
            fclose(fp);

            printf("Executing: %s\n", value);

            return system(value);
        }
    }

    fclose(fp);

    printf("Command not found: %s\n", argv[1]);

    return 1;
}
```


- 2:
**Recomended:**
```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <ctype.h>

#define MAX_LINE 1024

void trim(char *str)
{
    char *start = str;

    while (isspace((unsigned char)*start))
        start++;

    memmove(str, start, strlen(start) + 1);

    if (*str == '\0')
        return;

    char *end = str + strlen(str) - 1;

    while (end >= str && isspace((unsigned char)*end))
    {
        *end = '\0';
        end--;
    }
}

int main(int argc, char *argv[])
{
    if (argc < 2)
    {
        printf("Usage:\n");
        printf("myrun <command>\n");
        return 1;
    }

    FILE *fp = fopen(".run", "r");

    if (fp == NULL)
    {
        printf("Error: .run file not found\n");
        return 1;
    }

    char line[MAX_LINE];
    char lastKey[MAX_LINE] = "";

    while (fgets(line, sizeof(line), fp))
    {
        char *equal = strchr(line, ':');

        if (equal == NULL)
            continue;

        *equal = '\0';

        char *key = line;
        char *value = equal + 1;

        trim(key);
        trim(value);

        strcpy(lastKey, key);

        if (strcmp(key, argv[1]) == 0)
        {
            fclose(fp);

            int status = system(value);

            if (status != 0)
            {
                printf("Error:\n");
                printf("Please write correct Command: %s\n", value);
                return 1;
            }

            return 0;
        }
    }

    fclose(fp);

    printf("Command not found [ %s ] in .run\n", argv[1]);

    return 1;
}
```
# GET NEXT LINE
A program that reads a file line by line and prints each line to the standard output.
Bonus: read multiple file descriptors.

## Usage
```bash
gcc -Wall -Wextra -Werror -D BUFFER_SIZE=32 get_next_line.c get_next_line_utils.c -o gnl
```
or for bonus
```bash
gcc -Wall -Wextra -Werror -D BUFFER_SIZE=32 get_next_line_bonus.c get_next_line_utils_bonus.c -o gnl
```
buffer size can be changed to any value.

the program can be tested with the following code (or just comment out the main function in the get_next_line.c file and run the program)
```c
#include "get_next_line.h"
int	main(void)
{
	int		fd;
	char	*result;
	int		i;

	i = 0;
	fd = open("/dev/pts/1", O_RDONLY);
	while (i < 5)
	{
		result = get_next_line(fd);
		printf("line %i: %s", i + 1, result);
		if (result != NULL)
			free(result);
		i++;
	}
	close(fd);
	result = get_next_line(fd);
	printf("line %i: %s", i + 1, result);
	if (result != NULL)
		free(result);
}
```

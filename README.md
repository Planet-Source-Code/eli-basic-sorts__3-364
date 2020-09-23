<div align="center">

## Basic Sorts


</div>

### Description

Great introduction for beginners to different sorts... Implements functions for a MinSort, BubbleSort, InsertionSort and ShellSort. All on an array of chars, with a specified complexity for each one. Good for beginners to study.
 
### More Info
 


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Eli](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/eli.md)
**Level**          |Beginner
**User Rating**    |4.7 (33 globes from 7 users)
**Compatibility**  |C, C\+\+ \(general\)
**Category**       |[Sorting](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/sorting__3-24.md)
**World**          |[C / C\+\+](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/c-c.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/eli-basic-sorts__3-364/archive/master.zip)

### API Declarations

```
#include <iostream.h>
#include <string.h>
#include <conio.h>
```


### Source Code

```
//**********************************************
//
// Different sorting algorithms. All sorting an
// array of chars.
//
//**********************************************
#include <iostream.h>
#include <string.h>
#include <conio.h>
void MinSort(char*, int);
void BubbleSort(char*, int);
void InsertionSort(char*, int);
void ShellSort(char*, int);
int main()
{
 clrscr();
 char cr[] = "dcabrosterdeonmlk";
 cout << cr << endl;
 ShellSort(cr, strlen(cr));
 cout << cr << endl;
 return 0;
}
// Complexity: n^2
void MinSort(char* array, int n)
{
 int i, j, temp_index;
 char min;
 for (i=0; i < n-1; ++i)
 {
  temp_index = i;
  min = array[i];
  for (j = i+1; j < n; ++j)
  {
   if (array[j] < min)
   {
	   temp_index = j;
	   min = array[j];
   }
  }
  array[temp_index] = array[i];
  array[i] = min;
 }
}
// Complexity: n^2
void BubbleSort(char* array, int n)
{
 int i, j;
 char temp;
 for (i = 0; i < n-1; ++i)
  for (j = i+1; j > 0; --j)
   if (array[j] < array[j-1])
   {
	   temp = array[j];
	   array[j] = array[j-1];
	   array[j-1] = temp;
   }
}
// Complexity: n^2
void InsertionSort(char* array, int n)
{
 int i, j;
 char temp;
 for (i=1; i < n; ++i)
 {
  temp = array[i];
  j = i-1;
  while ((j >= 0) && (temp < array[j]))
  {
   array[j+1] = array[j];
   j--;
  }
  array[j+1] = temp;
 }
}
// Complexity: n^1.2
void ShellSort(char* array, int n)
{
 int i, j, k, s, gap_cnt;
 char temp;
 int gaps[5];
 gaps[0] = 9; gaps[1] = 5; gaps[2] = 3; gaps[3] = 2; gaps[4] = 1;
 for (gap_cnt = 0; gap_cnt < 5; gap_cnt++)
 {
  k = gaps[gap_cnt];
  s = -k;
  for (i = k; i < n; ++i)
  {
   temp = array[i];
   j = i-k;
   if (s == 0)
   {
	   s = -k;
	   s++;
	   array[s] = temp;
   }
   while (temp < array[j] && j >= 0 && j <= n) // + Bound checking
   {
	   array[j+k] = array[j];
	   j = j-k;
   }
   array[j+k] = temp;
  }
 }
}
```


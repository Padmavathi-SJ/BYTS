## Pointer:

* Pointers always contain the address of any other variable.
* Pointers are derived data types.
* & (address of) and * (indirection operator)
  
### Decleration of pointer:
```
datatType * pointerName;
EX:
int* p; (or) int *p; (or) int * p;
all the above are same in c language.
```
```
01: int p; //here p will contain int type value
02: int* p; //here p will contain the address of any other int type variable;
03: float* p; //here p will contain the address of any other float type variable;
04: double* p; //here p will contain the address of any other double type variable;
```

### Initialization of pointer:
```
int a=10;
int* p;
p=&a; //here p is holding the address of a var.

* now, address of a is = 100, so p is holding 100, and p is also a var(pointer variable), it is also having a address in memory, so address of p is = 200.
* Now p is pointing a.
```

**Ex:**
```
#include<stdio.h>
int main() {
    int a=10;
    int* p=&a;
    printf("%d\n", a); //10
    printf("%d\n", *p); //10
    printf("%d", p); //1542941612 not exact
    printf("%x", p); //795d611c it will give in a hexadecimal form
    printf("%x", &p); //3e128bace128bb0 address of p
    return 0;
}
```

## Double Pointer:
* A pointer is storing the address of another pointer is called "double pointer".
```
#include<stdio.h>
int main() {
    int a=10;
    int* p=&a;
    int** q=&p;
    printf("%d\n", p); //-405204332
    printf("%d", q); //-405204328 //here q is a double pointer. q is holding the address of p.
    return 0;
}
```

## Pointer:

* Pointers always contain the address of any other variable.
* Pointers are derived data types.

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
```


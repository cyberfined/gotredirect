# gotredirect
Load library, that compiled as position independent code, into victim process address space, then redirect host function to the library function
# Usage
```bash
./gotredirect <pid> <path_to_lib.so> <original_function,replacer_function,[patch_offset]>
```
# Examples
```bash
./gotredirect 1234 payload.so puts,pay_puts,49
```
Attach to the process with id 1234, load payload.so to it address space, then rewrite puts GOT entry by pay_puts address. Write real puts addres to pay_puts+49

```bash
./gotredirect 1234 payload.so puts,pay_puts printf,pay_f,49
```
Attach to the process with id 1234, load payload.so to it address space, then rewrite puts GOT entry by pay_puts address, then rewrite printf GOT entry by pay_f address. Write real printf address to pay_f+49
# Build
1. git clone https://github.com/Undefined3102/gotredirect.git && cd gotredirect
2. make

# License
BSD4. Read LICENSE file

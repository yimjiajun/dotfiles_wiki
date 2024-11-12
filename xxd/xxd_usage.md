# XXD - Usage

<br>

______________________________________________________________________

<br>

## Convert binary

<br> **Binary to hex dump**

```bash
xxd <binary_file> > <hexdump_file>
```

<br> ex: `xxd test.bin test.txt`

```text
00000000: 9751 8000 9381 81e5 9702 0000 9382 c208  .Q..............
00000010: 7390 5230 7350 4030 d1ad 0000 0000 0000  s.R0sP@0........
```

<br> **Binary to binary digit dump**

```bash
xxd -b <binary_file> > <binary_digit_dump_file>
```

<br> ex: `xxd -b test.bin test.hex`

```text
00000000: 10010111 01010001 10000000 00000000 10010011 10000001  .Q....
00000006: 10000001 11100101 10010111 00000010 00000000 00000000  ......
```

<br>For more readable, you can use `-c` option to set the number of bytes per line.

```bash
xxd -c <number_of_bytes> <binary_file> > <hexdump_file>
```

ex: `xxd -c 4 test.bin test.txt`

```text
00000000: 10010111 01010001 10000000 00000000  .Q..
00000004: 10010011 10000001 10000001 11100101  ....
00000008: 10010111 00000010 00000000 00000000  ....
```

<br>

______________________________________________________________________

<br>

## Revert to binary

<br> Hexdump to binary

```bash
xxd -r <hexdump_file> > <binary_file>
```

ex: `xxd -r test.txt test.bin`

<br>

______________________________________________________________________

<br>

## Modify hexdump

<br>

**1. Convery binary to hexdump**

```bash
xxd <binary_file> > <hexdump_file>
```

ex: \<hexdump_file>

```text
00000000: 9751 8000 9381 81e5 9702 0000 9382 c208  .Q..............
00000010: 7390 5230 7350 4030 d1ad 0000 0000 0000  s.R0sP@0........
```

**2. Modify hexdump**

Modify the hexdump file using any text editor or command line.
Able to leave the ASCII part as unchanged even modified the hex part.

ex: `sed -i 's/9751/1234/g' <hexdump_file>`

```text
00000000: 1234 8000 9381 81e5 9702 0000 9382 c208  .Q..............
00000010: 7390 5230 7350 4030 d1ad 0000 0000 0000  s.R0sP@0........
```

**3. Convert back to binary**

```bash
xxd -r <hexdump_file> > <binary_file>
```

<br>

______________________________________________________________________

<br>

## Cherry-pick binary

For some binary file, we may drop some part of the binary file and keep the rest.

**1. Convery binary to hexdump**

```bash
xxd <binary_file> > <hexdump_file>
```

ex: \<hexdump_file>

```text
00000000: 9751 8000 9381 81e5 9702 0000 9382 c208  .Q..............
00000010: 7390 5230 7350 4030 d1ad 0000 0000 0000  s.R0sP@0........
00000020: 0000 0000 0000 0000 0000 0000 0000 0000  ................
```

**2. Remove the part you want to drop**

ex: `sed -i '1d' <hexdump_file>`

Remove second line from the hexdump file with 16 bytes or offset 0x00.

```text
00000010: 7390 5230 7350 4030 d1ad 0000 0000 0000  s.R0sP@0........
00000020: 0000 0000 0000 0000 0000 0000 0000 0000  ................
```

**3. Convert back to binary**

Since we removed 16 bytes from the hexdump file, the binary file expected will be 16 bytes shorter.

- if we revert the hexdump file to binary directly, we will found the removed second line is padding with 0x00 on offset 0x10.

  ex: `xxd -r <hexdump_file> > <binary_file> && xxd <binary_file> > <hexdump_file>`

  ```text
  00000000: 0000 0000 0000 0000 0000 0000 0000 0000  ................
  00000010: 7390 5230 7350 4030 d1ad 0000 0000 0000  s.R0sP@0........
  00000020: 0000 0000 0000 0000 0000 0000 0000 0000  ................
  ```

Suppress leading bytes of offset 0x10 to 0x00

```bash
xxd -r -s -<suppress_bytes> <hexdump_file> > <binary_file>
```

ex: `xxd -r -s -0x10 test.txt test.bin`

```text
00000000: 7390 5230 7350 4030 d1ad 0000 0000 0000  s.R0sP@0........
00000010: 0000 0000 0000 0000 0000 0000 0000 0000  ................
```

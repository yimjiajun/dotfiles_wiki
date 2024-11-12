# XXD

Make binary as a hexdump or do the reverse hexdump to binary.

```mermaid

graph LR
    A[.bin] --> B[.txt / hexdump]
    B --> A
```

Benefits:

1. Without extra external tools, you can convert binary to hexdump and vice versa.
1. Convert to hexdump easy to modify and convert back to binary.
1. Text is easy to search and replace by command line, which is easier for automation.

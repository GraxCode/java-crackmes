# Solution for CrackMe #1
<details>
  <summary>Spoiler warning</summary>
The way to solve this crackme is to overcome the obfuscation, and then interpret the bytecode correctly. 
A working key can be generated using this method:

```java
List<Integer> keys = new ArrayList<>();
int           n0   = "XVCe".hashCode() >> 8;
for (int i = 0, j = 0x80000000; i < 128; i++, j -= 0x01000000) { keys.add(n0 - j); }
```

</details>

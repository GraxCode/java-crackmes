# Solution for CrackMe #1
<details>
  <summary>Spoiler warning</summary>
The way to solve this crackme is to overcome the obfuscation, and then interpret the bytecode correctly. 
A working key can be generated using this method:

```java
int user_code_temp, user_code_crc, valid_code_crc;

// a bit of optimization
valid_code_crc = "XVCe".hashCode();

// outer, "permutation" loop
for(int user_code = 1; user_code != 0; user_code++) {
    user_code_temp = user_code; 
    user_code_crc = user_code_temp << 8;

    // inner, basic validation loop
    for(int j = 0; user_code_temp > 1; j++) {
        if ((-(user_code_temp%2)) == 0) {
            user_code_temp >>= 1;
        } else {
            user_code_temp = user_code_temp ^ 2;
            if (user_code_crc << 2 == 0) {
                // a bit more optimizations
                break;
            }
            user_code_temp--;
        }
        user_code_crc = (user_code_crc << user_code_temp) ^ (user_code_temp % 5);
        if ((user_code_crc << 2) == user_code_temp) {
            user_code_temp = user_code_temp ^ 6;
        }
    }

    // second stage validation
    // at this point, if this validation passes, we print the valid input value
    if (user_code_crc == valid_code_crc) {
        System.out.println(String.format("%d", user_code));
    }
}
```

The full explaination can be read at http://www.nullsecurity.org/article/crackmes_one_noverify_graxcode_java_crackme_1


</details>

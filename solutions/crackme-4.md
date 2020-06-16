# Solution for CrackMe #4
<details>
  <summary>Spoiler warning</summary>

There are two main methods. The real one is synthetic and hidden by some decompilers.
The actual main method takes in a hex[16] and reverses it, and then calls the fake main method.
Then it xors the value with `0xCAFEBABE` converted to BigInteger. Then it calls `AuthKey.valueOf` with the BigInteger converted to a decimal string. 
But the only possible number it takes to solve the crackme is `15542048963542891100`, which is hidden inside the `valueOf` method.
With that information you can calculate the key easily.

</details>

# Reversing the .ELF file revels the following code at the main:

      if (length < 0xc) { //0xc is 12 in decimal
        local_20 = 0;
        while( true ) {
          uVar1 = (ulong)local_20;
          length = strlen(magic_string);
          if (length <= uVar1) break;
          local_1c = local_1c + magic_string[local_20];
          local_20 = local_20 + 1; // this line addes 1 to local_20 variable
        }
        if (local_1c == 1000) {// 
          local_28 = strcat_str();
          printf("flag is flag{");
          for (local_20 = 0; local_20 < 10; local_20 = local_20 + 1) {
            putchar((int)*(char *)(local_28 + local_20));
          }
  ### We can see that local_1c is staking up the ascii code as int 
    local_1c = local_1c + magic_string[local_20]
    
  ### We can identify the following condition:
    if (local_1c == 1000)
    
  ### This give us a hint that we need to bring local_1c to 1000 the string size is 12 we need to decrese the end of the string and the start of 
  ### the string so the number of chars inside the magic string is 10 in magic_string{0} first char is space which its value is 10, 
  ### the magic_string{11} is NULL, there for the solution is 'c' ten times to get 990{10 time 'c' acii value} + 10 {space ascii value}
  
 ![jumpjumpjump_flag](https://user-images.githubusercontent.com/30953572/184826802-3ee07119-f6da-4ffa-9418-60a5671ebb01.png)

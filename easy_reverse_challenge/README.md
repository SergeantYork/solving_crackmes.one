Reversing the .ELF file the using GHIDRA reverse engineering, checking the main function revels the following code:
undefined8 main(int argc,char **argv)

{
  size_t length;
  
  if (argc == 2) {
    length = strlen(argv[1]);
    if (length == 10) {
      if (argv[1][4] == '@') {
        puts("Nice Job!!");
        printf("flag{%s}\n",argv[1]);
      }
      else {
        usage(*argv);
      }
    }
    else {
      usage(*argv);
    }
  }
  else {
    usage(*argv);
  }
  return 0;
}
I renamed several variables and it reveld that in order to crack the pass word we need a 10 length string with @ between letters.
inserting the following for each argv space:
argv[1][0]=a
argv[1][1]=b
argv[1][2]=c
argv[1][3]=d
argv[1][4] == @
argv[1][5]=e
argv[1][6]=f
argv[1][7]=g
argv[1][8]=h
argv[1][9]=i
this revels the following answer in the terminal 
"
Nice Job!!
flag{abcd@efghi}
"
![easy_reverse_flag](https://user-images.githubusercontent.com/30953572/184820208-cd49bfac-9469-447d-a470-37b4f63d155d.png)

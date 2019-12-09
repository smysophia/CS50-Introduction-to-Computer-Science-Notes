# Command line
`clang hello.c` compiling 汇编  source code to machine code
`clang hello.c -lcs50` link in cs50  
`clang -o hello hello.c` output hello.c to hello  
`./hello` to run it  
`make hello` = `clang -o hello hello.c -lcs50`  
`ls` list 所有文件的列表  
`cd` change directory 什么都不接的话跳回home directory  
`cd .` to current directory  
`cd ..` to parent directory (upper) `cd ../..` 再返回一层  
`pwd` present working directory  
`mkdir` make directory 创建一个directory  
`cp hello.txt hi.txt` copy hello.txt name as hi.txt  
`cp -r pset0 pset3` copy recursively directory pset0 and name the new pset 3 因为directory里还有别的文件，所以recursively  
`rm` remove (delete it) 
`rm -f` force remove
`rm -r` remove recursively a directory  
`rm -rf` remove recursively and force directory  
`redir` remove a directory
`mv greddy.c greedy.c` move (rename) greddy.c to greedy.c  

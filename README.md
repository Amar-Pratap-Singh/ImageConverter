# ImageConverter

This program helps you to convert a PNG image with some specifications to a BMP image.  

### BUILDING PROCESS

All the files should be in one directory which is required to complete the program.
All the required files are :-

BMP_struct.h
function.h
PNG_struct.h
BMP_write.c
PNG_read.c
filter.c
main.c
zpipe.c
makefile
libz.a
<image>.png

### Composition of makefile

##### The ‘gcc -c file.c’ command compile file.c file but does not make an executable instead make an object (file.o) file due to ‘-c’ after gcc which can be used later in other commands where they are required.
  
##### makefile: 
    output: main.o PNG_read.o filter.o BMP_write.o zpipe.o
        gcc -o my_project main.o PNG_read.o filter.o BMP_write.o libz.a zpipe.o -lz

    main.o: main.c
        gcc -c main.c

    PNG_read.o: PNG_read.c
        gcc -c PNG_read.c

    filter.o: filter.c
        gcc -c filter.c

    BMP_write.o: BMP_write.c
        gcc -c BMP_write.c

    zpipe.o : zpipe.c
        gcc -I . -c zpipe.c -lz
  
   
##### These are the respective codes to make respective object files.
##### Since, zpipe.c is linked with zlib.h hence to work, in the command ‘-lz’ extension is added to include zlib header file.
    
##### Now, control goes back to our first task ‘output’, where the following command is executed: 
> gcc -o my_project main.o PNG_read.o filter.o BMP_write.o libz.a zpipe.o -lz


##### ‘-o my_project’ makes an executable of name “my_project” (once the above command is executed successfully) which when executed runs the program and a desired <filename>.bmp is created.


##### One task is ‘clean':
> clean: 
>    rm main.o PNG_read.o filter.o BMP_write.o zpipe.o my_project temp.bin

##### When this task is performed using ‘make clean’ command, all the executable along with all the .o files is removed. From the outputs, only the finalimage (bmp format) is retained.

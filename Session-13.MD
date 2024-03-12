# Colors in the shell script :


```
Color	Foreground Code	Background Code
Black	30	40
Red	31	41
Green	32	42
Yellow	33	43
Blue	34	44
Magenta	35	45
Cyan	36	46
Light Gray	37	47
Gray	90	100
Light Red	91	101
Light Green	92	102
Light Yellow	93	103
Light Blue	94	104
Light Magenta	95	105
Light Cyan	96	106
White	97	107
```


# Note : Remove whole content in the file >> Esc:1 $d


```
#!/bin/bash 
DATE=$(date +%F)
outputfile="$0"-$DATE.log


RED="\e[31m"
GREEN="\e[32m"
NOCOLOR="\e[0m"

checkerror(){
  if [ $1 -eq 0  ]
  then 
  echo -e " ${GREEN}  $2 software installed sucessfully ${NOCOLOR}"
  else 
  echo -e " ${RED}   $2 software installation failure ${NOCOLOR}"
  fi
}


userid=$(id -u)
if [ $userid -eq 0 ]
then 
  echo "Installing Tree software"
  apt-get install tree -y &>>/tmp/$outputfile
  checkerror $? Tree
  echo "Installing Tree software completed "
else 
  echo -e " ${RED} Please run the script with root user ${NOCOLOR}"
fi 

```


# Loops :

# Print numbers from 1 to 5 

```
#!/bin/bash 
echo "1"
echo "2"
echo "3"
echo "4"
echo "5"
```
# Print numbers from 1 to 1000
* Algorithm :
    * To print numbers from 1 to 1000
    * Number=1  Number= 1000
    * echo "Number"
* Syntax:

```
for condition
do 
steps 
done 
```

```
#!/bin/bash 
for i in {1..1000}
do 
echo "$i"
done 
```

# Print the values in the array 

```
#!/bin/bash
fruits=("apple" "banana" "mango")
for fruitnames in $fruits
do 
# echo "The first fruit in the array is $fruits[@]"
echo "$fruits[@]"
done

```

```
#!/bin/bash
fruits=("apple" "banana" "mango")
for fruitnames in ${fruits[@]}
do 
# echo "The first fruit in the array is $fruits[@]"
echo "$fruitnames"
done
```


# Assignement :
* Script that can find the .log files which are older than 7 days and delete them by using for loop .

1. To find the log file(.log) which are older than 1 week 

```
find /pathtosearch/ -type f -name "*.log" -mtime +7

Deletefiles=$(find .  -type f -name "*.log" -mtime +7)

```
2. Delete the file 
3. Need to log the deleted file names
```
for step 2 & 3
use for loop and echo while deleting

echo "$Deletefile" &>>/tmp/$logfile
```

4. Error mechanism 
```
checkerror
```
5. Logggig mechanism 
```
DATE=$(date +%F)
logfile="$0"-$DATE.log
```



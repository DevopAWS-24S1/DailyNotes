# Special Variables:
   * Shell scripting also has special variables like `$0`, `$1`, `$@`, `$*`, etc., which hold special meanings. For instance, `$0` holds the name of the script itself, `$1`, `$2`, etc., hold positional parameters, and `$@` holds all positional parameters.

   Example:
   ```bash
   echo "Script name: $0"
   echo "All arguments: $@"
   echo " Last command status: $?"


```
#!/bin/bash
person1=Surya
person2=Teja

echo "$person1 : Hey $person2. How are you ..? "
echo "$person2 : Hi $person1. Im good . How is your day ..? "
echo "$person1 : My day is good $person2. Glad to meet you ."
echo "Script name: $0"
echo "All arguments: $@"
echo " Last command status: $?"

```

# Operators : 

### Arithmetic Operators:

- `+`: Addition
- `-`: Subtraction
- `*`: Multiplication
- `/`: Division
- `%`: Modulus (remainder after division)
- `**`: Exponentiation (raise to the power of)

### String Operators:

- `=`: Checks if two strings are equal
- `!=`: Checks if two strings are not equal
- `-z`: Checks if the length of a string is zero
- `-n`: Checks if the length of a string is non-zero

### Comparison Operators (for numeric comparisons):

- `-eq`: Equal to
- `-ne`: Not equal to
- `-lt`: Less than
- `-le`: Less than or equal to
- `-gt`: Greater than
- `-ge`: Greater than or equal to

### Logical Operators:

- `!`: Logical NOT
- `-a` (or `&&`): Logical AND
- `-o` (or `||`): Logical OR

### File Test Operators:

- `-e`: Checks if a file exists
- `-f`: Checks if it's a regular file
- `-d`: Checks if it's a directory
- `-r`: Checks if a file is readable
- `-w`: Checks if a file is writable
- `-x`: Checks if a file is executable

### Other Operators:

- `=` (assignment): Assigns a value to a variable
- `+=` (compound assignment): Appends to a variable or adds to a number variable

* These operators are used in conditional statements (`if`, `elif`, `case`), arithmetic operations, string manipulation, and file tests within Bash scripts. Depending on the context, you may use different operators to achieve the desired functionality in your script.


# condition 

* Syntax:

```
if [ condition ]
then 
echo " number is grater than 100 "
else
echo "number is less than 100 "
fi 
```

* Script to print whether number is greater than 100 

```
#!/bin/bash
echo " Enter the Number : "
read number
if [ $number -gt 100 ]
then 
echo " $number is greater than 100"
else 
echo "$number is lessthan 100"
fi 

```

* If it is sunday > it should print today is holiday. If any other day > it should print Go to the school.

* Algorithm:
1. Provide an option to the user to enter the day    >> read
2. Compare the day with sunday to saturday           >> if [ = ]
3. True - print - today is holiday                    >> echo 
4. False - print - Go to the school                   >> echo 


```
#!/bin/bash 
echo "Enter the Day: " 
read day
if [ $day = "sunday" ]
then 
echo "Today is Holiday "
else 
echo " Go to school"
fi 
```

## To install a software by using shell script 

```

#!/bin/bash 
userid=$(id -u)
if [ $userid -eq 0 ]
then 
  apt-get install tree -y 
else 
  echo " Please run the script with root user "
fi 

```


```

#!/bin/bash 
userid=$(id -u)
if [ $userid -eq 0 ]
then 
  apt-get install $1 -y 
else 
  echo " Please run the script with root user "
fi 

```

```
/bin/bash install.sh maven 
```


# Improvise te above script :
* logging mechanism 
* route those logs to the file 
* Error checking mechanism 

# Error & Logging  Mechanism :

```
#!/bin/bash 
DATE=$(date +%F)
outputfile="$0"-$DATE.log

userid=$(id -u)
if [ $userid -eq 0 ]
then 
  apt-get install tree -y &>>/tmp/$outputfile
  if [ $? -eq 0  ]
  then 
  echo "Tree software installed sucessfully"
  else 
  echo " Tree software installation failure"
  fi 
else 
  echo " Please run the script with root user "
fi 
```


# Redirect 

```
> - overwrite the content in the file 
>> - append the content to the file 
```


# Functions:

* syntax:

```
functionname(){

}
```


```
checkerror(){
  if [ $? -eq 0  ]
  then 
  echo "Tree software installed sucessfully"
  else 
  echo " Tree software installation failure"
  fi
}
```


```
#!/bin/bash 
DATE=$(date +%F)
outputfile="$0"-$DATE.log


checkerror(){
  if [ $1 -eq 0  ]
  then 
  echo "$2 software installed sucessfully"
  else 
  echo " $2 software installation failure"
  fi
}


userid=$(id -u)
if [ $userid -eq 0 ]
then 
  echo "Installing Tree software"
  apt-get install tree -y &>>/tmp/$outputfile
  checkerror $? tree
  echo "Installing Tree software completed "

else 
  echo " Please run the script with root user "
fi 


userid=$(id -u)
if [ $userid -eq 0 ]
then 
   echo "Installing maven software"
  apt-get install maven -y &>>/tmp/$outputfile
  checkerror $? maven
echo "Installing maven  software completed "

else 
  echo " Please run the script with root user "
fi 
```

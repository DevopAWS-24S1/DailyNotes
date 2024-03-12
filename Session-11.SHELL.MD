# Shell scripting :

## Scripting vs Coding 
* Coding mainly deals with developing the aplication.
* Scripting is automating the daily activities are doing repeatedly.

* Place  manual steps in single file and run it.
# Create a file for shell script 

```
Helloworld.sh
```

* Shell script file starts with a shebang
* shebang >> #!/bin/bash  >>  Tell to your file that you are using bash interpreter to run this file 

```
#!/bin/bash 
echo "helloWorld"
```
# Run the shell script :

```
/bin/bash helloworld.sh  >> without execute permissions 

chmod +x helloworld.sh
./helloworld.sh          >> with execute permissions

```

# Conversation :
```
#!/bin/bash
echo "Surya : Hey Teja. How are you ..? "
echo "Teja : Hi Surya. Im good . How is your day ..? "
echo "Surya : My day is good Teja. Glad to meet you ."
```

* DRY Policy >> Dont repeat yourself 

# Variable : 

* Syntax:
```
variablename=varaiablevalue
```


```
#!/bin/bash
person1=Surya
person2=Teja

echo "$person1 : Hey $person2. How are you ..? "
echo "$person2 : Hi $person1. Im good . How is your day ..? "
echo "$person1 : My day is good $person2. Glad to meet you ."
```


```
#!/bin/bash
DATE=$(date)
echo " This scripting is running at $DATE"

```




# Agruments :

```
#!/bin/bash
person1=$1
person2=$2

echo "$person1 : Hey $person2. How are you ..? "
echo "$person2 : Hi $person1. Im good . How is your day ..? "
echo "$person1 : My day is good $person2. Glad to meet you ."
```

```
/bin/bash/ argument.sh Raju Hari 
```

# Add two numbers :

```
#!/bin/bash
Number1=5
Number2=4
sum=$(($Number1 + $Number2))
echo "The sum of two numbers is : $sum"
```


```
#!/bin/bash
echo " Adding two numbers"
echo "Enter Number1 value : "
read Number1
echo "Enter Number2 value : "
read Number2
sum=$(($Number1 + $Number2))
echo "The sum of two numbers is : $sum"
```

* read provide an option to the user to input the values 
* read -s >> hide the value that is typying by the user 

```
#!/bin/bash
echo "username"
read username
echo "password"
read -s password 
echo "User input values are $username & $password"

```


# DataTypes:
1. String  >> person=Surya
2. Integer >> num=4
3. Array  >> fruits=("apple" "banana" "mango")
4. Boolean >> True/False 

# Note : In shell script . No need of defining data type 

* int var = 4
* string name = teja 
* array fruits = "apple", "banana", "mango"
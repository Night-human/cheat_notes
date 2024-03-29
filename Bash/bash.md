# Bash commands

# Output

## cat
Display the content of a file

    cat <file>

### pipes: |

- wc: word count(lines, words, characters)

        cat <file> | wc

### stdout: >

- \> : send the output stream to another process

        //Overwrites the file
        ls > <file>

        //Append output
        ls >> <file>

### Redirection

-  Redirects the output stream depending on the succes or error: 1:succes   2:error

        ls /will_cause_error 1>output.txt 2>error.txt

# Brace expansion {}
List of values/ranges basically.

    echo c{0,1,2}t

    echo c{0..20}t

    //2 by 2
    echo c{1..30..2}t

# Parameter expansion ${}

    //set variable
    hello="Hello you stranger"

    //substring from 6th position
    echo ${hello:6}
    > you stranger

    //substring from 6th to 3 positions ahead
    echo ${hello:6:3}
    > you

    // replace string
    echo ${hello/stranger/dude}
    > Hello you dude

    // replace a letter
    echo ${hello//e/_}
    > H_llo you strang_r

# Command substitution $()

    echo "This is the: $(nano --version)"
    
# Arithmetic expansion $(())

    echo $((2+2))
    > 4

# Comparing values with test []

    //Display test help
    help test | less

    //Check if a file exists example
    [ -a index.s ]; echo $?

# Arrays

    //Create an array
    fruits=("Melon" "Pineapple" "Grape")

    //Add next value to the list
    fruits+=("Strawberry")

    //Add value from index
    fruits[2]="Apple"

    //Print all values
    echo ${fruits[@]}

# if

    if condition
    then
        script
    fi

    //Example
    if [ 1 -eq 1 ] 
    then 
        echo "1 equeals to 1"
    fi

# while

    while condition
    do
        script
    done

    //Example
    declare -i n=0
    while [ $n -lt 5 ]
    do 
        echo "hi" 
        ((n++))
    done

# for

    for i in  ... 
    do
        script
    done

    //Example
    for i in {1..12}
    do 
        echo $i
    done

    //Example
    fruits=("watermelon" "apple" "banana")
    for i in ${fruits[@]}
    do 
        echo $i
    done
    
# case
    
    fruit="mango"
    
    case $fruit in
        apple) echo "An apple";;
        melon|pineapple) echo "This certainaly not";;
        *) echo "Default"
    esac

# functions

    myFunction() {
        echo "It's a function from $1"
    }
    
    myFunction Alex //call with parameter
    
$ arguments

    //Example
    echo "This is an example from $1, for arguments in $0"
    
    ./script.bat Alex
    
    > "This is an example from Alex, for arguments in ./script.bat"
   
 
# options

    while options :a:b: option; do
        case $option in
            a) echo "argument a is $a"
            b) echo "argument a is $b"
            ?) echo "Empty"
        esac
    done
    
    > ./script.bat -a hola -b adios
    
# read

    echo "give me a number"
    read n
    
    echo $n


    
        

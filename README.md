# RustLang---convert_temperature_v1
To obtain user input and then print the result as output:
``` 
use std::io; 
```
### Declare function run_program() 
Make a repeating code with loop. Then printing a prompt stating what the game is and requesting input from the user:
```
fn run_program() {
    loop {
        println!("Welcome to the Convert Temperature Program!");
        println!("Do you want to convert to Celsius or Fahrenheit?");
        println!("Please enter C for Fahrenheit to Celsius, or F for Celsius to Fahrenheit:");
    }
}
```
### Declare temperature conversion type input
First, create a variable to store the user input:
```
let mut conversion_type = String::new();
```
Second, receiving user input:
```
io::stdin()
    .read_line(&mut conversion_type)
```
Last, handling potential failure with the Result type:
```
.expect("Failed to read line");
```
### Handling invalid temperature conversion type input
```
let conversion_type = match conversion_type.trim() {
    "C" => 1,
    "F" => 2,
    _ => {
        println!("Please input C or F!");
        continue;
    }
};
```
### Declare temperature input
```
println!("Please enter the temperature:");

    let mut temp = String::new();   
    io::stdin()
        .read_line(&mut temp)
        .expect("Failed to read line");
```
### Handling invalid temperature input
```
let temp: f64 = match temp.trim().parse() {
    Ok(temp) => temp,
    Err(_) => {
         println!("Please input a valid temperature");
         continue;
    }
};
```
### Declare converted temperature input
```
let converted_temp = if conversion_type == 1 {
    f_to_c(temp)
} else {
    c_to_f(temp)
};
println!("The converted temperature is {}", converted_temp);
```
### Declare function convert Celsius to Fahrenheit and vice versa
Celsius to Fahrenheit:
```
fn c_to_f(c: f64) -> f64 {
    c * (9. / 5.) + 32.
}
```
Fahrenheit to Celsius:
```
fn f_to_c(f: f64) -> f64 {
    (f - 32.) * (5. / 9.)
}
```
### Declare function main()
Print the message about exit program.
```
fn main() {
    run_program();
    println!("Program has exit!");
}
```
### The final code
``` 
// C to F: F = C*(9/5) + 32
// F to C: C = (F-32)*(5/9)

use std::io;

// Celsius to Fahrenheit
fn c_to_f(c: f64) -> f64 {
    c * (9. / 5.) + 32.
}

// Fahrenheit to Celsius
fn f_to_c(f: f64) -> f64 {
    (f - 32.) * (5. / 9.)
}

fn run_program() {
    loop {
        println!("Welcome to the Convert Temperature Program!");
        println!("Do you want to convert to Celsius or Fahrenheit?");
        println!("Please enter C for Fahrenheit to Celsius, or F for Celsius to Fahrenheit:");
        
        // Declare conversion type
        let mut conversion_type = String::new();
        io::stdin()
            .read_line(&mut conversion_type)
            .expect("Failed to read line");

        let conversion_type = match conversion_type.trim() {
            "C" => 1,
            "F" => 2,
            _ => {
                println!("Please input C or F!");
                continue;
            }
        };

        // Declare temperature input
        println!("Please enter the temperature:");

        let mut temp = String::new();   
        io::stdin()
            .read_line(&mut temp)
            .expect("Failed to read line");

        let temp: f64 = match temp.trim().parse() {
            Ok(temp) => temp,
            Err(_) => {
                println!("Please input a valid temperature");
                continue;
            }
        };

        // Declare converted temperature
        let converted_temp = if conversion_type == 1 {
            f_to_c(temp)
        } else {
            c_to_f(temp)
        };
        println!("The converted temperature is {}", converted_temp);
    }   
}

fn main() {
    run_program();
    println!("Program has exit!");
}
```

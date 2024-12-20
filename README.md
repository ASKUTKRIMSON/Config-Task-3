# Config to YAML Converter

This project is a command-line tool that parses user configuration files written in a custom configuration language and converts them into YAML format. It supports constants, nested structures (dictionaries and lists), and comments.

## Features

- Support for single-line (`%`) and multi-line (`/* */`) comments in input files.
- Constants can be defined and referenced automatically using the `^` symbol.
- Parsing of nested structures: dictionaries and lists.
- Conversion of parsed data into a YAML file.
- Simple implementation with room for extensions.

---

## Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/username/config_to_yaml.git
   ```
2. Navigate to the project directory:
   ```bash
   cd config_to_yaml
   ```
3. Compile the Java program:
   ```bash
   javac Main.java
   ```

---

## Usage

Run the program with the following syntax:
```bash
java Main -o <output_file>
```

- **`<output_file>`**: The name of the YAML file to generate.

### Input File Format

Example configuration file:
```plaintext
% This is an example configuration
def MAX_COUNT = 100;
{
  name = "example",
  values = [
    1, 2, 3
  ],
  max = ^MAX_COUNT,
}
```

```plaintext
def THRESHOLD = 10;
{
  settings = {
    mode = "auto",
    threshold = ^(THRESHOLD)
  },
  data = [1, 2, 3]
}
```

### Expected YAML Output

For the above configuration files, the output will be:
```yaml
max: 100
name: example
values:
- 1
- 2
- 3
```

```yaml
settings:
  mode: auto
  threshold: 10
data:
  - 1
  - 2
  - 3
```

---

## Testing

### Example Execution Log

```sh
Token: BANG, ![
  Group 0: ![ 
  Group 1: ![
  Group 16: ![
Token: LEFT_PAREN, (
  Group 0: (
  Group 1: (
  Group 2: (
Token: NUMBER, 1
  Group 0: 1
  Group 1: 1
  Group 13: 1
Token: COMMA, ,
  Group 0: , 
  Group 1: ,
  Group 8: ,
Token: NUMBER, 2
  Group 0: 2
  Group 1: 2
  Group 13: 2
Token: COMMA, ,
  Group 0: , 
  Group 1: ,
  Group 8: ,
Token: STRING (single-quoted), three
  Group 0: 'three'
  Group 1: 'three'
  Group 9: 'three'
  Group 10: three
Token: RIGHT_PAREN, )
  Group 0: ) 
  Group 1: )
  Group 3: )
Token: SEMICOLON, ;
  Group 0: ;
  Group 1: ;
  Group 7: ;
Token: EOF
Token: NAME, UNDEFINED_CONSTANT
  Group 0: UNDEFINED_CONSTANT
  Group 1: UNDEFINED_CONSTANT
  Group 14: UNDEFINED_CONSTANT
Token: SEMICOLON, ;
  Group 0: ;
  Group 1: ;
  Group 7: ;
Token: EOF
Token: LEFT_BRACE, @{
  Group 0: @{
  Group 1: @{
  Group 4: @{
Token: STRING (single-quoted), key1
  Group 0: 'key1'
  Group 1: 'key1'
  Group 9: 'key1'
  Group 10: key1
Token: COMMA, ,
  Group 0: , 
  Group 1: ,
  Group 8: ,
Token: STRING (single-quoted), value1
  Group 0: 'value1'
  Group 1: 'value1'
  Group 9: 'value1'
  Group 10: value1
Token: COMMA, ,
  Group 0: , 
  Group 1: ,
  Group 8: ,
Token: STRING (single-quoted), key2
  Group 0: 'key2'
  Group 1: 'key2'
  Group 9: 'key2'
  Group 10: key2
Token: COMMA, ,
  Group 0: , 
  Group 1: ,
  Group 8: ,
Token: NUMBER, 2
  Group 0: 2
  Group 1: 2
  Group 13: 2
Token: RIGHT_BRACE, }
  Group 0: }
  Group 1: }
  Group 5: }
Token: SEMICOLON, ;
  Group 0: ;
  Group 1: ;
  Group 7: ;
Token: EOF
```

### Photo

![image](https://github.com/user-attachments/assets/ad493470-1c2b-4ba6-84f7-aee2814bbb70)

![image](https://github.com/user-attachments/assets/042bd2d3-8a33-4092-be52-b7b1f6d96928)

---

## License

This project is licensed under the [MIT License](LICENSE).

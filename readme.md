# Minigrep

`mingrep` is a minimal version of the grep command-line utility, written in Rust. It allows users to search for a specified query string in a given file and prints out the lines containing the query.

## Components

The project consists of two main components:

`Library (lib.rs)`: Contains the core functionality of the mingrep tool, including functions for searching text, handling configurations, and running the search operation.

`Executable (main.rs)`: Acts as the entry point of the application, responsible for parsing command-line arguments, creating a Config object, and executing the search operation using the functions provided by the library.

### lib.rs

#### Functions

`run(config: Config) -> Result<(), Box<dyn Error>>`: Runs the mingrep application. It reads the contents of the specified file, performs a case-sensitive or case-insensitive search based on the configuration, and prints the matching lines.

`search<'a>(query: &str, contents: &'a str) -> Vec<&'a str>`: Performs a case-sensitive search for the given query string in the provided text content and returns a vector containing the matching lines.

`search_case_insensitive<'a>(query: &str, contents: &'a str) -> Vec<&'a str>`: Performs a case-insensitive search for the given query string in the provided text content and returns a vector containing the matching lines.

#### Structs

`Config`: Represents the configuration settings for the mingrep application, including the query string, file name, and case sensitivity.

Implementations

`Config::new(args: &[String]) -> Result<Config, &str>`: Constructs a new Config object from the command-line arguments. It validates the number of arguments and determines whether the search should be case-sensitive based on the presence of an environment variable.

### main.rs

Parses command-line arguments using `env::args()`.
Creates a Config object from the parsed arguments.
Prints the search query and file name to the console.
Executes the `mingrep::run()` function with the provided configuration.
Handles errors gracefully, printing error messages to the standard error stream.
Testing

The project includes unit tests in the tests module of lib.rs to verify the correctness of the search functions under various scenarios, including both case-sensitive and case-insensitive searches.

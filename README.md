# week4
def process_file_with_error_handling():
    """
    Reads content from an input file, modifies it (converts to uppercase),
    and writes the modified content to an output file.
    Includes robust error handling for file operations.
    """
    input_filename = input("Enter the name of the input file (e.g., input.txt): ")
    output_filename = input("Enter the name of the output file (e.g., output.txt): ")

    file_content = ""
    # --- Error Handling for Reading the Input File ---
    try:
        # Use 'with' statement for automatic file closing, even if errors occur
        with open(input_filename, 'r', encoding='utf-8') as infile:
            file_content = infile.read()
        print(f"\nSuccessfully read content from '{input_filename}'.")
        print("Original content snippet (first 100 chars):")
        print("---")
        print(file_content[:100] + "..." if len(file_content) > 100 else file_content)
        print("---\n")

    except FileNotFoundError:
        print(f"Error: The input file '{input_filename}' was not found.")
        print("Please ensure the file exists in the same directory as the script, or provide the full path.")
        return # Exit the function if input file not found
    except IOError as e:
        print(f"Error: Could not read from input file '{input_filename}'.")
        print(f"Details: {e}")
        return # Exit the function if there's an I/O error

    # --- Modify the content ---
    # For this example, we'll convert all text to uppercase.
    # You can change this modification logic as needed.
    modified_content = file_content.upper()
    print("Content modified (converted to uppercase).")

    # --- Error Handling for Writing to the Output File ---
    try:
        # Use 'with' statement for automatic file closing
        with open(output_filename, 'w', encoding='utf-8') as outfile:
            outfile.write(modified_content)
        print(f"Successfully wrote modified content to '{output_filename}'.")
        print("Modified content snippet (first 100 chars written to output):")
        print("---")
        print(modified_content[:100] + "..." if len(modified_content) > 100 else modified_content)
        print("---\n")

    except IOError as e:
        print(f"Error: Could not write to output file '{output_filename}'.")
        print(f"Details: {e}")
    except Exception as e:
        print(f"An unexpected error occurred during writing: {e}")

# Call the function to run the program
if __name__ == "__main__":
    print("Welcome to the File Read & Write Challenge with Error Handling!\n")
    process_file_with_error_handling()
    print("\nProgram finished.")

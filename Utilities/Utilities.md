# Utility Functions Quick Description and Usage

Concise documentation for the helper utilties

## File Tree
utilities/
└── Colors.sh
└── Communication.sh
└── Conversion.sh
└── Prompts.sh
└── Queries.sh
└── SSH.sh


## Colors.sh

Colors.sh/__int_lerp__: Performs integer linear interpolation between START and END using FRACTION (0 to 100).  
Usage: __int_lerp__ <start> <end> <fraction>  
Example Output: For __int_lerp__ 10 20 50, the output is: 15  
Output: Prints the interpolated integer value.

Colors.sh/__gradient_print__: Prints multi-line text with a vertical color gradient.  
Usage: __gradient_print__ "multi-line text" R1 G1 B1 R2 G2 B2 [excluded_chars]  
Example Output: When given ASCII art and colors from (128,0,128) to (0,255,255), the output is the ASCII art printed with a vertical gradient.  
Output: Prints the text with a gradient applied.

Colors.sh/__line_gradient__: Applies a left-to-right color gradient to a single line of text.  
Usage: __line_gradient__ "text" R1 G1 B1 R2 G2 B2  
Example Output: For __line_gradient__ "Hello" 255 0 0 0 0 255, the output is "Hello" printed with a gradient transitioning from red to blue.  
Output: Prints the text with a horizontal gradient applied.

Colors.sh/__line_rgb__: Prints a line of text in a single, solid RGB color.  
Usage: __line_rgb__ "text" R G B  
Example Output: For __line_rgb__ "Static Text" 0 255 0, the output is "Static Text" printed in bright green.  
Output: Prints the text in the specified color.

Colors.sh/__simulate_blink_async__: Simulates a blinking effect by toggling between bright and dim text asynchronously.  
Usage: __simulate_blink_async__ "text to blink" [times] [delay]  
Example Output: For __simulate_blink_async__ "Blinking" 5 0.3, the output is "Blinking" toggling between bright and dim (observed asynchronously).  
Output: Prints the blinking text effect asynchronously.

## Communication.sh

Communication.sh/__spin__: Runs an infinite spinner with rainbow color cycling in the background.  
Usage: __spin__ &  
Example Output: When executed in the background, the spinner animates through rainbow colors.  
Output: Runs indefinitely until terminated.

Communication.sh/__stop_spin__: Stops the running spinner process (if any) and restores the cursor.  
Usage: __stop_spin__  
Example Output: The spinner process is terminated and the cursor is made visible.  
Output: Terminates the spinner and resets SPINNER_PID.

Communication.sh/__info__: Prints an informational message in bold yellow and starts the rainbow spinner.  
Usage: __info__ "message"  
Example Output: "Processing..." is displayed in bold yellow with an active spinner.  
Output: Displays the message and starts the spinner.

Communication.sh/__update__: Updates the text displayed next to the spinner without stopping it.  
Usage: __update__ "new message"  
Example Output: The text next to the spinner is replaced with "new message".  
Output: Updates the spinner line text.

Communication.sh/__ok__: Stops the spinner and prints a success message in green.  
Usage: __ok__ "success message"  
Example Output: The spinner stops and "Completed successfully!" is printed in green bold.  
Output: Terminates the spinner and displays the success message.

Communication.sh/__err__: Stops the spinner and prints an error message in red.  
Usage: __err__ "error message"  
Example Output: The spinner stops and "Operation failed!" is printed in red bold.  
Output: Terminates the spinner and displays the error message.

Communication.sh/__handle_err__: Handles errors by stopping the spinner and printing error details including the line number, exit code, and failing command.  
Usage: trap '__handle_err__ $LINENO "$BASH_COMMAND"' ERR  
Example Output: Error details with line number, exit code, and failing command are printed.  
Output: Displays error details and stops the spinner.

## Conversion.sh

Conversion.sh/__ip_to_int__: Converts a dotted IPv4 address string to its 32-bit integer equivalent.  
Usage: __ip_to_int__ "127.0.0.1"  
Example Output: For __ip_to_int__ "127.0.0.1", the output is: 2130706433  
Output: Prints the 32-bit integer representation of the IP to stdout.

Conversion.sh/__int_to_ip__: Converts a 32-bit integer to its dotted IPv4 address equivalent.  
Usage: __int_to_ip__ 2130706433  
Example Output: For __int_to_ip__ 2130706433, the output is: 127.0.0.1  
Output: Prints the dotted IPv4 address string to stdout.

Conversion.sh/__cidr_to_netmask__: Converts a CIDR prefix to a dotted-decimal netmask.  
Usage: __cidr_to_netmask__ 18  
Example Output: For __cidr_to_netmask__ 18, the output is: 255.255.192.0  
Output: Prints the full subnet netmask.

## Prompts.sh

Prompts.sh/__check_root__: Checks if the current user is root.  
Usage: __check_root__  
Example Output: If not run as root, the output is: "Error: This script must be run as root (sudo)."  
Output: Exits 1 if not root.

Prompts.sh/__install_or_prompt__: Checks if a specified command is available.  
Usage: __install_or_prompt__ <command_name>  
Example Output: If "curl" is missing and the user declines installation, the output is: "Aborting script because 'curl' is not installed."  
Output: Exits 1 if user declines the installation.

Prompts.sh/__prompt_keep_installed_packages__: Prompts the user whether to keep or remove all packages that were installed in this session via __install_or_prompt__().  
Usage: __prompt_keep_installed_packages__  
Example Output: If the user chooses "No", the output is: "Removing the packages installed in this session..." followed by "Packages removed."  
Output: Removes packages if user says "No", otherwise does nothing.

## SSH.sh

SSH.sh/__wait_for_ssh__: Repeatedly attempts to connect via SSH to a specified host using a given username and password until SSH is reachable or until the maximum number of attempts is exhausted.  
Usage: __wait_for_ssh__ <host> <sshUsername> <sshPassword>  
Example Output: For __wait_for_ssh__ "192.168.1.100" "user" "pass", the output might be: SSH is up on "192.168.1.100"  
Output: Returns 0 if a connection is established within the max attempts, otherwise exits with code 1.

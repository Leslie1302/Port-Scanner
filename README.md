Port Scanner

This Python program performs a comprehensive port scan on a target host to identify open ports. It uses multithreading to enhance performance, enabling it to scan all 65,535 ports quickly.
Features

    Target Specification: The program accepts a hostname or IP address as input and resolves it to an IP address using Python's socket module.
    Port Scanning: Scans the full range of TCP ports (1–65,535) to check for open ports on the target.
    Multithreading: Implements multithreaded scanning, creating a separate thread for each port to speed up the scanning process.
    Timeout Handling: Sets a timeout for each port connection attempt, ensuring unresponsive ports don’t delay the scan.
    Detailed Output: Displays open ports, along with error messages for any issues encountered.
    Graceful Exit: Handles keyboard interrupts (Ctrl+C) gracefully, allowing the user to exit the program without abrupt termination.

Usage
Prerequisites

    Python 3.x installed on your system.

Running the Program

    Save the script as scanner.py (or any other name you prefer).

    Run the script from the command line:

python scanner.py <target>

Replace <target> with the hostname or IP address of the target you want to scan. For example:

    python scanner.py scanme.nmap.org

    The program will begin scanning all TCP ports (1–65,535) and display the status of each open port.

How It Works

    Argument Parsing:
        The script validates that the target (hostname or IP) is passed as a command-line argument.
        If the argument is missing or invalid, the program exits with an error message.

    Target Resolution:
        The program resolves the provided hostname into an IP address using socket.gethostbyname(). If the resolution fails, it reports an error.

    Port Scanning:
        A multithreaded approach is used to scan ports concurrently:
            For each port in the range 1–65,535, a thread is created and assigned to attempt a connection to that port.
            If the connection is successful, the port is reported as open.
            Errors or timeouts are handled gracefully to prevent the program from crashing.

    Multithreading:
        Threads are used to speed up the scanning process.
        Each thread independently scans a single port, reducing overall scan time significantly.

    Output:
        Displays the open ports as they are found.
        Provides error messages for socket issues, such as unresolvable hostnames or connection errors.

    Completion:
        The program waits for all threads to complete before displaying a completion message.

Example Output

--------------------------------------------------
Scanning target 45.33.32.156
Time started : 2024-12-29 12:34:56
--------------------------------------------------
Port 22 is open
Port 80 is open
Port 443 is open

Scan completed!

Limitations

    High System Resource Usage: Creating thousands of threads can be resource-intensive.
    No UDP Support: This scanner only scans TCP ports.
    No Banner Grabbing: The program identifies open ports but does not attempt to retrieve service banners.

License

This project is open-source and available under the MIT License.

Date : 02-05-2026

# Topic - File Handling and Log parser
Objective : Build a log parser security script with the help of file handling

Concept : 
A log parser security script is a program that uses file handling to read and analyze log files, extract important information like IP addresses, login attempts, timestamps, and error messages, and identify suspicious activities such as repeated failed logins, unauthorized access, or malware behavior. The main concept is to automate security monitoring by parsing log data, applying detection rules, and generating alerts or reports whenever abnormal activity is found.

Code :
def parse_log_file(filename):
    log_counts = {
        "INFO": 0,
        "ERROR": 0,
        "WARNING": 0
    }

    try:
        with open(filename, 'r') as file:
            for line in file:
                line = line.strip()

                if line.startswith("INFO"):
                    log_counts["INFO"] += 1
                elif line.startswith("ERROR"):
                    log_counts["ERROR"] += 1
                elif line.startswith("WARNING"):
                    log_counts["WARNING"] += 1

        print("LOG SUMMARY:")
        for level, count in log_counts.items():
            print(f"{level}: {count}")

    except FileNotFoundError:
        print("Error: File not found.")
 parse_log_file("sample_log_parser.txt")

NOTE: sample_log_parser.txt is a test log file used to verify and check the working of the log parser program.

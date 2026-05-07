Date : 06-05-2026

# Topic - Network Scanner
Objective : Build a network scanner using python which can also store the ouput.

Concept : 
A network scanner is a tool or system designed to discover, identify, and analyze devices, services, and vulnerabilities on a computer network. The core concept behind a network scanner is to map the structure and activity of a network by sending requests to devices and interpreting the responses.

Code : 
import subprocess
from datetime import datetime

target = input("Enter target IP address: ")

print("""
Choose scan type:
1. Quick scan
2. Full Port scan
3. Service scan
4. Full scan (Aggressive)
""") 

choice = input("Enter your choice :" )

if choice == "1" :
   command = f"nmap {target}"
elif choice == "2":
   command = f"nmap -p- {target}"
elif choice == "3" : 
   command = f"nmap -sV {target}"
elif choice == "4" :
   command = f"nmap -A  {target}"
else : 
   print("Invalid choice.")
   exit()          

print("\n [+] Running scan .....\n")

result = subprocess.getoutput(command)

formatted = f"""
==============================
      SCAN REPORT
==============================
Target: {target}

Scan Type: {command}

------------------------------
RESULT:
------------------------------
{result}

==============================
"""

timestamp = datetime.now().strftime("%Y%m%d_%H%M%S")
safe_target = target.replace(".", "_")
file_name = f"results/scan_{safe_target}_{timestamp}.txt"

with open(file_name , 'w') as f :
        f.write(formatted)

print(formatted)
print(f"\n[+] Result saved in {file_name}")        




Date : 01-05-2026

# Topic - Networking with sockets(in python)
Objective - Create a simple port scanner using sockets with the help of python 

Concept : 
Port - A port is a communication endpoint on a computer.
Goal of a Port Scanner - The scanner tries to connect to ports on a target IP or hostname.
Steps  - 
1.Creates a socket
2.Tries connecting to a port
3.Checks response
4.Prints result

Code : 
import socket
import threading
from queue import Queue

target = input("Enter the IP Address of the target : ")
queue = Queue()
open_ports =[]

def portscan(port):
    try :
        sock = socket.socket(socket.AF_INET,socket.SOCK_STREAM)
        sock.connect((target,port))
        return True
    except :
        return False

def fill_queue(port_list):
    for port in port_list:
        queue.put(port)

def worker():
    while not queue.empty():
        port = queue.get()
        if portscan(port):
            print("Port {} is open".format(port))

port_list = range(1,10000)
fill_queue(port_list)

thread_list = []

for t in range(50):
    thread = threading.Thread(target=worker)
    thread_list.append(thread)

for thread in thread_list :
    thread.start()

for thread in thread_list :
    thread.join()

print("Open ports are : ",open_ports)

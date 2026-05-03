Date : 29-04-2026

# Topic - Creating a ping sweeper using bash scripting
Objective : Understand how bash script is used to ping a network

Concept : A ping sweeper is a simple network discovery technique used to find which devices on a network are “alive”. It’s based on the Internet Control Message Protocol, specifically ICMP Echo Requests and Echo Replies.

Code :
#!/bin/bash

network="192.168.29"

echo " Stating ping sweep on $network.0/24 .... "

for ip in {1..254}
do 
   ping -c 1 -w 1 $network.$ip > /dev/null 2>&1

   if [ $? -eq 0 ]; then
     echo "[+] Host $network.$ip is up."

   else
     echo "[-] Host $network.$ip is down." 

   fi       

done

echo "Scan complete"

# Topic - Creating a file organizer using bash scripting
Objective : Understand how bash script is used to automate file organization.

Concept : A file organizer is built around the idea of automatically classifying and arranging files based on rules so that storage stays structured without manual effort.

Code :
#!/bin/bash 

dir="$1"

if [ ! -d "$dir" ]; then
   echo "No Directory Found...."
   exit 1
fi

mkdir -p "$dir/images"  "$dir/videos"   "$dir/documents"  "$dir/others"

for file in "$dir"/*
do 
  if [ -f  "$file" ]; then
     case "${file##*.}" in 
       jpg|jpeg|png|gif)
       mv "$file" "$dir/images"
       ;;
       mp4|mkv|avi)
       mv "$file" "$dir/videos"
       ;;
       pdf|docx|doc|txt)
       mv "$file" "$dir/documents"
       ;;
       *)
       mv "$file" "$dir/others"
       ;;
    esac
  fi
done

echo "Files organized successfully."

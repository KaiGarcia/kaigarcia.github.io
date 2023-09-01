---
layout: project
type: project
image: img/cotton/finder_logo.png
title: "File Organizer"
date: 2023
published: true
labels:
  - Python
  - Scripts
summary: "A simple Python script to organize my files."
---

This Python script allows you to declutter the files in your directories. The script will sort all the files into folders labeled with the file types.
Here is the source code of the script:

<hr>

<pre>
import os
import shutil

#handle input 
pathInput = input("Enter Path to Sort: ")
if pathInput == "Desktop":
    path = "/Users/username/Desktop"
elif pathInput == "Downloads":
    path = "/Users/username/Downloads"
files = os.listdir(path)

for file in files:
    file_name,extension = os.path.splitext(file)

    # Remove the leading period from the extension
    extension = extension[1:]

    path_is_checked_exist = os.path.join(path, extension)

    if not os.path.exists(path_is_checked_exist):
        os.makedirs(path_is_checked_exist)
    
    path_of_file_moved = os.path.join(path,file)
    shutil.move(path_of_file_moved,os.path.join(path_is_checked_exist,file))


</pre>

<hr>

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

After a few months of using the same Macbook for work and school, I have found myself with a crowded and disorganized downloads folder. I wanted to be able to find pdf or image files quickly without having to manually sort and scrape my large downloads folder. My struggle motivated me to write a quick script to solve my problems.

This Python script allows you to declutter the files in your directories. The script will sort all the files into folders labeled with the file types. 

Here is the source code of the script:

<hr>

```python
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

```

<hr>

# 3-Days-Documentation
#Docker installation. a)From docks.docker.com we have downloaded docker(https://docs.docker.com/docker-for-windows/install/). b)After downloaded we got error while installing (Docker desktop requires server services to be enabled) https://www.bing.com/videos/search?view=detail&mid=C12FF81E191DA0CA296AC12FF81E191DA0CA296A&q=docker from using this reference we rectified error. steps for error rectification->in serch type services.msc -> server -> automatic/Manual

2)Creating ubuntu image(http://www.servermom.org/pull-docker-images-run-docker-containers/3225/#:~:text=To%20pull%20an%20image%2C%20use%20%E2%80%9C%20docker%20pull,your%20server%2C%20use%20%E2%80%9C%20docker%20images%20%E2%80%9D%20command) open cmd prompt-> docker pull ubuntu ->docker ps -l ->docker run -i -t ubuntu /bin/bash

3)setup python notebook a)Installing python->https://www.datasciencelearner.com/install-and-run-python-in-docker-container/ ->running ubuntu->docker run -ti -d ubuntu: latest ->To get images ->docker ps ->Updating ubuntu to latest version ->apt-get update ->Install python ->apt-get install python3 ->apt-get install python3 4)open ubuntu in docker and then clc there we have to give 1.sudo ls 2.su - 3.apt-get update 4.apt-get install sudo 5.sudo ls 6.sudo apt update 7.sudo apt install python3-pip python3-dev 8.it will asks do you want to continue [y/n] we should give y to install 9.sudo -H pip3 install --upgrade pip 10.sudo -H pip3 install virtualenv 11.mkdir ~/myproject_dir 12.cd ~/myproject_dir 13.virtualenv myproject_env 14.source myproject_env/bin/activate 15.pip install jupyter jupyter notebook,--allow-root,jupyter notebook --no-browser --port=8888,local:8888these r used but got errors 16.jupyter notebook --allow-root then we got 7)ctrl+c 5)open cmd prompt 1)ssh -L 8888:localhost:8888 root@97e384798831 2)docker run -p 8888:8888 jupyter 3)docker run -p 8888:8888 jupyter/minimal-notebook After that will get localhost link then we have to copy and past that code in browser .

----------------------

#Program for counting words

string =input("Enter :);
#Converts the string into lowercase
string = string.lower();
#Split the string into words using built-in function
words = string.split(" ");
print("Duplicate words in a given string : ");
for i in range(0, len(words)):
count = 1;
for j in range(i+1, len(words)):
if(words[i] == (words[j])):
count = count + 1;
#Set words[j] to 0 to avoid printing visited word
words[j] = "0";
#Displays the duplicate word if count is greater than 1
if(count > 1 and words[i] != "0"):
print(words[i]);

--------------------
# PdfConvertion
 
**Before the code installation:**
```
pip3 install PIL
pip3 install pytesseract
pip3 install pdf2image
sudo apt-get install tesseract-ocr
```
**Code:**
```
from PIL import Image
import pytesseract
import sys
from pdf2image import convert_from_path
import os
 
PDF_file = "new.pdf"                            //opens
pages = convert_from_path(PDF_file, 500)                //counter pages to stores images
image_counter = 1
for page in pages:
    filename = "page_"+str(image_counter)+".jpg"            //save each page
    page.save(filename, 'JPEG')
    image_counter = image_counter + 1
filelimit = image_counter-1
outfile = "out_text.txt"                        //create output file
f = open(outfile, "a")                            //opens in append mode
for i in range(1, filelimit + 1):
    filename = "page_"+str(i)+".jpg"                    
    text = str(((pytesseract.image_to_string(Image.open(filename)))))
    text = text.replace('-\n', '') 
    f.write(text)                            //writes in file
f.close()
```
 

**ERRORS:**
 
Link:https://www.geeksforgeeks.org/python-reading-contents-of-pdf-using-ocr-optical-character-recognition/
 
**To change from jovyan to root:**  (https://github.com/jupyter/docker-stacks/issues/408)     //TO USE SUDO
 
```docker exec -it -u root container_id bash  ``` //no password required
 
**Password issue:**
 
tried url pasting multiple times.
 
**Unable to locate package tesseract-ocr:**(https://github.com/codenvy/codenvy/issues/1068)
```    
    sudo apt-get update
    sudo apt-get install tesseract-ocr         //doesnt work if executed first.
```
**To find number of pages**(https://github.com/Belval/pdf2image/issues/25)
```
    sudo apt-get install -y poppler-utils
```
**Get path:**(https://linuxize.com/post/python-get-change-current-working-directory/#:~:text=To%20find%20the%20current%20working,chdir(path)%20.)
```
import os
os.getcwd()
```

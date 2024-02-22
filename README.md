# File-Handling-in-Python




# To store the data for future purposes:
               Very Less data storage we will go with file systems
               IF we have more amount of data then we prefer to go with DBs


# Types of files:
         Text files - Juypter notebook, program file, log file
         Binary Files - Image or video


# To perform any action on the files:
            Open a file, need to mention the purpose of the opening of the files as well





# open()

f = open(filename, mode)

# The allowed modes in Python:
          1. Read (r) Open an existing file for read operation Default mode
          2. Write (w) Open a file and write something, if data is present already then ,

# it will overwrite the data and
# If the file is not present then it will create one.
           3. Append (a) - It will append the data in the file, if the file is not available then it will create one.
           4. Read and write data (r+) Read and write the data, Previous data will not deleted , file pointer will start at the
              start of the file.
           5. Write and Read (w+) - Write and read, Previous data will be deleted
           6.Append and read (a+) - Append the data and read, It will not overwrite existing data
           7. Exclusive Creation mode for writing operation (x) Fileexist error if it is present






# Closing the file-
    
    f.close()



'''f = open('vikas.txt','w')
print('File name',f.name)
print('File mode',f.mode)
print('File Readable',f.readable())
print('File Writable',f.writable())
print('File closed',f.close())
f.close()
print('File closed',f.close())'''




# How to write the data in the file:
 
  f.write(str)
  f.writelines(list of lines)



'''f = open('vikas.txt','w')
f.write('python looks like an easy programming lan\n')
f.write('Earlier i was very much scared of python\n')
print("Data written successfully")
print('file closed?',f.closed)
f.close()
print('file closed?',f.closed)'''





# Reading character or data from the file.
                 
                 read() -> Read the total data form of file.
                 read(n) -> to read the first n character from the file
                 readline() -> read data line by line one by one
                 readlines() -> Read all the lines into the list



f = open('vikas.txt','r')
data = f.read()
type(data)
print(data)
f.close()




'''f = open('vikas.txt','r')
data = f.read(8)
print(data)
f.close()'''




# tell() - it gives the current position of the pointer

# r+ (start) - At the start of the file
# w+ (start) - Remove the old
# a+ (end) - end of the file




import os
import sys
fname = input("Enter file name : ")
if os.path.isfile(fname):
    print('The file exists',fname)
    f = open(fname,'r')
else:
    print("file does not exists",fname)
    sys.exit(0)
print('the content of the file is')
data = f.read()
print(data)




# Binary files



f1 = open('education.png','rb')
f2 = open('education2.png','wb')
bytes = f1.read()
f2.write(bytes)
print('the new file is created')





# CSV Files


import csv
with open('employee.csv','w',newline= '') as f:
    w = csv.writer(f)
    w.writerow(['ENO','ENAME','ESAL'])
    n = int(input("num of employees: "))
    for i in range(n):
        eno = int(input('Enter employee no: '))
        ename = input('Enter employee name: ')
        esal = float(input("Enter employee sallary: "))
        w.writerow([eno,ename,esal])
print('Total Data Successfully')



# Pickling and Unpickling of the object
# Pickling(writing) - serialization
# UnPickling(reading) - unserialization




import pickle
class Employee:
    def __init__(self,eno,ename,esal):
        self.eno = eno
        self.ename = ename
        self.esal = esal
    def Display(self):
        print(self.eno)
        print(self.ename)
        print(self.esal)
e = Employee(100,'vikas',50000)
e.Display()

with open('emp.dat','wb') as f:
    e = Employee(100, 'vikas', 50000)
    pickle.dump(e,f)
    print('Pickling of the employee object comleted')

with open('emp.dat','rb') as f:
    obj = pickle.load(f)
    print("Employee info after pickling")
    obj.Display()


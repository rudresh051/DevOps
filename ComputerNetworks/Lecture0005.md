# Problem solving on Subnetting(6 Hours)

# Question 9

![alt text](image-86.png)

# Question 10

![alt text](image-87.png)

# Question 11
![alt text](image-88.png)

# Part 1

## Question 1

IP Address = 200.200.200.126  
Subnet Mask = 255.255.255.255.192  
then find Subnet ID and Host ID

![alt text](image-89.png)

## Question 2

![alt text](image-90.png)

## Question 3
Write the 120 as bits value starting from larger values (128, 64, 32, 16, 8, 4, 2, 1)  
And then whichever are common add those value.

Just remember - To find the subnet ID do the bitwise Anding with subnet mask.  
And after that to find the host id , subtract the subnet id from ip value( i.e. 120 - 40 = 80)

![alt text](image-91.png)

## Question 4
Same as above question. Just to the bitwise Anding with Mask address as IP address address is given. You can also use shortcut to quikly write down values and add the common in both(IP address and mask address)

![alt text](image-125.png)


## Important discussion

![alt text](image-126.png)

In above the number 0's indicate Host ID part. therefore HID = 5 bit

**In the above example the above subnet mask can be used for class A, class B or class C. Because in above the number of 1's is greater than 8, greater than 16 and greater than 24. So that's why above subnet mask can be used for class A, class B and Class C**

In the above example from subnet mask, we can't say that subnet ID is of 27 bits. Because default subnet mask of class A is 255.0.0.0 and some extra one's are present we can say the number of bits borrowed for class A.

Similarly default subnet mask of class B is 255.255.0.0 and any extra bits indicate subnet ID but it can also be for class A
Similary default subnet for class C is 255.255.255.0 And any extra bits indicate subnet ID but it can also be for class A , class B and class C


## Question 5

![alt text](image-127.png)

![alt text](image-128.png)

**Shortcut Note - To find the no. of subnet in above find how many extra 1's are present.**

![alt text](image-129.png)


## Question 6
Same as above

![alt text](image-130.png)

## Question 7

![alt text](image-131.png)

For class C subnet to be possible, no of minimum ones required is 24. so subnet for class C is not possible in above.

## Question 8

![alt text](image-132.png)

11111111.11111100.00000000.00000000  

No. of 0's = 18  
therefore Host ID = 18 bit  
No. of IP address/subnet = 2^18  
No. of Host/subnet = 2^18-2   
No. of 1's = 14  

Class A - NID + SID = 14  
8 + Subnet ID = 14  
Subnet ID = 6 bit in class A. therefore no. of subnet in class A = 2^6  

No. of subnet in class B - Not possible. Because minimum number of 1's required for class B is 16 bit.

No. of Subnet in Class C - Not possible. Because minimum number of 1's required in class C is 24 bit.  

## Question 9

![alt text](image-133.png)

Shortcut - Just find how many extra 1's are present. Class is not given in question so we will have two correct answer.

## Question 10

![alt text](image-134.png)

## Question 11

![alt text](image-135.png)

Important - What is the meaning of direct broadcast address? whenever we have all 1's in the host ID part

![alt text](image-136.png)

So in above last 4 bit of HID are zeros. Just find which options have last 4 bit as 1's  and those can be direct broadcast address.

## Question 12

![alt text](image-137.png)

## Question 13

![alt text](image-138.png)


## Question 14

 ![alt text](image-139.png)

 ## Question 15

 




## BIG O Notation

#### Example 1

i) Even if the n is billion, it will only perform three operations.

![image](https://user-images.githubusercontent.com/42731246/162637266-35b017a6-1918-4dab-aa28-57de1709f9f9.png)

---

#### Example 2

ii) As n grows the number of operations does grow

![image](https://user-images.githubusercontent.com/42731246/162637385-b0ad17b6-a9ca-4cda-8b89-7d48ed8c6a21.png)

##### Out of both the one that has less operations executes much faster ,in our case it is Example 1 )

---

![image](https://user-images.githubusercontent.com/42731246/184493479-6b3d8123-1af4-4e6b-a3dd-6b665be7cf26.png)

---

#### Example 3

![image](https://user-images.githubusercontent.com/42731246/184493610-15899491-2a97-49f7-9e86-403773ad636a.png)

---

#### Example 4

![image](https://user-images.githubusercontent.com/42731246/184493630-053d306b-0cf5-43e2-84af-cbf4ab14a05d.png)

---

#### Example 5

![image](https://user-images.githubusercontent.com/42731246/184493793-540d975e-032c-4812-b124-70fb8e3c661a.png)

---

#### Example 6

![image](https://user-images.githubusercontent.com/42731246/184493859-af86e790-ce17-437a-a805-e4ce7004a83e.png)

---

#### Example 7

![image](https://user-images.githubusercontent.com/42731246/184493937-fa76c9da-44ae-4710-951a-1f01b72867d7.png)

---

#### Example 8

![image](https://user-images.githubusercontent.com/42731246/184494018-c0469604-5c77-428b-934b-e133a9ebbaa6.png)

---

# Space Complexity

#### When we talk about space complexity, technically we'll be talking about auxiliary space complexity.

![image](https://user-images.githubusercontent.com/42731246/184494135-fa729954-a88d-4968-ab35-f464d174f514.png)

---

![image](https://user-images.githubusercontent.com/42731246/184494166-78bfa0d8-03a3-46d5-a472-111c3a0c91c1.png)

---

![image](https://user-images.githubusercontent.com/42731246/184494255-ced31d3d-c5f8-4bcc-9422-cda146b03220.png)

---

### Two numbers always take the same space, no matter what is the size of the input

![image](https://user-images.githubusercontent.com/42731246/184494874-fb6af3fa-ba21-4791-99de-2abb426f0116.png)

---

### Our input array is proportional to the output array (space taking up is directly proportional to the N to the input array )

![image](https://user-images.githubusercontent.com/42731246/184495035-2c237376-d83d-43ae-ab16-c7e60654a65d.png)

---

# Objects

![image](https://user-images.githubusercontent.com/42731246/184496590-752b11d5-891f-4098-a1a5-751c4e07561d.png)

---

![image](https://user-images.githubusercontent.com/42731246/184496642-37d5051b-fa30-4e75-95d3-8941922dc0a7.png)

---

![image](https://user-images.githubusercontent.com/42731246/184496666-e67a7bd7-4281-41a7-bd1a-4ca9dcfe3ae5.png)

---

### As the number of keys or values or entries grows then it has to access each and every item (that is the reason it takes O(n) time)

### hasOwnProperty access only one item (and that is the reason it takes O(1) time)

![image](https://user-images.githubusercontent.com/42731246/184496781-e27a2def-c900-4a30-a2e2-90c87e1abe0d.png)

---

# Arrays

![image](https://user-images.githubusercontent.com/42731246/184504310-0ce9d489-2d88-48dc-93e4-650046ea1333.png)

---

![image](https://user-images.githubusercontent.com/42731246/184504546-bad1f449-02b2-49c6-a1c9-c46b335964d3.png)

---

#### Inserting & Removing an element at the start of an array is O(N) time whereas at the end of the Index is O(1)

#### Bcoz we are changing the indices of the entire array by inserting/removing at beginning of the array whereas it is not the case for an element for end of the array

![image](https://user-images.githubusercontent.com/42731246/184504563-f84c6384-b56e-4454-b968-ff112b103220.png)

---

- ### push an element is inserting at the end of the array (O(1) time)

---

- ### pop an element is removing at the end of the array (O(1) time)

---

- ### shift an element is removing at the beginning of the array (re-index the every element in the array) (O(N) time)

---

- ### unshift an element is inserting at the beginning of the array (re-index the every element in the array) (O(N) time)

---

- ### concat is merging two arrays (it is linear proportional to the input size) (O(N) time)

---

- ### slice is taking the copy of the elements of the array (it is linear proportional to the input size) (O(N) time)

---

- ### splice an element is inserting at the beginning or middle of the array (for inserting and re-indexing) (O(N) time)

---

- ### sort sorts the array based on asc or desc (O(NlogN) time)

---

- ### forEach/map/filter/reduce looping through each element of the array (it is linear proportional to the input size) (O(N) time)

---

![image](https://user-images.githubusercontent.com/42731246/184504714-3b6a58dd-5d10-4636-a4df-043f8f254158.png)

---



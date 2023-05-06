Download Link: https://assignmentchef.com/product/solved-eecs-1015-lab-9-revisiting-the-minmaxlist-importing-classes-and-improving-efficiency-assigned
<br>
<strong>LAB 9 – TASK/</strong>

<strong>Lab 9 – Improving MinMaxList efficiency </strong>

<strong>STARTING CODE</strong> – main.py [<a href="https://trinket.io/python/44a3131856">https://trinket.io/python/44a3131856</a><a href="https://trinket.io/python/44a3131856">]</a>

<strong>from MinMaxList import MinMaxList</strong>         # Import MinMaxList from separate file from random import randint




# Main function is given. def main():     aList = MinMaxList([10, 11, 99, 1, 34, 88])




print(“–Insert Item–“)     for i in range(30):

x = randint(1, 100)

aList.insertItem(x, True)                  # You need to modify insertItem (See Task 2)




print(“–Get Min–“)     for i in range(10):         print(“Min item %d ” % aList.getMin() )    # Notice that the getMinMax() method has been changed.

aList.printList()                         # printList() is a new method




print(“–Get Max–“)     for i in range(10):         print(“Max item %d ” % aList.getMax() )    # Notice that the getMinMax() method has been replaced.

aList.printList()                         # printList() is a new method

if __name__ == “__main__”:     main()




<strong>Task 1 – MinMaxList: simple modifications </strong>

<ul>

 <li>Write the code the MinMaxList class in a separate file named “py.” In PyCharm, this should be in the same project and folder as your main.py code. Note that the code above imports the MinMaxList class.</li>

 <li>Modify the MinMaxList class (— see Lecture 9— <a href="https://trinket.io/python/19a5baaa92">https://trinket.io/python/19a5baaa92</a> ) as follows:</li>

</ul>

Remove the getMinMax() and replace it with two methods as follows (see code above too that calls these methods):

getMin() – returns the minimum item from the list, deletes the item from the list. getMax()  – returns the maximum item from the list, deletes the item from the list.

<ul>

 <li>Add a new method called printList printList() – prints the instance variable storing the list</li>

</ul>




<strong>See next page for Task 2 – Making insert more efficient </strong>

<strong>Task 2: Making MinMaxList more efficient by modifying the insertItem() method </strong>

The current implementation of the MinMaxList is to perform a sort() in the constructor and when an item is inserted.   For the constructor, apply sort() reasonable.

The current implementation of insertItem() is as follows:   def insertItem(self, item):     self.listData.append(item)     self.listData.sort()




For inserting an item into an already sorted list, the current approach is <em>highly inefficient</em>.  The time complexity of a sort() algorithm is O(nlogn) (this means, n * log(n)), which is slower than O(n).   We can modify insertItem() to have a time-complexity of O(n) by searching the list for the correct location to insert the item.  Recall that a list object has a method called “insert(index, item)” to insert an item at a particular index.




You need to make two modification to insertItem().  The first is to remove the sort, the second is to allow the method to printout information regarding how your insertion worked.

<strong>Modification #1</strong> – do not use sort, instead, find the correct location to insert the item

<strong>Pseudo-code for performing the insertion:</strong> <strong>if </strong>the List is empty

Append item to end of the List (same as adding item to the list) <strong>else</strong> if item &gt;= last element in the List:     Append item to end of the List

<strong>otherwise</strong>

<em>Find the appropriate index in the list to    </em>

<em>   insert the new item.</em>

<ul>

 <li>Start by setting the index to 0.</li>

 <li>Add one to the index if the item is larger than the current position.</li>

 <li>Stop when you find an item is smaller than the element at the current position.    (d) Insert the item at this index to the List.</li>

</ul>

<strong>See diagram on the right</strong> à

<strong>Modification #2 – have insertItem() printout information on your insertion </strong>

insertItem(self, item, printResult=False/True)

Add an additional parameter to allow a print out of where you inserted the item. Your print out should be as follows:

Item (<strong>86</strong>) inserted at location <strong>5</strong><strong>                  # print out the item and location you inserted it</strong> [1, 2, 10, 11, 34, 86, 88, 99, 99]           <strong># print out the the list after insertion</strong>

Note that the provided code above uses this option.




<strong>Sample Output  </strong>

If your MinMaxList is implemented correctly, your <strong>main.py</strong> (provided to you – see above) should work.

An example output is shown below.  Note that the inserted numbers are randomly generated, so your output will look different.

— Insert Item —

Item (99) inserted at location 5

[1, 10, 11, 34, 88, 99, 99]

Item (2) inserted at location 1

[1, 2, 10, 11, 34, 88, 99, 99]

Item (86) inserted at location 5

[1, 2, 10, 11, 34, 86, 88, 99, 99]

Item (83) inserted at location 5

[1, 2, 10, 11, 34, 83, 86, 88, 99, 99]

Item (39) inserted at location 5

[1, 2, 10, 11, 34, 39, 83, 86, 88, 99, 99]

Item (16) inserted at location 4

[1, 2, 10, 11, 16, 34, 39, 83, 86, 88, 99, 99]

Item (81) inserted at location 7

[1, 2, 10, 11, 16, 34, 39, 81, 83, 86, 88, 99, 99]

Item (98) inserted at location 11

[1, 2, 10, 11, 16, 34, 39, 81, 83, 86, 88, 98, 99, 99]

Item (17) inserted at location 5

[1, 2, 10, 11, 16, 17, 34, 39, 81, 83, 86, 88, 98, 99, 99]

Item (78) inserted at location 8

[1, 2, 10, 11, 16, 17, 34, 39, 78, 81, 83, 86, 88, 98, 99, 99]

Item (97) inserted at location 13

[1, 2, 10, 11, 16, 17, 34, 39, 78, 81, 83, 86, 88, 97, 98, 99, 99] <strong>— I SKIPPED A FEW INSERTS —- </strong>

[1, 2, 10, 11, 16, 17, 33, 34, 39, 78, 81, 81, 83, 85, 86, 88, 93, 95, 97, 98, 99, 99] Item (41) inserted at location 9

[1, 2, 10, 11, 16, 17, 33, 34, 39, 41, 78, 81, 81, 83, 85, 86, 88, 93, 95, 97, 98, 99, 99] Item (50) inserted at location 10

[1, 2, 10, 11, 16, 17, 33, 34, 39, 41, 50, 78, 81, 81, 83, 85, 86, 88, 93, 95, 97, 98, 99, 99] Item (24) inserted at location 6

[1, 2, 10, 11, 16, 17, 24, 33, 34, 39, 41, 50, 78, 81, 81, 83, 85, 86, 88, 93, 95, 97, 98, 99, 99] Item (24) inserted at location 6

[1, 2, 10, 11, 16, 17, 24, 24, 33, 34, 39, 41, 50, 78, 81, 81, 83, 85, 86, 88, 93, 95, 97, 98, 99, 99]

— Get Min —

Min item 1

[2, 10, 11, 16, 17, 24, 24, 33, 34, 39, 41, 50, 78, 81, 81, 83, 85, 86, 88, 93, 95, 97, 98, 99, 99] Min item 2

[10, 11, 16, 17, 24, 24, 33, 34, 39, 41, 50, 78, 81, 81, 83, 85, 86, 88, 93, 95, 97, 98, 99, 99] Min item 10

[11, 16, 17, 24, 24, 33, 34, 39, 41, 50, 78, 81, 81, 83, 85, 86, 88, 93, 95, 97, 98, 99, 99] Min item 11

[16, 17, 24, 24, 33, 34, 39, 41, 50, 78, 81, 81, 83, 85, 86, 88, 93, 95, 97, 98, 99, 99] Min item 16

[17, 24, 24, 33, 34, 39, 41, 50, 78, 81, 81, 83, 85, 86, 88, 93, 95, 97, 98, 99, 99] Min item 17

[24, 24, 33, 34, 39, 41, 50, 78, 81, 81, 83, 85, 86, 88, 93, 95, 97, 98, 99, 99] Min item 24

[24, 33, 34, 39, 41, 50, 78, 81, 81, 83, 85, 86, 88, 93, 95, 97, 98, 99, 99] Min item 24

[33, 34, 39, 41, 50, 78, 81, 81, 83, 85, 86, 88, 93, 95, 97, 98, 99, 99] Min item 33

[34, 39, 41, 50, 78, 81, 81, 83, 85, 86, 88, 93, 95, 97, 98, 99, 99] Min item 34

[39, 41, 50, 78, 81, 81, 83, 85, 86, 88, 93, 95, 97, 98, 99, 99] — Get Max —

Max item 99

[39, 41, 50, 78, 81, 81, 83, 85, 86, 88, 93, 95, 97, 98, 99] Max item 99

[39, 41, 50, 78, 81, 81, 83, 85, 86, 88, 93, 95, 97, 98]

Max item 98

[39, 41, 50, 78, 81, 81, 83, 85, 86, 88, 93, 95, 97]

Max item 97

[39, 41, 50, 78, 81, 81, 83, 85, 86, 88, 93, 95]

Max item 95

[39, 41, 50, 78, 81, 81, 83, 85, 86, 88, 93]

Max item 93

[39, 41, 50, 78, 81, 81, 83, 85, 86, 88]

Max item 88

[39, 41, 50, 78, 81, 81, 83, 85, 86]

Max item 86

[39, 41, 50, 78, 81, 81, 83, 85]

Max item 85

[39, 41, 50, 78, 81, 81, 83]

Max item 83

[39, 41, 50, 78, 81, 81]















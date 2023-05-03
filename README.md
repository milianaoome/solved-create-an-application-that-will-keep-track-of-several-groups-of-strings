Download Link: https://assignmentchef.com/product/solved-create-an-application-that-will-keep-track-of-several-groups-of-strings
<br>
Create an application that will keep track of several groups of strings. Each string will be a member of exactly one group. We would like to be able to see whether two strings are in the same group as well as perform a union of two groups. Use a linked structure to represent a group of strings. Each node in the structure contains a string and a reference to another node in the group. For example, the group {“a”, “b”, “d”, “e”} is represented by the following structure:

<img decoding="async" data-recalc-dims="1" data-src="https://i0.wp.com/www.ankitcodinghub.com/wp-content/uploads/2017/05/675.png?w=980&amp;ssl=1" class="aligncenter lazyload" src="data:image/gif;base64,R0lGODlhAQABAAAAACH5BAEKAAEALAAAAAABAAEAAAICTAEAOw==">

 <noscript>

  <img decoding="async" class="aligncenter" src="https://i0.wp.com/www.ankitcodinghub.com/wp-content/uploads/2017/05/675.png?w=980&amp;ssl=1" data-recalc-dims="1">

 </noscript>

One string in each group—”d” in our example—is in a node that has a null reference. That is, it does not reference any other node in the structure. This string is the representative string of the group. Create the class GroupHolder to represent all of the groups and to perform operations on them. It should have the private instance variable items to hold the nodes that belong to all of the groups. The nodes within each group are linked together as described previously. Make items an instance of ArrayList whose base type is GroupNode, where GroupNode is a private inner class of GroupHolder. GroupNode has the following private instance variables:

<ul>

 <li>data—a string</li>

 <li>link—a reference to another node in the group, or null</li>

</ul>




Define the following methods in the class GroupHolder:

<ul>

 <li>addItem(s)—adds a string s to an empty group. First search items for s; if you find s, do nothing; if you do not find s, create a new GroupNode object that has s as its string and null as its link and add it to items. The new group will contain only the item s.</li>

 <li>getRepresentative(s)—returns the representative string for the group containing s. To find the representative string, search items for s. If you do not find s, return null. If you find s, follow links until you find a null reference. The string in that node is the representative string for the group.</li>

 <li>getAllRepresentatives—returns an instance of ArrayList that contains the representative strings of all the groups in this instance of GroupHolder. (A representative string is in an instance of GroupNode that contains a null reference.)</li>

 <li>inSameGroup(s1, s2)—returns true if the representative string for s1 and the representative string for s2 are the same and not null, in which case the strings s1 and s2 are in the same group.</li>

 <li>union(s1, s2)—forms the union of the groups to which s1 and s2 belong. (Hint: Find the representative strings for s1 and s2. If they are different and neither is null, make the link of the node containing s1’s representative string reference the node for s2’s representative string.)</li>

</ul>

For example, suppose that we call addItem with each of the following strings as an argument: “a”,”b”,”c”,”d”,”e”,”f”,”g”, and “h”. Next, let’s form groups by using these union operations:

union(“a”, “d”), union(“b”, “d”), union(“e”, “b”), union(“h”, “f”)




We will have four groups—{“a”, “b”, “d”, “e”}, {“c”}, {“f”, “h”}, and {“g”}—represented by the following structure:

<img decoding="async" data-recalc-dims="1" data-src="https://i0.wp.com/www.ankitcodinghub.com/wp-content/uploads/2017/05/518.png?w=980&amp;ssl=1" class="lazyload" src="data:image/gif;base64,R0lGODlhAQABAAAAACH5BAEKAAEALAAAAAABAAEAAAICTAEAOw==">

 <noscript>

  <img decoding="async" src="https://i0.wp.com/www.ankitcodinghub.com/wp-content/uploads/2017/05/518.png?w=980&amp;ssl=1" data-recalc-dims="1">

 </noscript>




The representative strings for these four groups are “d”,”c”,”f”, and “g”, respectively. Now the operation inSameSet(“a”, “e”) would return true because both getRepresentative(“a”) and getRepresentative(“e”) return d. Also, inSameSet(“a”, “f”) would return false because getRepresentative(“a”) returns d and getRepresentative(“f”) returns f. The operation union(“a”, “f”) would make the node containing the representative string of the group to which “a” belongs—which is “d”—reference the node containing the representative string of the group to which “f” belongs, which is “f”. This reference would be represented by an arrow from “d” to “f” in the previous diagram.




Your application should create an instance of GroupHolder and allow the user to add an arbitrary number of strings, each to its own group. It should then perform an arbitrary number of union operations to form several groups. Finally, it should demonstrate the other operations.



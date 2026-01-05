C#-and-.NET-concepts<br>
This Repository will have project and some concepts of C# and .NET along with interview questions<br>

Some Features of C#<br>
- It has an inbuilt garbage collector that is managed by CLR(common language runtime)<br>
- It is not cross platform which means it require .NET Framework to run<br>

Q What is CLR<br>
A CLR stands for Common language runtime it is a virtual machine component in .NET Framework. It provides the runtime env for execution of code and makes it simple by providing services like memory management, type safety and thread management

Q what is use of ref in C#<br>
A Ref keyword is used to pass argument value by reference(argument is need to be defined before passing)

Q what is out keyword<br>
A It is not necessary to define before passing, it is used to pass argument to method by reference type, it is mainly used when we are returning multiple values.<br>

Q what is different between const and ReadOnly<br>
A The const keyword is used to declare a constant field. The value is assigned to const field at time of declaration only and its value cannot be modified. While in readonly the value could be intiliased either inside constuctor of a class or at declaration.

Q What is Jagged Array?<br>
A Jagged Array is multi dimensional array with fixed row size or it is array of array with each array of being a vivid length<br>
<i>Initilisation</i>- int[][] arr = new int[3][];

Q What is Tuples<br>
A Tuples are similar to array but they are stored they can hold diff datatype values. They can hold uptill max 8 values. 
<i>Initilization</i> Tuple<int,string,int>tp = new Tuple<int, string, int>(1,"wef",5);



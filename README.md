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

Q What is JIT<br>
A JIT stands for just in time it is part of clr and helps in executing the code written in .NET language. Language specific compiler comvert the code in intermediate language from where JIT converts it into machine understandable form

Q What is Garbage Collector<br>
A Garbage Collector is used for automatic memory management. It work on managed heap. Garbage Collection happen when atleast one of this is cleared
<ul>
  <li>
    System has low physical memory
  </li>
  <li>When memory in the heap memory exceeds the exsisting threshold</li>
  <li>GC.Collect method is called</li>
</ul>

Q What is Namespace<br>
A It is a way of keeping one set of name(classes, struct and interfaces) different from another set of name. The major adv of this is same class name defined in different namespace dont clash with each other. Classes having common feature must be declared under same name space.<br>
<b> ex</b>
<ul>
  <li>namespace first {<br>
class animal{}
}
  </li>
<li>
  System.Console.WriteLine();
</li>
</ul><br>
Q What is use of "using keyword"<br>
A using provides the way of specifying which namespace is being used. We dont need to use namespace.class combination again and again. By "using " we can directly access the class of the namespace<br>

Q What is use of String.Text.StringBuilder<br>
A Inorder to make a muttable string we use StringBuilder. If we would be using System.String and we try to edit a string it will create a new object in the heap memory 

Q What is sealed class<br>
A Sealed keyword is used to restrict the user from inheriting the class. A method can also be sealed but in order to seal it we need to declare it as virtual in base class. Sealed method can not be overloaded.<br>
<p>
  Q What is virtual method<br>
  A Virtual Methdo is used to implement the polymorphirm. The virtual method is always need to be declared in the base class. All virtual method are not need to be overridden in the child class. Override keyword is used to override the virtual method
</p>

Q What are access modifiers<br>
A These are used to set the accessibility of members, methods of the class, class as well. There are 4 type of accessmodifiers that are private, public, protected and internal.
<p>
  Q what is delegate<br>
  A Delegate are wrapper around a method in place of calling method directly it allows us to invoke it dynamically
</p>
<p>Q What is Static Class<br>
A Static class cannot be initialised and contain only static members. Static keyword is used to define a static class along with it we can directly use it by name in place of instance</p>
<p>
  Q Explain the concept of nullable type<br>
  A It is used to allow nullable value + normal range of values. It is defined using ? operator.<br>
  Ex int ? x = null;<br>
  HasValue is used to to determine if value is null or not. ex x.HasValue<br>
  x.Value is used to fetch the value out of nullable variable.<br>
  null-coalescing operator ?? - int value = nullableInt ?? 0; // Use 0 if nullableInt is null<br>
Nullable types are especially handy in scenarios where a value might be absent, such as optional parameters or database fields.
</p>

Q What is difference B/w managed and unmanaged code<br>
A .NET code can be managed and unmanaged depending upon the how it is run in CLR
<h4> Managed Code </h4>
When we write code in C# it is run inside CLR. CLR takes care of memeory management, security and exception handling. We dont have to worry about the memory allocation and freeing up space.

<h4> Unmanaged code</h4>
The code that is written outside the CLR is unmanaged code. Developer need to take care of memory management manually. It might be effecient in some cases but come with greater rish ok crashes, memory leak and security vunerability.

Q How Garbage collection works.
A Garbage collector is part of CLR and responsible for the memory management
<ul>
  <li>
    it scans the memory to identify which object is still in use
  </li>
  <li>
    it sweeps through memory to free up the space
  </li>
  <li>
    it reorganises the momory to avoid the fregmentation
  </li>
</ul>

Q What is LINQ ?
A It stands for <b>Language Integrated Query</b> It is feature of C# which allows us to filter, transform data in by help of sql like syntax without looping over the XML, collection of database.

Q Does garbage collector afftects performance
A <b>Yes</b> it might temporary pause the execution when run. to avoid it take following steps
<ul>
  <li>
    use of structure instead of class for smaller objects
  </li>
  <li>
    reusing the same object instead of making the new one whereever possible
  </li>
  <li>
    Making smaller objects becoz larger one are treated differently
  </li>
</ul>

<b>Note:</b> In ASP.NET middleware are registered using the program.cs file

Q What is DI
A In real time scenarios a class may require an object of other class for example there is class named orderservice which has an attribute of class paymenttype so making instance of paymenttype when creating object for orderservice make it tightly copuled.<br>
Thats when Dependency injection comes into picture

public class OrderService
{
    private PaymentService _paymentService = new PaymentService(); // Hardcoded dependency

    public void ProcessOrder()
    {
        _paymentService.ProcessPayment();
    }
}


public class OrderService
{
    private readonly IPaymentService _paymentService;

    public OrderService(IPaymentService paymentService) // Injecting dependency
    {
        _paymentService = paymentService;
    }

    public void ProcessOrder()
    {
        _paymentService.ProcessPayment();
    }
}

<b>NOTE</b>here dependency can be set by the help of constructor AND  classes depends on interface rather than full implementation of a class.

<b>Note</b> ASP.NET automatically implements the dependency injection by the help of Program.cs file


Example
Step 1️⃣ Create an interface
public interface IPaymentService
{
    void Pay();
}<br>
Step 2️⃣ Implement the interface
public class CreditCardPaymentService : IPaymentService
{
    public void Pay()
    {
        Console.WriteLine("Payment done using Credit Card");
    }
}

public class UpiPaymentService : IPaymentService
{
    public void Pay()
    {
        Console.WriteLine("Payment done using UPI");
    }
}<br>
Step 3️⃣ Use interface in the dependent class
public class OrderService
{
    private readonly IPaymentService _paymentService;

    public OrderService(IPaymentService paymentService)
    {
        _paymentService = paymentService;
    }

    public void PlaceOrder()
    {
        _paymentService.Pay();
    }
}<br>
Step 4️⃣ Register dependency (ASP.NET Core)
builder.Services.AddScoped<IPaymentService, CreditCardPaymentService>();

Q What is serialization
A It is process of converting object into the stream of byte. We can recreate the ibject from it whenever needed that process is called deserialization. I have used the xml serialization i.e is storing data in the xml format.

Q What is upcasting
A converting the child class object into the parent class reference. Meaning in memory it will be stored as child class only but can be referred as parent. But miraculously runtime polymorphismm can be implemented<br>
class Animal{
public void eat(){Console.WriteLine("fhgcgh")}

public virtual void sound(){Console.WriteLine("this is any sound")}; 
}

class dog : Animal{
public overridevoid sound(){Console.WriteLine("bark")}
}

Animal ani  = new dog();
ani.eat();
ani.sound();// output bark

<u>Benefits of Upcasting</u>
<ul>
  <li>
    Loose Coupling
  </li>
  <li>
    helps to implement the DI
  </li>
</ul>








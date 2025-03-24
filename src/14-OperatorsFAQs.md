we can use new operator to create an object if we know classname at the begining 

Test t = new Test();
Student s = new Student();
Customer c = new Customer();


newInstance is a method in class Class , we can use newInstacne method to crrate an object 
if we dont know classname at the begining and it is avilabe dynamically at runtime 

class Student
{
}
class Customer
{
}
class Test
{
        public static void main(String[] args) throws Exception
        {
                Object o = Class.forName(args[0]).newInstance();
                System.out.println("Object created for:"+
                o.getClass().getName());
        }
}


C:\durga_classes>javac Test.java
C:\durga_classes>java Test Student
object created for:Student
C:\durga_classes>java Test Customer
object created for:Customer
C:\durga_classes>java Test java.lang.String
object created for:java.lang.String
C:\durga_classes>_


one scenario where newInstacnce methos is used:

web container use internally newInstance method until runtime web container dont know for which method we have to create an object for servlet 



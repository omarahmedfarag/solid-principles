SOLID stands for:
•	S - Single-responsibility
•	O - Open-closed 
•	L - Liskov Substitution 
•	I - Interface Segregation 
•	D - Dependency Inversion 

******************************************************************
# 1-Single-responsibility :- 
  A class should have one and only one reason to change, meaning that a class should have only one job
  
Example :
![image](https://user-images.githubusercontent.com/45467325/198904679-467e6547-5a04-4561-b488-8ead87edb2d0.png)
![image](https://user-images.githubusercontent.com/45467325/198904687-5dce76ff-02ba-4036-8914-06bc5af6e98e.png)
![image](https://user-images.githubusercontent.com/45467325/198904693-a3f6dce4-123a-4e1c-b3d9-3cd907ccf92c.png)

Can you guess the problem here ? : hint (the problem will be with output ) 

!! The problem with the output method is that the AreaCalculator handles the logic to output the data.
Consider a scenario where the output should be converted to another format like JSON.
All of the logic would be handled by the AreaCalculator class. This would violate the single-responsibility principle. The AreaCalculator class should only be concerned with the sum of the areas of provided shapes. It should not care whether the user wants JSON or HTML


@ Now we will Apply Single-responsibility

![image](https://user-images.githubusercontent.com/45467325/198904749-a8078ebb-ddcd-429a-a930-26d3f623307f.png)
![image](https://user-images.githubusercontent.com/45467325/198904907-8b7e4cbe-9d06-49ea-992d-65214438a788.png)

*******************************************************************
# 2- Open-Closed Principle
  Objects or entities should be open for extension but closed for modification.
  
  
Example
![image](https://user-images.githubusercontent.com/45467325/198905002-2c5bcadf-56ff-4b7d-a965-75e1d130035b.png)

 
Can you guss the problem ?  : hint (the problem with the in a specific senario sum method)

!! Consider a scenario where the user would like the sum of additional shapes like triangles, pentagons, hexagons, etc. You would have to constantly edit this file and add more if/else blocks. That would violate the open-closed principle.
  
Solution - > A way you can make this sum method better is to remove the logic to calculate the area of each shape out of the AreaCalculator class method and attach it to each shape’s class.

![image](https://user-images.githubusercontent.com/45467325/198905187-d2ebb02b-60bd-4416-a64c-5691de8ac0a6.png) ![image](https://user-images.githubusercontent.com/45467325/198905207-a7b10a9b-2f3a-48f5-b778-554153277fc9.png)

![image](https://user-images.githubusercontent.com/45467325/198905229-a58020ae-fe5b-4876-ba4c-97f80901caba.png)

Now, you can create another shape class and pass it in when calculating the sum without breaking the code.

However, another problem arises. How do you know that the object passed into the AreaCalculator is actually a shape or if the shape has a method named area?
![image](https://user-images.githubusercontent.com/45467325/198995872-28e17559-fa81-4a9d-8fb1-ff6ac3842581.png)
![image](https://user-images.githubusercontent.com/45467325/198995903-40fef3a2-369e-4357-a19a-9b783d1f8301.png)



********************************************************************
# 3- Liskov Substitution Principle
  This means that every subclass or derived class should be substitutable for their base or parent class.
  
Example 
![image](https://user-images.githubusercontent.com/45467325/198905548-5f82bdf1-f962-47b7-b52c-25c980222eb0.png)
![image](https://user-images.githubusercontent.com/45467325/198905557-b6376d5f-6a18-4e27-b731-f6e4172f45b7.png)
![image](https://user-images.githubusercontent.com/45467325/198905571-fe1d9753-14eb-467b-9acd-efdd0b49c97c.png)

Can you guss the problem ?  : hint (the problem with the output)

!! When you call the HTML method on the $output2 object, you will get an E_NOTICE error informing you of an array to string conversion.

Solution - > To fix this, instead of returning an array from the VolumeCalculator class sum method, return $summedData:
![image](https://user-images.githubusercontent.com/45467325/198905640-f280eb0b-bd56-4682-ab4a-1f09190a7e16.png)

*********************************************************************
# 4- Interface Segregation Principle
  A client should never be forced to implement an interface that it doesn’t use, or clients shouldn’t be forced to depend on methods they do not use.
  
Example 
Still building from the previous ShapeInterface example, you will need to support the new three-dimensional shapes of Cuboid and Spheroid, and these shapes will need to also calculate volume.

![image](https://user-images.githubusercontent.com/45467325/198996263-50ae843a-acfb-4819-9c27-7361bd0084cd.png)

Can you guss the problem ? : hint (the problem with the volum function)

Now, any shape you create must implement the volume method, but you know that squares are flat shapes and that they do not have volumes, so this interface would force the Square class to implement a method that it has no use of.

This would violate the interface segregation principle. Instead, you could create another interface called ThreeDimensionalShapeInterface that has the volume contract and three-dimensional shapes can implement this interface:

![image](https://user-images.githubusercontent.com/45467325/198996390-098d09b0-e8b8-498e-a978-bef091c22305.png)

**********************************************************************
# 5- Dependency Inversion Principle
  Entities must depend on abstractions, not on concretions. It states that the high-level module must not depend on the low-level module, but they should depend on       abstractions.
  --This principle allows for decoupling.
  
Example 
 
Here is an example of a PasswordReminder that connects to a MySQL database:
![image](https://user-images.githubusercontent.com/45467325/198998143-79f7709a-201b-49fc-8112-214eba8a7a63.png)

First, the MySQLConnection is the low-level module while the PasswordReminder is high level, but according to the definition of D in SOLID, which states to Depend on abstraction, not on concretions. This snippet above violates this principle as the PasswordReminder class is being forced to depend on the MySQLConnection class.

Later, if you were to change the database engine, you would also have to edit the PasswordReminder class, and this would violate the open-close principle.

The PasswordReminder class should not care what database your application uses. To address these issues, you can code to an interface since high-level and low-level modules should depend on abstraction:

![image](https://user-images.githubusercontent.com/45467325/198998207-59f89a4e-ef51-4b2d-bcf5-d3cee0a72e6f.png)

The interface has a connect method and the MySQLConnection class implements this interface. Also, instead of directly type-hinting MySQLConnection class in the constructor of the PasswordReminder, you instead type-hint the DBConnectionInterface and no matter the type of database your application uses, the PasswordReminder class can connect to the database without any problems and open-close principle is not violated.

![image](https://user-images.githubusercontent.com/45467325/198998407-3037f32f-d8c5-4827-8fd7-5c609f02edc3.png)

# Conclusion
In this article, you were presented with the five principles of SOLID Code. Projects that adhere to SOLID principles can be shared with collaborators, extended, modified, tested, and refactored with fewer complications.

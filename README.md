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



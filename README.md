SOLID stands for:
•	S - Single-responsibility
•	O - Open-closed 
•	L - Liskov Substitution 
•	I - Interface Segregation 
•	D - Dependency Inversion 

******************************************************************
1-Single-responsibility :- 
  A class should have one and only one reason to change, meaning that a class should have only one job
  
Example :
![image](https://user-images.githubusercontent.com/45467325/198904679-467e6547-5a04-4561-b488-8ead87edb2d0.png)
![image](https://user-images.githubusercontent.com/45467325/198904687-5dce76ff-02ba-4036-8914-06bc5af6e98e.png)
![image](https://user-images.githubusercontent.com/45467325/198904693-a3f6dce4-123a-4e1c-b3d9-3cd907ccf92c.png)

Can you guess the problem here ? : hint (the problem will be with output the output ) 

!! The problem with the output method is that the AreaCalculator handles the logic to output the data.
Consider a scenario where the output should be converted to another format like JSON.
All of the logic would be handled by the AreaCalculator class. This would violate the single-responsibility principle. The AreaCalculator class should only be concerned with the sum of the areas of provided shapes. It should not care whether the user wants JSON or HTML


### Now we will Apply Single-responsibility

![image](https://user-images.githubusercontent.com/45467325/198904749-a8078ebb-ddcd-429a-a930-26d3f623307f.png)


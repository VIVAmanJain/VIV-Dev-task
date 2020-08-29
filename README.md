# **Full-stack developer task**

**General Suggestions:**

- Read the task completely before you start writing code.
- Make sensible comments throughout your code.
- Document all the progress that you have made by creating a separate markdown file called DOCUMENT.md
- In order to start with the task, do the following:
  - Fork this repo
  - Clone it on your personal device
  - Create a new branch with the following name, viv_<your_name>
  - All the code that you write should be on that branch
  - Push it to your fork
  - Then create a pull request to the original repository

**Backend**

Your task involves designing and implementing a warehouse management web application using Node.js and MongoDB (Create a well-defined database structure and implement it in the models.). The system should have the following features:
  1. An single authentication system which has different categories of users, namely:
        - Facility Head
        - Corporate manager
        - Assembly line supervisor
        - Warehouse worker

        Each user has a profile image and other parameters can be chosen as candidate finds suitable. The users will have features accessible to them based on the category they belong to.

  1. **(Facility head and Assembly line supervisor)** The warehouse has different types of products. The company wants a record of all the products. This job was allocated to the facility head and assembly line supervisor. Create REST APIs for adding items to the database. Choose parameters for items as you find suitable but note that each item must have
       1. An image for the item, assign a default image in case an image is not provided.
       2. Unique item id for each new item **(UUID)**
  2. **(Facility head and Assembly line supervisor)** Warehouse level management allot stations to workers daily. Create REST APIs to allot stations to workers on daily basis. This helps corporate management analyse productivity of workers individually.
  3. **(Assembly line workers)** Assembly line workers scan items every time they move the items from one station to another. For simplicity let&#39;s assume there are only 4 locations in the warehouse:
     1. Entry station
     2. 2 storage stations
     3. Exit station

        For every station there are two processes which are to be logged, i.e., exit and entry. This means there are only 8 possible actions (4 stations \* 2 actions per station).
  
      _Here&#39;s the caveat,_

        - An item id that is already in the warehouse cannot be scanned by the system twice
        - An item that has not been scanned at the entry spot of any station, cannot be exited.

      _Your task is to create backend for the logging system. Let&#39;s assume that the worker will scan every item from an edge device. The edge device will send request to the system with the following data:_

      - Station Id
      - Quantity
      - Item Id
      - Timestamp

      _You have to add the allotted worker to each log in the backend. These logs will be viewed later by the corporate management to analyse the working of the warehouse._

  4. **(Corporate manager)** Corporate managers are not interested in the daily working of the warehouse. But they are interested in the data. Create APIs for corporate managers to:
   
      i. Track every item just by the item id.

      ii. View actions performed by every worker.
      
      iii. API to retrieve logs.
      
      iv. Retrieve log data in csv format.
      
      v. View inventory of each item available in the warehouse.

**Brownie Points:**

  1. Write up on the ideal system architecture and the design of API given enough time and resources.
  2. Write tests for the system that you have implemented as you deem suitable.
  3. Use the async functionality provided by node.js. Moreover, in your document write where and why you have used the same.

**DevOps**

1. Now that you have completed making the backend it&#39;s time for deployment. Now your code may work perfectly on your system but while running it on my system I might face unforeseen errors. We want to avoid that. Hence, we will use a tool called docker (and docker compose). Dockerize your application with the following things in mind.

  1. Default express server is fine for development. But when deploying in production we use are different server for serving our application like nginx and apache server. For this task we shall use **nginx**. While dockerizing your application use an nginx image along with your backend application.
  2. Use docker volumes in order to manage your MongoDB database.
  3. Combine all these services using docker compose.

**Front-end**

At Variety Innovation Ventures, **react** is our frontend framework of choice. Hence, we expect you to use it as well. For the front-end part of the task, design and implement the corporate management portal. This portal will be used by the corporate management in order to track the work done in the warehouse.

Fairly, straight-forward right?

Now the tricky part, after creating this basic visualization, you need to create some charts and graphs that depict a story and are useful for the end-user. For example, you could show the amount of scanning that is done at each location or implement an interesting design to track items.

Remember, Design Matters!!

**Note:**

  - Although we expect you to use react, if you are more comfortable with some other framework go ahead with that.
  - You may use chart.js for creating interactive charts

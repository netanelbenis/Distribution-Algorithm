<p align="center">
  <img src="https://user-images.githubusercontent.com/44754325/78273213-36a98b80-7517-11ea-8f8e-fb9b8e569988.png">
</p>

# Distribution Algorithm

A web application for fairly dividing goods among people with different valuations.

The [front-end](demoWeb/) allows each person to specify how much he/she values each of the goods.
The data is then sent to the [server](server/).
It runs an [algorithm](server/algorithm) that computes an allocation of the goods among the people.
The algorithm guarantees the following properties:

1. **Fairness**: each agent receives goods with a value of at least 1/n of his/her valuation of all goods.

2. **Pareto Efficiency**: there is no other allocation that is at least as good for all agents and better for at least one agent.

3. **Minimal sharing**: subject to fairness and efficiency, the allocation minimizes the number of sharings of goods between two or more people.
I.e., if there is a fair and efficient allocation with no sharing at all - it will be returned.
Otherwise, if there is a fair and efficient allocation with only one sharing (one good is shared between two people) - it will be returned. And so on.


# Server Installation

**NOTE: in our development process we are using python 3.6.9**

Since the root user is the most powerful, essentially a root user can do everything on the server, so we may want to limit access to it to improve security.You can create a new user and configure it to "act like" a root user but with certain limitations, and we will log in as this user from then on. It is highly recommended to do so, but if you choose not to follow this practice and simply want to login as the root user, continue the guide, otherwise see the CreateUser.md guide.


## Debug Server  

First, we need to set a virtual environment and install the server dependencies.                            
Go into **server/** folder.
Run the following command and replace the parameter `` <password> ``  with your user password.

```
./app.sh build <password>
```

Go into **server/** folder 
and run the following command.

```
./app.sh
```
Now that the server deployed using Flask and Flask-RESTful, access the default Server landing page to confirm that the software is running properly through this URL:

```
  http://127.0.0.1:5000
```
## Production Server 

It is highly recommended to run the Debug server, and check whether everything works before installing the Production Server . 

Go into the **server/** folder.                                             
Run the following command and replace the `` <password> `` parameter with your user password and the  ``` <user> ```  parameter with your ubuntu username .  
(TIP: to find your ubuntu user name run the command  ``whoami``  )

```
./deployServer <password> <user>
```
Now that the server deployed using Nginx and uWSGI,  
access the default Server landing page to confirm that the software is running properly through your IP address:
(TIP: to find your IP run the command  ``ifconfig``  )

```
  http://your_ip
```

# Running the Algorithm Directly

The algorithm can be run without the server, e.g. for experiments.
To do this, download the repository, and 
add the [Distribution-Algorithm/server/](Distribution-Algorithm/server/) path to your Python include path.
An example of a Python code for running the algorithm can be found 
[here](server/algorithm/Version3/TestScript.py).

# Contributors

* [Algorithm Programming](server/algorithm/): Eliyahu Satat and Nachshon Satat.
* [Server Programming](server/): Daniel Abergel and Elyashiv Deri.
* [Front-End Programming](demoWeb/): Netanel Ben Issahar.

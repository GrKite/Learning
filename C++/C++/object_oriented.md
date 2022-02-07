# What is an object?

- Object = Entity 

  对象就是东西, 什么是东西? 

- Object may be

  - Visible or
  - invisible

- Object is variable in programming languages. (对象就是变量在程序设计语言)

  - 变量是用来保存数据的, 变量有类型
  - 所有的对象都会以变量的形式存在



## Objects = Attributes + Services

- Data: the properties or status

- Operations: the functions

  ![image-20220111092333321](C:\Users\duoduo.liu\AppData\Roaming\Typora\typora-user-images\image-20220111092333321.png)

因为本身有一些特性，通过接受一些控制来提供一些服务



# Mapping

- From the problem space to the solution one.

  ![image-20220111092640240](C:\Users\duoduo.liu\AppData\Roaming\Typora\typora-user-images\image-20220111092640240.png)

# What is object-oriented

- A way to organize
   - Designs
   - Implementations
- Objects, not control or data flow, are the primary focus of the design and implementation.
- To focus on things, not operations.



# Objects send messages

- Messages are
  - Composed by the sender
  - Interpreted by the receiver
  - Implemented by methods
- Messages
  - May cause receiver to change state
  - May return results

# Object vs. Class

- Objects (cat) 实体
  - Represent things, events, or concepts
  - Respond to messages at run-time
- Classes (cat class) 概念
  - Define properties of instance
  - Act like types in C++

![image-20220111122049184](C:\Users\duoduo.liu\AppData\Roaming\Typora\typora-user-images\image-20220111122049184.png)

![image-20220111122453209](C:\Users\duoduo.liu\AppData\Roaming\Typora\typora-user-images\image-20220111122453209.png)

总是先有类型， 再有对象



# An object has an interface

- The interface is the way it receives messages.
- It is defined in the class the object belong to.

# Functions of the interface

- Communication

- Protection

  耦合性，这个高还是低， 对于这个是非常好的说

# The Hidden Implementation
- Inner part of an object, data members to present its state, and the actions it takes when messages is rcvd is hidden.

- Class creators vs. Client programmers

  - Keep client programmers' hands off portions they should not touch.
  - Allow the class creators to change the internal working of the class without worrying about how it will affect the client programmers.
  
  
  
  
  
# Encapsulation 封装
- bundle data and methods dealing with these data together in an object
- Hide the details of the data and the action.
- Restrict only access to the publicized methods. 
  
  

# DataBases

- Different types of data bases, tables(UserDefaults, Codable, KeyChain) and DatabaseSolutions(SQLite, Core Data, Realm).

| Method | Use |
|:--:|:--:|
| UserDefaults | Quickly persist small bits of data e.g. top score, playerNickname, music on/off |
| Codable | Flash freeze custom objects |
| Keychain API | Save small bits of data securely |
| SQLite | Persist large amounts of daa and query it |
| Core Data | Object-oriented database |
| Realm | A faster and easier database solution |

## Core-Data

- Steps on how to Set up and Configure Core Data using CRUD (Create, Read, Update, Destroy) Operations.

### 1. Set up and Configure Core Data

1. File/New/File and choose Data Model and put in to corresponding Design Pattern folder.
2. Using a CoreDataTest project, copy the funcs (persistentContainer, and saveContext) needed to run the CoreData.
   1. **Important** you must change to match the name of the CoreData file ```NSPersistentContainer(name: "NameCoreDataFile")```
3. Configure CoreData file.
   1. Important keywords:
      1. Entity = Class
      2. Attributes = Properties
   2. Setup Entity and rename it.
   3. Setup the attributes by renaming and setting the dataType we are using to collect the data.
   4. On your entity Data Model Inspector change the Module to Current Project Module
   5. Select what Codegen property you need in the Inspector:
      1. CodegenTypes
         1. Manual/None:
            1. No code will be generated and you must do all the work and code yourself. (Hardly ever used.)
         2. Class Definition:
            1. Default item - it converts the data file into classes and properties to manipulate programmatically in the app. (Easiest to setup and use.)
         3. Category/Extension
            1. Use this if you want to write custom code for you own categories and extensions and manipulate the CoreData files. (Most used out in the wild.)
   6. C (Create) in CRUD using the persistent container and the context that will interact with the app's database.
   7. R (Read) data by fetching the data from the Core Data by requesting data from the entity (**Remember** you MUST specify the dataType of the variable for the request).  The request will fetch from the Core Data and then render the data on the view (**Remember** to load the data to the viewDidLoad with the corresponding function).
   8. U (Updating) data is simple and you can do many thing with data in Core Data, however you **MUST** remember to save the items to context because they will not update the persistent container/Entity/Core Data or SQLite data.
   9. D (Destroy) data is simple with ```context.delete()``` however you must remember to save the context or this line of code will do nothing.  Also **NOTE** if you are needing to delete an item from a viewTable or an array, you **MUST** delete from the database first and then from the array.  The order of the code matters in this instance. 

## Core Data Fundamentals

- Difference in terminology between OOP (Object Oriented Programming), Core Data, and Database.

| OOP World | Core Data World | Database World |
|:--:|:--:|:--:|
| Class | Entity | Table |
| Property | Attribute | Field |

- **NSManagedObject** is the row of each Entity or Table.
- Lets say that we have three entities (Product, Buyers, and Orders), if we put those all into _permanent container_, then that container is the **persistent container** which in essence is a **SQLite database**.
- We cannot talk to or manipulate the data directly with the persistent container, instead we have to go through a temporary area called **Context**.
- Through the context we can Create, Read, Update, or Destroy data hence the CRUD acronym.
- Once you are finished CRUD your data then you save the data with ```context.save()```

## Core Data Relationships


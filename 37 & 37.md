Find all the information about each product

Ans:db.products.find({})

Find the product price which are between 400 to 800

Ans:db.products.find({"product_price":{$gt:400,$lt:600}})

Find the product price which are not between 400 to 600

Ans:db.products.find({"product_price":{$not:{$gt:400,$lt:600}}})

List the four product which are grater than 500 in price 

Ans:db.products.find({"product_price":{$gt:500}}).limit(4)

Find the product name and product material of each products

Ans:db.products.find({},{product_name:1,product_material:1,_id:0})

Find the product with a row id of 10

Ans:db.products.find({"id":"10"})

Find only the product name and product material

Ans:db.products.find({},{product_name:1,product_material:1,_id:0})

Find all products which contain the value of soft in product material 

Ans:db.products.find({"product_material":"Soft"})

Find products which contain product color indigo  and product price 492.00

Ans:db.products.find({"product_color":"indigo","product_price":492.00})

Delete the products which product price value are same

Ans:

db.products.aggregate([
 {
     "$group": {
         _id: "$product_price",
         dups: { $addToSet: "$_id" } ,
         count: { $sum : 1 }
     }
 },
 {
     "$match": {
         count: { "$gt": 1 }
     }
 }
]).forEach(function(doc) {
   db.products.remove({
       _id: {$in: doc.dups}
   });
})

Create DB :

use products

Create collection and add documents:
 
db.products.insertMany([
...     {
...         "id": "1",
...         "product_name": "Intelligent Fresh Chips",
...         "product_price": 655.00,
...         "product_material": "Concrete",
...         "product_color": "mint green"
...     },
...     {
...         "id": "2",
...         "product_name": "Practical Fresh Sausages",
...         "product_price": 911.0,
...         "product_material": "Cotton",
...         "product_color": "indigo"
...     },
...     {
...         "id": "3",
...         "product_name": "Refined Steel Car",
...         "product_price": 690.00,
...         "product_material": "Rubber",
...         "product_color": "gold"
...     },
...     {
...         "id": "4",
...         "product_name": "Gorgeous Plastic Pants",
...         "product_price": 492.00,
...         "product_material": "Soft",
...         "product_color": "plum"
...     },
...     {
...         "id": "5",
...         "product_name": "Sleek Cotton Chair",
...         "product_price": 33.00,
...         "product_material": "Fresh",
...         "product_color": "black"
...     },
...     {
...         "id": "6",
...         "product_name": "Awesome Wooden Towels",
...         "product_price": 474.00,
...         "product_material": "Plastic",
...         "product_color": "orange"
...     },
...     {
...         "id": "7",
...         "product_name": "Practical Soft Shoes",
...         "product_price": 500.00,
...         "product_material": "Rubber",
...         "product_color": "pink"
...     },
...     {
...         "id": "8",
...         "product_name": "Incredible Steel Hat",
...         "product_price": 78.00,
...         "product_material": "Rubber",
...         "product_color": "violet"
...     },
...     {
...         "id": "9",
...         "product_name": "Awesome Wooden Ball",
...         "product_price": 28.00,
...         "product_material": "Soft",
...         "product_color": "azure"
...     },
...     {
...         "id": "10",
...         "product_name": "Generic Wooden Pizza",
...         "product_price": 84.00,
...         "product_material": "Frozen",
...         "product_color": "indigo"
...     },
...     {
...         "id": "11",
...         "product_name": "Unbranded Wooden Cheese",
...         "product_price":26.00,
...         "product_material": "Soft",
...         "product_color": "black"
...     },
...     {
...         "id": "12",
...         "product_name": "Unbranded Plastic Salad",
...         "product_price": 89.00,
...         "product_material": "Wooden",
...         "product_color": "pink"
...     },
...     {
...         "id": "13",
...         "product_name": "Gorgeous Cotton Keyboard",
...         "product_price": 37.00,
...         "product_material": "Concrete",
...         "product_color": "sky blue"
...     },
...     {
...         "id": "14",
...         "product_name": "Incredible Steel Shirt",
...         "product_price": 54.00,
...         "product_material": "Metal",
...         "product_color": "white"
...     },
...     {
...         "id": "15",
...         "product_name": "Ergonomic Cotton Hat",
...         "product_price": 43.00,
...         "product_material": "Rubber",
...         "product_color": "mint green"
...     },
...     {
...         "id": "16",
...         "product_name": "Small Soft Chair",
...         "product_price": 47.00,
...         "product_material": "Cotton",
...         "product_color": "teal"
...     },
...     {
...         "id": "17",
...         "product_name": "Incredible Metal Car",
...         "product_price":36.00,
...         "product_material": "Fresh",
...         "product_color": "indigo"
...     },
...     {
...         "id": "18",
...         "product_name": "Licensed Plastic Bacon",
...         "product_price":88.00,
...         "product_material": "Steel",
...         "product_color": "yellow"
...     },
...     {
...         "id": "19",
...         "product_name": "Intelligent Cotton Chips",
...         "product_price": 46.00,
...         "product_material": "Soft",
...         "product_color": "azure"
...     },
...     {
...         "id": "20",
...         "product_name": "Handcrafted Wooden Bacon",
...         "product_price": 36.00,
...         "product_material": "Concrete",
...         "product_color": "lime"
...     },
...     {
...         "id": "21",
...         "product_name": "Unbranded Granite Chicken",
...         "product_price": 90.00,
...         "product_material": "Metal",
...         "product_color": "gold"
...     },
...     {
...         "id": "22",
...         "product_name": "Ergonomic Soft Hat",
...         "product_price": 99.00,
...         "product_material": "Rubber",
...         "product_color": "black"
...     },
...     {
...         "id": "23",
...         "product_name": "Intelligent Steel Pizza",
...         "product_price": 95.00,
...         "product_material": "Cotton",
...         "product_color": "azure"
...     },
...     {
...         "id": "24",
...         "product_name": "Tasty Rubber Cheese",
...         "product_price":47.00,
...         "product_material": "Frozen",
...         "product_color": "orchid"
...     },
...     {
...         "id": "25",
...         "product_name": "Licensed Steel Car",
...         "product_price":20.00,
...         "product_material": "Cotton",
...         "product_color": "indigo"
...     }
... ])













Find all the topics and tasks which are thought in the month of October

Ans : 
db.topics.aggregate([{
    $lookup: {
            from: "tasks",
            localField: "TOPIC_ID",
            foreignField: "TOPIC_ID",
            as: "tasks"
        }
},
{ 
$match: { "$expr": { "$eq": [{ "$month": "$CLASS_DATE" }, 10] } } 
}])

Find all the company drives which appeared between 15 oct-2022 and 31-oct-2022

db.company_drives.find({DRIVE_DATA:{$gte: ISODate("2022-10-15T00:00:00.000Z"),$lt: ISODate("2022-10-31T00:00:00.000Z")}});

Find all the company drives and students who are appeared for the placement.

db.users.aggregate([{
    $lookup: {
            from: "company_drives",
            localField: "ID",
            foreignField: "USER_ID",
            as: "Drives"
        }
}])


Find the number of problems solved by the user in codekata

db.codekata.aggregate([{
     $lookup:
       {
         from: "users",
         localField: "USER_ID",
         foreignField: "ID",
         as: "user"
       }
  }
  ,{$group:{_id : "$user.STUDENT_NAME", problemsCompleted:{$sum: '$COMPLETED'} }}, 
  {$project :{_id:0,studentName: "$_id", problemsCompleted:1} }])


Find all the mentors with who has the mentee's count more than 15


db.mentors.find({MENTEE_COUNT:{$gt:15}});

Find the number of users who are absent and task is not submitted  between 15 oct-2020 and 31-oct-2020

db.attendance.find({"CLASS_DATE":{$gte: ISODate("2022-10-15T00:00:00.000Z"),$lt: ISODate("2022-10-31T00:00:00.000Z")},"STATUS":"No","TASK_COMPLETED": "No"});


Design database for Zen class programme
users
codekata
attendance
topics
tasks
company_drives
mentors


use Students

db.tasks.insertMany([
  {
    "TOPIC_ID": 1,
    "TASK_ID": 1,
    "TASK_DETAIL": "Create API",
    "CLASS_DATE": "09-01-22"
  },
  {
    "TOPIC_ID": 2,
    "TASK_ID": 2,
    "TASK_DETAIL": "Host API in Heroku",
    "CLASS_DATE": "10-10-22"
  },
  {
    "TOPIC_ID": 3,
    "TASK_ID": 3,
    "TASK_DETAIL": "Create a Expres app",
    "CLASS_DATE": "11-10-21"
  }
]);

db.topics.insertMany([
  {
    "TOPIC_ID": 1,
    "CLASS_TOPIC": "Nodejs & Expressjs",
    "CLASS_DATE": new Date("2022-01-09"),
    "CLASS_CONTENT": "What is express,API methods",
    "CLASS_PREREAD": "https://expressjs.com"
  },
  {
    "TOPIC_ID": 2,
    "CLASS_TOPIC": "Node & mongo DB connectivity",
    "CLASS_DATE": new Date("2021-10-10"),
    "CLASS_CONTENT": "Connection to MongoDB(local & atlas)",
    "CLASS_PREREAD": ""
  },
  {
    "TOPIC_ID": 3,
    "CLASS_TOPIC": "Nodejs deployment",
    "CLASS_DATE": new Date("2021-10-11"),
    "CLASS_CONTENT": "dotenv,Deployment",
    "CLASS_PREREAD": "https://www.npmjs.com/package/dotenv"
  }
]);




db.company_drives.insertMany([
  {
    "DRIVE_ID": 1,
    "COMPANY_NAME": "Zoho",
    "DRIVE_DATA": new Date("2022-01-09"),
    "USER_ID": 1
  },
  {
    "DRIVE_ID": 1,
    "COMPANY_NAME": "Zoho",
    "DRIVE_DATA": new Date("2022-01-09"),
    "USER_ID": 2
  },
  {
    "DRIVE_ID": 1,
    "COMPANY_NAME": "Zoho",
    "DRIVE_DATA": new Date("2022-01-09"),
    "USER_ID": 3
  },
  {
    "DRIVE_ID": 2,
    "COMPANY_NAME": "TCS",
    "DRIVE_DATA": new Date("2022-01-10"),
    "USER_ID": 4
  },
  {
    "DRIVE_ID": 2,
    "COMPANY_NAME": "TCS",
    "DRIVE_DATA": new Date("2022-01-10"),
    "USER_ID": 5
  },
  {
    "DRIVE_ID": 3,
    "COMPANY_NAME": "CTS",
    "DRIVE_DATA": new Date("2022-10-15"),
    "USER_ID": 3
  },
  {
    "DRIVE_ID": 3,
    "COMPANY_NAME": "CTS",
    "DRIVE_DATA": new Date("2022-10-15"),
    "USER_ID": 4
  },
  {
    "DRIVE_ID": 4,
    "COMPANY_NAME": "Accenture",
    "DRIVE_DATA": new Date("2022-10-20"),
    "USER_ID": 1
  },
  {
    "DRIVE_ID": 5,
    "COMPANY_NAME": "Freshwork",
    "DRIVE_DATA": new Date("2022-10-30"),
    "USER_ID": 2
  },
  {
    "DRIVE_ID": 5,
    "COMPANY_NAME": "Freshwork",
    "DRIVE_DATA": new Date("2022-10-30"),
    "USER_ID": 4
  }
]);


db.users.insertMany([
  {
    "ID": 1,
    "STUDENT_NAME": "Vivek",
    "STUDENT_EMAIL": "vivek@gmail.com",
    "GENDER": "Male"
  },
  {
    "ID": 2,
    "STUDENT_NAME": "Balaji",
    "STUDENT_EMAIL": "balaji@gmail.com",
    "GENDER": "Male"
  },
  {
    "ID": 3,
    "STUDENT_NAME": "Shivani",
    "STUDENT_EMAIL": "shivani@gmail.com",
    "GENDER": "Female"
  },
  {
    "ID": 4,
    "STUDENT_NAME": "Megha",
    "STUDENT_EMAIL": "megha@gmail.com",
    "GENDER": "Female"
  },
  {
    "ID": 5,
    "STUDENT_NAME": "Vignesh",
    "STUDENT_EMAIL": "vignesh@gmail.com",
    "GENDER": "Male"
  }
]);

db.codekata.insertMany([
  {
    "USER_ID": 1,
    "PROBLEM_ID": 1,
    "PROBLEM_NAME": "Numbers",
    "COMPLETED": 20,
    "TOTAL": 50
  },
  {
    "USER_ID": 1,
    "PROBLEM_ID": 2,
    "PROBLEM_NAME": "Array",
    "COMPLETED": 2,
    "TOTAL": 30
  },
  {
    "USER_ID": 1,
    "PROBLEM_ID": 3,
    "PROBLEM_NAME": "Strings",
    "COMPLETED": 25,
    "TOTAL": 60
  },
  {
    "USER_ID": 2,
    "PROBLEM_ID": 1,
    "PROBLEM_NAME": "Numbers",
    "COMPLETED": 2,
    "TOTAL": 50
  },
  {
    "USER_ID": 2,
    "PROBLEM_ID": 2,
    "PROBLEM_NAME": "Array",
    "COMPLETED": 20,
    "TOTAL": 30
  },
  {
    "USER_ID": 2,
    "PROBLEM_ID": 3,
    "PROBLEM_NAME": "Strings",
    "COMPLETED": 5,
    "TOTAL": 60
  },
  {
    "USER_ID": 3,
    "PROBLEM_ID": 1,
    "PROBLEM_NAME": "Numbers",
    "COMPLETED": 9,
    "TOTAL": 50
  },
  {
    "USER_ID": 3,
    "PROBLEM_ID": 2,
    "PROBLEM_NAME": "Array",
    "COMPLETED": 8,
    "TOTAL": 30
  },
  {
    "USER_ID": 3,
    "PROBLEM_ID": 3,
    "PROBLEM_NAME": "Strings",
    "COMPLETED": 7,
    "TOTAL": 60
  },
  {
    "USER_ID": 4,
    "PROBLEM_ID": 1,
    "PROBLEM_NAME": "Numbers",
    "COMPLETED": 2,
    "TOTAL": 50
  },
  {
    "USER_ID": 4,
    "PROBLEM_ID": 2,
    "PROBLEM_NAME": "Array",
    "COMPLETED": 29,
    "TOTAL": 30
  },
  {
    "USER_ID": 4,
    "PROBLEM_ID": 3,
    "PROBLEM_NAME": "Strings",
    "COMPLETED": 60,
    "TOTAL": 60
  },
  {
    "USER_ID": 5,
    "PROBLEM_ID": 1,
    "PROBLEM_NAME": "Numbers",
    "COMPLETED": 50,
    "TOTAL": 50
  },
  {
    "USER_ID": 5,
    "PROBLEM_ID": 2,
    "PROBLEM_NAME": "Array",
    "COMPLETED": 30,
    "TOTAL": 30
  },
  {
    "USER_ID": 5,
    "PROBLEM_ID": 3,
    "PROBLEM_NAME": "Strings",
    "COMPLETED": 60,
    "TOTAL": 60
  }
]);



db.mentors.insertMany([
  {
    "MENTOR_ID": 1,
    "MENTOR_NAME": "Ragav",
    "MENTOR_SKILL": "React.js",
    "MENTEE_COUNT": 20
  },
  {
    "MENTOR_ID": 2,
    "MENTOR_NAME": "lavish",
    "MENTOR_SKILL": "Js,HTML,CSS",
    "MENTEE_COUNT": 15
  },
  {
    "MENTOR_ID": 3,
    "MENTOR_NAME": "Kanan",
    "MENTOR_SKILL": "JS",
    "MENTEE_COUNT": 30
  },
  {
    "MENTOR_ID": 4,
    "MENTOR_NAME": "Ramya",
    "MENTOR_SKILL": "Anguar",
    "MENTEE_COUNT": 7
  },
  {
    "MENTOR_ID": 5,
    "MENTOR_NAME": "Teju",
    "MENTOR_SKILL": "Mongo",
    "MENTEE_COUNT": 50
  }
]);



db.attendance.insertMany([
  {
    "USER_ID": 1,
    "CLASS_DATE": new Date("2022-01-09"),
    "STATUS": "Yes",
    "TASK_COMPLETED": "Yes"
  },
  {
    "USER_ID": 1,
    "CLASS_DATE": new Date("2022-10-16"),
    "STATUS": "No",
    "TASK_COMPLETED": "No"
  },
  {
    "USER_ID": 1,
    "CLASS_DATE": new Date("2022-10-30"),
    "STATUS": "Yes",
    "TASK_COMPLETED": "No"
  },
  {
    "USER_ID": 2,
    "CLASS_DATE": new Date("2022-01-09"),
    "STATUS": "No",
    "TASK_COMPLETED": "No"
  },
  {
    "USER_ID": 2,
    "CLASS_DATE": new Date("2022-10-16"),
    "STATUS": "No",
    "TASK_COMPLETED": "Yes"
  },
  {
    "USER_ID": 2,
    "CLASS_DATE": new Date("2022-10-30"),
    "STATUS": "Yes",
    "TASK_COMPLETED": "No"
  },
  {
    "USER_ID": 3,
    "CLASS_DATE": new Date("2022-01-09"),
    "STATUS": "Yes",
    "TASK_COMPLETED": "Yes"
  },
  {
    "USER_ID": 3,
    "CLASS_DATE": new Date("2022-10-16"),
    "STATUS": "Yes",
    "TASK_COMPLETED": "Yes"
  },
  {
    "USER_ID": 3,
    "CLASS_DATE": new Date("2022-10-30"),
    "STATUS": "Yes",
    "TASK_COMPLETED": "Yes"
  },
  {
    "USER_ID": 4,
    "CLASS_DATE": new Date("2022-01-09"),
    "STATUS": "No",
    "TASK_COMPLETED": "No"
  },
  {
    "USER_ID": 4,
    "CLASS_DATE": new Date("2022-10-16"),
    "STATUS": "No",
    "TASK_COMPLETED": "No"
  },
  {
    "USER_ID": 4,
    "CLASS_DATE": new Date("2022-10-30"),
    "STATUS": "No",
    "TASK_COMPLETED": "Yes"
  },
  {
    "USER_ID": 5,
    "CLASS_DATE": new Date("2022-01-09"),
    "STATUS": "No",
    "TASK_COMPLETED": "No"
  },
  {
    "USER_ID": 5,
    "CLASS_DATE": new Date("2022-10-16"),
    "STATUS": "No",
    "TASK_COMPLETED": "Yes"
  },
  {
    "USER_ID": 5,
    "CLASS_DATE": new Date("2022-10-30"),
    "STATUS": "Yes",
    "TASK_COMPLETED": "Yes"
  }
])


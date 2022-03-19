## Evaluate Amazon Web Services 
"In the cloud" is an oft-repeated phrase these days, and nearly every technology used promises cloud access. What does it mean? It's not technology "floating in the clouds," but rather computing hosted on a shared virtual environment, interconnected to a massive storage facility with contained servers, storage, and different sites.

Amazon Web Services (AWS) is the largest cloud provider in the market today. It's not the only one—many companies, such as Google and Microsoft, also have their own cloud platforms. We'll focus on AWS, but the services offered will be similar across all solutions.

Cloud services, such as AWS, allow a company to scale easily. Before cloud services, you would need to buy and store your own servers, which is costly, time-consuming, and requires physical space. A few considerations: How much to buy? What if you miscalculated your growth rate and spent too much or too little on servers? Cloud services allow the flexibility to adjust on the fly for budget and resources.

Before we begin, understand we'll be using AWS's set of free tier options. This way, we can learn and practice on the platform without incurring costs. AWS and other cloud services charge sneaky costs that quickly add up, so it's important to always follow the directions and use the free tier services. At the end of this module, we'll perform a full cleanup of all the services we used to ensure nothing is left in the cloud.

## Create an AWS Relational Database 
- Use RDS on AWS 

## Test with Create, Read, Update, and Delete 
Before we test our connection with our RDS instance and pgAdmin, let's learn about persistent data storage. Persistent data storage is where data is saved even when a machine's power is off (i.e., your computer's hard drive). SQL databases, such as the one we just connected to with AWS, is persistent storage.

The four basic functions of persistent data storage are Create, Read, Update, and Delete (CRUD). Let's test our connection to the RDS instance by performing some simple CRUD operations. This is review material, but it's important to understand which queries and operations belong to which part of CRUD.

Before we begin, from pgAdmin, create a new database within our RDS instances called "medical."

### Create
The first function of CRUD is creating data. We'll make tables and insert data into them. Inserting is the main part of creating data to be stored within the database. Let's run the following query.

CREATE TABLE doctors (
 id INT PRIMARY KEY NOT NULL,
 speciality TEXT,
 taking_patients BOOLEAN
);
CREATE TABLE patients (
 id INT NOT NULL,
 doctor_id INT NOT NULL,
 health_status TEXT,
 PRIMARY KEY (id, doctor_id),
 FOREIGN KEY (doctor_id) REFERENCES doctors (id)
);

INSERT INTO doctors(id, speciality, taking_patients)
VALUES
(1, 'cardiology', TRUE),
(2, 'orthopedics', FALSE),
(3, 'pediatrics', TRUE);
INSERT INTO patients (id, doctor_id, health_status)
VALUES
(1, 2, 'healthy'),
(2, 3, 'sick'),
(3, 2, 'sick'),
(4, 1, 'healthy'),
(5, 1, 'sick');

Great! We have just created some data. Although you have seen this before, it's important to understand where these queries fall in CRUD whenever you see it referenced.

### Read
The second function is reading our data. We'll run our SELECT statements for the data we want to retrieve from our tables. Let's run the following query to confirm our data has been successfully inserted.

-- Read tables
SELECT * FROM doctors;
SELECT * FROM patients;

### Update
The third function is updating data that is currently stored. We'll run the following query to update our data.

-- Update rows
UPDATE doctors
SET taking_patients = FALSE
WHERE id = 1;
UPDATE patients
SET health_status = 'healthy'
WHERE id = 1;

To confirm our update, run a SELECT statement, which as you recall is the read function of CRUD.

### Delete
The final function is deleting data. We'll run the following query to delete data.

-- Delete row
DELETE FROM patients
WHERE id = 1;

You're not likely to use the DELETE statement because we're in the business of collecting data, not removing it. You should always be very careful when deleting data—often a system or rules are in place to secure your database and make data removal difficult to prevent mistakes, which can happen.

You now have an RDS instance running and tested by the CRUD functions within persistent data storage. It's time to learn how raw data is stored.

## Database vs Data Storage


Data storage holds raw data such as CSVs, Excel files, and JavaScript Object Notation (JSON) files. Think of your own computer file system where you keep a ton of files as data storage. This data doesn't need to be queried and analyzed for business decisions. The files still have structure and can be reviewed, but not nearly as efficiently as a database.

A database contains cleaned, related information in tabular form. This database has been carefully planned and structured so that data can be analyzed efficiently through queries. Doing so comes at a cost of processing data to fit all the rules and structures.

Data storage is a place where large amounts of raw data can be kept without any wrangling or curating. Data storage allows us to keep data of different types or data we might want to parse in the future.

The benefit of having dedicated data storage is that nothing limits the intake of data. Data can flow in constantly and be saved without having to worry if it fits the criteria of the database. We have seen this with our extract, transform, and load (ETL) process—the data storage can hold raw files, such as CSV or JSON, for different needs.

AWS's S3 is a popular data storage service that we'll cover next.

## AWS Simple Storage Service: S3
S3 is Amazon's cloud file storage service that uses key-value pairs. Files are stored on multiple servers and have a high rate of availability of more than 99.9%. To store files, S3 uses buckets, which are similar to folders or directories on your computer. Buckets can contain additional folders and files. Each bucket must have a unique name across all of AWS.

One of S3's perks is its fine-grained control over files. Each file or bucket can have different read and write permissions, which helps regulate what can be done with each file.

S3 is also very scalable—you are not limited to the memory of one computer. As data flows in, more and more can be stored, as opposed to a local computer that is limited by available memory. Additionally, it offers availability—several team members can access massive amounts of data from one central location.

## PySpark and S3 Stored Data 
Since PySpark is a big data tool, it has many ways of reading in files from data storage so that we can manipulate them. We have decided to use S3 as our data storage, so we'll use PySpark for all data processing.

Using PySpark is how we've been reading in our data into Google Colab so far. The format for reading in from S3 is the S3 link, followed by your bucket name, folder by each folder, and then the filename, as follows:

For US East (default region)

template_url = "https://<bucket-name>.s3.amazonaws.com/<folder-name>/<file-name>"

example_url = "https://dataviz-curriculum.s3.amazonaws.com/data-folder/data.csv"

For other regions

template_url = "https://<bucket-name.s3-<region>.amazonaws.com/<folder-name>/<file-name>"

example_url =" https://dataviz-curriculum.s3-us-west-1.amazonaws.com/data-folder/data.csv"

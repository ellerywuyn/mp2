# CareerHub
Mini Project 2 – CareerHub: Building a Mini Job Portal with MongoDB and Flask

## Objectives: 
- Schema Design and Data Transformation: Understand the differences between relational and NoSQL databases. Design a MongoDB schema and transform data from a "relational" format (provided as multiple CSV files) into MongoDB collections
- MongoDB and Python Integration: Practice using PyMongo to interact with MongoDB through Python to gain hands-on experience with database operations such as insertion, querying, and updates
- Web API Development: Explore the basics of web API development using Flask and enhance your understanding of creating and managing endpoints to a modern database. You will practice testing these endpoints using tools like Postman to ensure your API's functionality and reliability

## Assignment Tasks
### Schema Design
I am using Mysql workbench to create a diagram that represents the proposed schema in a relational manner. Mysql Workbench is traditionally used for designing relational databases and not document-oriented databases like MongoDB, but I will just use it to show how the schema looks like:

**1. companies.csv:**

id: A unique identifier for the company. <br>
name: The name of the company. <br>
size: The size of the company (e.g., number of employees).<br>
type: The type of the company (e.g., Enterprise, Multinational, Startup, SME).<br>
location: The location of the company.<br>
website: The company's website URL.<br>
description: A brief description of the company.<br>
hr_contact: The HR contact email for the company.<br>

**2. education_and_skills.csv:**

id: A unique identifier for the education and skill entry.<br>
required_education: The required education level for a job.<br>
preferred_skills: A list of preferred skills for the job (comma-separated).<br>
job_id: A foreign key linking to a specific job.<br>

**3. employment_details.csv:**

id: A unique identifier for the employment detail entry.<br>
employment_type: The type of employment (e.g., Part-time, Contract, Full-time, etc.).<br>
average_salary: The average salary for the job.<br>
benefits: A list of benefits offered for the job.<br>
remote: A boolean indicating whether the job is remote or not.<br>
job_posting_url: The URL link to the job posting.<br>
posting_date: The date when the job was posted.<br>
closing_date: The date when the job application will close.<br>

**4. industry_info.csv:**

id: A unique identifier for the industry information entry.<br>
industry_name: The name of the industry.<br>
growth_rate: The growth rate of the industry.<br>
industry_skills: A list of skills relevant to the industry.<br>
top_companies: A list of top companies in the industry.<br>
trends: Industry-specific trends.<br>

**5. jobs.csv:**

id: A unique identifier for the job entry.<br>
title: The job title.<br>
description: A brief description of the job.<br>
years_of_experience: The years of experience required for the job.<br>
detailed_description: A detailed description of the job.<br>
responsibilities: Responsibilities associated with the job.<br>
requirements: Requirements for the job.<br>

******************
### Proposed Schema

The MongoDB collection follow the schema outlined below:

- **Root (Object)**
  - `id` (Integer, Required)
  - `title` (String, Required)
  - `description` (String, Required)
  - `years_of_experience` (Integer)
  - `detailed_description` (String)
  - `responsibilities` (String, Required)
  - `requirements` (String, Required)

- **company (Object, Required)**
  - `name` (String, Required)
  - `size` (String, Required)
  - `type` (String, Required)
  - `location` (String, Required)
  - `website` (String)
  - `description` (String, Required)
  - `hr_contact` (String, Required)

- **education_and_skills (Object, Required)**
  - `required_education` (String, Required)
  - `preferred_skills` (Array of Strings, Required)

- **employment_details (Object, Required)**
  - `employment_type` (String, Required)
  - `average_salary` (Integer, Required)
  - `benefits` (Array of Strings, Required)
  - `remote` (Boolean, Required)
  - `job_posting_url` (String, Required)
  - `posting_date` (String, Required)
  - `closing_date` (String, Required)

- **industry_info (Object, Required)**
  - `industry_name` (String, Required)
  - `growth_rate` (Double, Required)
  - `industry_skills` (Array of Strings, Required)
  - `top_companies` (Array of Strings, Required)
  - `trends` (Array of Strings, Required)

MongoDB schema in JSON Schema format:<br>

< img width="676" alt="image" src="https://github.com/Rundstedtzz/CareerHub/assets/63605514/a1ffad99-f990-435a-adf3-05e58a4bb78c">

*******************

### Data Transformation and Import
< img width="727" alt="image" src="https://github.com/Rundstedtzz/CareerHub/assets/63605514/e61961a2-ee3b-44e7-b5e1-a272fd18a138"> <br>



### Flask App

- Homepage
  - For the default root URL path (‘/’ or ‘http://localhost:5000/’), display a message welcoming your user.


- Create a Job Post
  - When a user visits this page http://localhost:5000/create/jobPost, they can create a new job posting with details, including title, description, industry, average salary, and location.
  - In the corresponding view function, make sure to include logic to validate the data and ensure that essential fields like title and industry are not empty.
  - Insert the validated data into the MongoDB collection.

- View Job Details (part 1)
  - When a user visits this page http://localhost:5000/search_by_job_id /<job_id> users can search by a job id.

- View Job Details (part 2)
  - Allow users to input a job title they wish to update via http://localhost:5000/update_by_job_title
  - Search for the job in the database and, if found, display the current details. Provide an option to modify fields like description, average, salary, and location.
  - Update the MongoDB collection with the new details after validation.
 
- Remove Job Listing
  - Provide an option for users to input a job title they wish to delete via http://localhost:5000/delete_by_job_title
  - Validate the input and search for the job in the database. If found, display the job details and ask the user for confirmation before deletion.
  - Delete the job from the MongoDB collection upon confirmation
 
- Salary Range Query
  - Develop an endpoint to query jobs based on a salary range.
  - The user should be able to provide min_salary and max_salary as query parameters, and the API should return jobs within that salary bracket.

- Job Experience Level Query
  - Create an endpoint where users can query jobs based on experience levels such as 'Entry Level', 'Mid Level', 'Senior Level', etc. 
  - Users should be able to provide an experience_level query parameter, and the API should list jobs that match the given experience requirement.

- Top Companies in an Industry
  - Develop an endpoint to fetch top companies in a given industry based on the number of job listings.
  - Users should provide an industry query parameter, and the API should return companies in that industry ranked by the number of job listings they have.

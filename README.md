# CareerHub
Mini Project 2 – CareerHub: Building a Mini Job Portal with MongoDB and Flask

## Objectives: 
**Schema Design and Data Transformation**: Understand the differences between relational and NoSQL databases. Design a MongoDB schema and transform data from a "relational" format (provided as multiple CSV files) into MongoDB collections.  
**MongoDB and Python Integration**: Practice using PyMongo to interact with MongoDB through Python to gain hands-on experience with database operations such as insertion, querying, and updates.  
**Web API Development**: Explore the basics of web API development using Flask and enhance your understanding of creating and managing endpoints to a modern database. You will practice testing these endpoints using tools like Postman to ensure your API's functionality and reliability.

## Schema Design

I just have one collection named Jobs

**Jobs Collection:**
- id
- title
- description
- years_of_experience
- detailed_description
- responsibilities
- requirements
- company:
  - name
  - size
  - type
  - location
  - website
  - description
  - hr_contact
- education_and_skills:
  - required_education
  - preferred_skills
- employment_details:
  - employment_type
  - average_salary
  - benefits
  - remote
  - job_posting_url
  - posting_date
  - closing_date
- industry_info:
  - industry_name
  - growth_rate
  - industry_skills
  - top_companies
  - trends

*******************

## Data Transformation and Import


<img width="1512" alt="Screenshot 2023-10-16 at 10 55 47 PM" src="https://github.com/ellerywuyn/mp2/assets/47910316/9963a352-c2d3-47f0-84b4-10cd4b4b806e">

<img width="723" alt="Screenshot 2023-10-16 at 8 32 41 PM" src="https://github.com/ellerywuyn/mp2/assets/47910316/ea2db726-8881-4e9d-a854-e587769814af">


## Flask App

- Homepage
  - For the default root URL path (‘/’ or ‘http://localhost:5000/’), display a message welcoming your user.

<img width="1512" alt="Screenshot 2023-10-16 at 10 57 37 PM" src="https://github.com/ellerywuyn/mp2/assets/47910316/e5f24105-2ba5-4a22-86db-cadb95c668d9">


- Create a Job Post
  - When a user visits this page http://localhost:5000/create/jobPost, they can create a new job posting with any of the fields in the collection such as details, including title, description, industry, average salary, and location.
  - Validate title and industry are not empty.  

<img width="1512" alt="Screenshot 2023-10-16 at 11 12 43 PM" src="https://github.com/ellerywuyn/mp2/assets/47910316/9340de2e-7f24-4a65-afea-914bb99e07e4">
<img width="1512" alt="Screenshot 2023-10-16 at 11 13 05 PM" src="https://github.com/ellerywuyn/mp2/assets/47910316/5177e7d1-d41a-484f-8a01-29d1e933a50c">  


  - Insert the validated data into the MongoDB collection.
 
<img width="1512" alt="Screenshot 2023-10-16 at 11 11 06 PM" src="https://github.com/ellerywuyn/mp2/assets/47910316/f06480fd-4d56-4533-8c14-f34a2049167c">



- View Job Details
  - When a user visits this page http://localhost:5000/search_by_job_id/<job_id> users can search by a job id.
  <img width="1512" alt="Screenshot 2023-10-16 at 11 05 49 PM" src="https://github.com/ellerywuyn/mp2/assets/47910316/8d9d2b89-f4da-45cd-afe1-1ca9ff436956">

- Update by Job Title
  - Allow users to input a job title they wish to update via http://localhost:5000/update_by_job_title
  - Search for the job in the database and, if found, display the current details. Provide an option to modify fields like description, average, salary, and location.
  <img width="1512" alt="Screenshot 2023-10-16 at 11 17 30 PM" src="https://github.com/ellerywuyn/mp2/assets/47910316/94047f66-12b8-42ee-81fd-da031327d1df">
  - Update the MongoDB collection with the new details after validation.
  <img width="1512" alt="Screenshot 2023-10-16 at 11 18 29 PM" src="https://github.com/ellerywuyn/mp2/assets/47910316/c482adfe-a468-4d7c-a23a-48aa710076f0">
  - Validate job exists and there's update values
  <img width="1512" alt="Screenshot 2023-10-16 at 11 18 52 PM" src="https://github.com/ellerywuyn/mp2/assets/47910316/87fcd6f2-b2a2-4771-94ab-c6b0a4035d32">
  <img width="1512" alt="Screenshot 2023-10-16 at 11 19 36 PM" src="https://github.com/ellerywuyn/mp2/assets/47910316/5ff54b75-062a-473d-a727-2f9dfadd50c4">


 
- Remove Job Listing
  - Provide an option for users to input a job title they wish to delete via http://localhost:5000/delete_by_job_title
  - Validate the input and search for the job in the database. If found, display the job details and ask the user for confirmation before deletion.
  - Delete the job from the MongoDB collection upon confirmation
 
    <img width="1512" alt="Screenshot 2023-10-16 at 11 20 35 PM" src="https://github.com/ellerywuyn/mp2/assets/47910316/71c4b683-3fc4-4f10-823b-aeb8fbbb57f7">
    - Validate job exists
  <img width="1512" alt="Screenshot 2023-10-16 at 11 20 57 PM" src="https://github.com/ellerywuyn/mp2/assets/47910316/ce9eb6bf-d590-4929-9b91-2ff3ba95ceb3">
  - Validate title exists
<img width="1512" alt="Screenshot 2023-10-16 at 11 24 58 PM" src="https://github.com/ellerywuyn/mp2/assets/47910316/bfb075bc-71fb-4f13-9431-243732e96a74">

  
 
- Salary Range Query
  - Develop an endpoint to query jobs based on a salary range.
  - The user should be able to provide min_salary and max_salary as query parameters, and the API should return jobs within that salary bracket.
    <img width="1512" alt="Screenshot 2023-10-16 at 11 26 32 PM" src="https://github.com/ellerywuyn/mp2/assets/47910316/da590f40-4252-49c1-8c60-ed0381486a23">


- Job Experience Level Query
  - Create an endpoint where users can query jobs based on experience levels such as 'Entry Level', 'Mid Level', 'Senior Level', etc. 
  - Users should be able to provide an experience_level query parameter, and the API should list jobs that match the given experience requirement.
<img width="1512" alt="Screenshot 2023-10-16 at 11 27 37 PM" src="https://github.com/ellerywuyn/mp2/assets/47910316/051290be-dc70-4480-aa38-68bf106e775b">
<img width="1512" alt="Screenshot 2023-10-16 at 11 27 50 PM" src="https://github.com/ellerywuyn/mp2/assets/47910316/b08a2b05-2b4b-48bc-9810-fe2c8d514984">
<img width="1512" alt="Screenshot 2023-10-16 at 11 28 01 PM" src="https://github.com/ellerywuyn/mp2/assets/47910316/c5bc16d8-e0fb-4ed0-86e1-1649c6679c75">

- Top Companies in an Industry
  - Develop an endpoint to fetch top companies in a given industry based on the number of job listings.
  - Users should provide an industry query parameter, and the API should return companies in that industry ranked by the number of job listings they have.
<img width="1512" alt="Screenshot 2023-10-16 at 11 28 50 PM" src="https://github.com/ellerywuyn/mp2/assets/47910316/17d0089e-350a-4c4f-88f8-120b89746b97">

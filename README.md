# SQL-Challenge

![image](https://github.com/nasr9000/SQL-Challenge/assets/128746625/1808fa4c-6ca8-4add-a31e-033bae180962)
![image](https://github.com/nasr9000/SQL-Challenge/assets/128746625/eb8473f6-e4e8-4a17-9f51-d782705a20c4)
![image](https://github.com/nasr9000/SQL-Challenge/assets/128746625/401365d0-11bc-4e5c-94e7-d05a4b113e88)

Instructions

This Challenge is divided into three parts: data modeling, data engineering, and data analysis.


1. Data Modeling
- Inspect the CSV files, and then sketch an Entity Relationship Diagram of the tables. To create the sketch, feel free to use a tool like QuickDBD.

2. Data Engineering
- Use the provided information to create a table schema for each of the six CSV files. Be sure to do the following:
  Remember to specify the data types, primary keys, foreign keys, and other constraints.

- For the primary keys, verify that the column is unique. Otherwise, create a composite key, which takes two primary keys to uniquely identify a row.

- Be sure to create the tables in the correct order to handle the foreign keys.

- Import each CSV file into its corresponding SQL table.

- Hint To avoid errors, import the data in the same order as the corresponding tables got created. And, remember to account for the headers when doing the imports.

3. Data Analysis

-  List the employee number, last name, first name, sex, and salary of each employee.

-  List the first name, last name, and hire date for the employees who were hired in 1986.

-  List the manager of each department along with their department number, department name, employee number, last name, and first name.

-  List the department number for each employee along with that employee’s employee number, last name, first name, and department name.

-  List first name, last name, and sex of each employee whose first name is Hercules and whose last name begins with the letter B.

-  List each employee in the Sales department, including their employee number, last name, and first name.

-  List each employee in the Sales and Development departments, including their employee number, last name, first name, and department name.

-  List the frequency counts, in descending order, of all the employee last names (that is, how many employees share each last name).

  Schema
  
CREATE TABLE titles (
    title_id varchar(5)   NOT NULL,
    title varchar(30)   NOT NULL,
    CONSTRAINT pk_titles PRIMARY KEY (
        title_id
     )
);

CREATE TABLE employees (
    emp_no INT  NOT NULL,
    emp_title_id VARCHAR NOT NULL,
    birth_date DATE  NOT NULL,
    first_name VARCHAR  NOT NULL,
    last_name VARCHAR  NOT NULL,
    sex VARCHAR  NOT NULL,
    hire_date DATE  NOT NULL,
    FOREIGN KEY (emp_title_id) REFERENCES titles (title_id),
    PRIMARY KEY (emp_no)
);


CREATE TABLE departments (
    dept_no varchar   NOT NULL,
    dept_name varchar   NOT NULL,
    CONSTRAINT pk_departments PRIMARY KEY (
        dept_no
     )
);
	
CREATE TABLE dept_manager (
    dept_no VARCHAR   NOT NULL,
    emp_no INT   NOT NULL,
    FOREIGN KEY (emp_no) REFERENCES employees (emp_no),
    FOREIGN KEY (dept_no) REFERENCES departments (dept_no),
    PRIMARY KEY (dept_no, emp_no)
);


CREATE TABLE dept_emp (
    emp_no INT  NOT NULL,
    dept_no VARCHAR  NOT NULL,
    FOREIGN KEY (emp_no) REFERENCES employees (emp_no),
    FOREIGN KEY (dept_no) REFERENCES departments (dept_no),
    PRIMARY KEY (emp_no, dept_no)
);



CREATE TABLE salaries (
    emp_no INT  NOT NULL,
    salary INT  NOT NULL,
    FOREIGN KEY (emp_no) REFERENCES employees (emp_no),
	PRIMARY KEY (emp_no)
);


  EBD Employee Diagram (FK's & PK's)

  
  ![image](https://github.com/nasr9000/SQL-Challenge/assets/128746625/74fc4846-d1a7-4931-a5d9-83c8cc366e5b)


# Web Application

## Intro

Throughout the semester, I have successfully designed and built a user-friendly, full-stack web application. This document aims to provide an overview of the technologies and methodologies I employed to fulfill the learning outcome of designing and building user-friendly, full-stack web applications.

## NodeJS
To develop the backend of the application, I utilized Node.js along with the Express.js framework. Node.js allowed me to build scalable and efficient server-side logic, while Express.js provided a robust foundation for handling routing and implementing communication protocols. By leveraging these technologies, I was able to create a reliable and performant backend for the web application.


### Appointment API
## ReactJS
For the frontend development, I chose React.js, a popular JavaScript framework known for its component-based architecture. Using React.js, I created a responsive and intuitive user interface for the web application. I organized the UI into reusable and modular components, adhering to best practices for code maintainability and scalability. 
### Customer frontend
## MySQL
To persist and manage data for the web application, I chose MySQL as the database management system. To simplify the deployment and management of the database, I utilized Docker Compose. The compose file provided a convenient way to define and orchestrate the MySQL container, along with other components of the application stack. By using Docker Compose, I ensured consistency and reproducibility in the setup of the database environment.

```version: '3'
services:
  client_information:
    container_name: customer_frontend_home
    build: ./customer_frontend
    volumes:
      - ./customer_frontend:/usr/src/app
    ports:
      - "3000:3000"
    restart: always
    # environment:
    #   CONN_URL: ""

  users:
    container_name: users_api
    build: ./users
    volumes:
      - ./users:/usr/src/app
    ports:
      - "5001:5001"
    restart: always

  schedule:
    container_name: schedule_api
    build: ./schedule
    volumes:
      - ./schedule:/usr/src/app
    ports:
      - "5002:5002"
    restart: always
    depends_on:
      - schedule_db

  appointments:
    container_name: appointments_api
    build: ./appointments
    volumes:
      - ./appointments:/usr/src/app
    ports:
      - "5003:5003"
    restart: always
    depends_on:
      - appointments_db
    # environment:
    #   DB_URL: "mysql://root:bub@appointments_db:3306/appointments"

  timeslots:
    container_name: time_slots_api
    build: ./time_slots
    volumes:
      - ./time_slots:/usr/src/app
    ports:
      - "5004:5004"
    restart: always
    depends_on:
      - timeslots_db

  appointments_db:
    container_name: appointments_db
    image: mysql
    restart: always
    volumes:
      - ./data/appointments:/var/lib/mysql
    environment:
      # MYSQL_USER: root
      MYSQL_ROOT_PASSWORD: bub
      MYSQL_DATABASE: appointments
    command: --pid-file=/var/lib/mysql/mysql.pid

  schedule_db:
    container_name: schedule_db
    image: mysql
    restart: always
    volumes:
      - ./data/schedule:/var/lib/mysql
    environment:
      # MYSQL_USER: root
      MYSQL_ROOT_PASSWORD: bub
      MYSQL_DATABASE: schedule
    command: --pid-file=/var/lib/mysql/mysql.pid

  timeslots_db:
    container_name: timeslots_db
    image: mysql
    restart: always
    volumes:
      - ./data/timeslots:/var/lib/mysql
    environment:
      # MYSQL_USER: root
      MYSQL_ROOT_PASSWORD: bub
      MYSQL_DATABASE: timeslots
    command: --pid-file=/var/lib/mysql/mysql.pid
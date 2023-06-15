# Portfolio

## Table of contents
- [Portfolio](#portfolio)
  - [Table of contents](#table-of-contents)
- [Intro](#intro)
- [Learning outcomes](#learning-outcomes)
- [Self-assessment](#self-assessment)
  - [1. Web application](#1-web-application)
  - [2. Software quality](#2-software-quality)
  - [3. Agile method](#3-agile-method)
  - [4. CI/CD](#4-cicd)
  - [5. Cultural differences and ethics](#5-cultural-differences-and-ethics)
  - [6. Requirements and design](#6-requirements-and-design)
  - [7. Business processes](#7-business-processes)
  - [8. Professional](#8-professional)

# Intro

This portfolio showcases my individual and group project during the software semester 3. It provides a comprehensive overview of my work, learning outcomes, and project achievements. With explanations of each learning outcome and a table of projects demonstrating my progress, this portfolio demonstrates my growth and dedication to software development.
# Learning outcomes

You can see a list of learning outcomes and their explanation [here](./learning_outcomes/learning-outcomes.md).
# Self-assessment

 ## 1. Web application

<table>
  <tr>
    <th><strong>Learning Outcome</strong></th>
    <td>"You desgin and build user-friendly, full-stack web applications."</td>
  </tr>
  <tr>
    <th><strong>Proficiency Rating</strong></th>
    <td>Proficient (4)</td>
  </tr>
  <tr>
    <th><strong>Explanation</strong></th>
    <td>
        <p>
          In this semestar I managed to set up a full React-Nodejs-MySQL stack application.
        </p>
        <p>
          Throughout my individual project, I successfully developed a user-friendly application using a full-stack approach. For the frontend, I utilized React, a widely adopted JavaScript framework, to create a responsive and intuitive user interface. I followed best practices for designing user interfaces, ensuring components were modular and had single responsibilities. Additionally, I conducted basic user experience testing to enhance the overall usability of the application.
        </p>
        <p>
           I integrated Auth0 for the login functionality in the application. By leveraging Auth0, I ensured secure and streamlined user authentication and authorization processes.  This allowed users to log in using email accounts.
        </p>
        <p>
          On the backend, I leveraged Node.js with Express.js as the server framework. This allowed me to handle routing efficiently and implement relevant communication protocols. To interact with the database, I utilized Sequelize, an ORM (Object-Relational Mapping) library, which facilitated seamless integration with MySQL. I ensured the persistence of data by employing Docker Compose to create a MySQL database and utilized MySQL volumes for storage.
        </p>
    </td>
  </tr>
  <tr>
    <th><strong>Proof</strong></th>
    <td>adsdas</td>
  </tr>
</table>

 ## 2. Software quality

<table>
  <tr>
    <th><strong>Learning Outcome</strong></th>
    <td>"You use software <strong>tooling and methodology</strong> that continuously monitors and improve the software quality during software development."</td>
  </tr>
  <tr>
    <th><strong>Proficiency Rating</strong></th>
    <td>Proficient (4)</td>
  </tr>
  <tr>
    <th><strong>Explanation</strong></th>
    <td>
        <p> 
          In order to continuously monitor and improve the software quality during software development, I employed various tools and methodologies.
        </p>
        <p>
          For testing, I utilized Jest to conduct unit tests and integration tests on both the frontend and backend components. These tests were executed in isolation, utilizing mocked classes or services when necessary to access external components. This ensured that relevant pieces of code were thoroughly tested and validated.
        </p>
        <p>
          To address code quality, I integrated Sonar for code analysis in both the frontend and backend repositories. Sonar performed scans to identify bugs, code smells, and vulnerabilities, providing valuable insights into improving the overall code quality. Additionally, Sonar was implemented within the CI (Continuous Integration) pipeline, specifically in Git actions. This allowed for automatic monitoring of code quality with each push or merge to the main branch, enabling timely identification and resolution of any issues.
        </p>
        <p>
          Additionally, I implemented ESLint within the CI (Continuous Integration) pipeline, specifically in Git actions. This enabled automatic code analysis with each push or merge to the main branch, allowing for early detection and resolution of any code quality issues.
        </p>
    </td>
  </tr>
  <tr>
    <th><strong>Proof</strong></th>
    <td>adsdas</td>
  </tr>
</table>

 ## 3. Agile method

<table>
  <tr>
    <th><strong>Learning Outcome</strong></th>
    <td>"You choose and implement the most suitable agile software development method for your software project."</td>
  </tr>
  <tr>
    <th><strong>Proficiency Rating</strong></th>
    <td>Proficient (4)</td>
  </tr>
  <tr>
    <th><strong>Explanation</strong></th>
    <td>
        <p>
         For my project, I implemented the Agile methodology using Jira as my project management tool. I organized my work into sprints, which are time-bound iterations for completing specific tasks and delivering incremental value. Initially, 
        </p>
        <p>
         I started with three-week sprints, but I realized that this timeframe was too long and caused me to lose focus and track of the sprint goals. Therefore, I made an informed decision to switch to two-week sprints, which allowed for better focus and improved alignment with the project objectives.
        </p>
    </td>
  </tr>
  <tr>
    <th><strong>Proof</strong></th>
    <td>adsdas</td>
  </tr>
</table>

 ## 4. CI/CD

<table>
  <tr>
    <th><strong>Learning Outcome</strong></th>
    <td>"You design and implement a (semi)automated software release process that matches the needs of the project context."</td>
  </tr>
  <tr>
    <th><strong>Proficiency Rating</strong></th>
    <td>Proficient (4)</td>
  </tr>
  <tr>
    <th><strong>Explanation</strong></th>
    <td>
        <p>
          Within every repository, a GitHub Actions workflow is set up to check if the application builds, and if the tests succeed.
        </p>
        <p>
          For continuous integration and deployment, I utilized GitHub Actions as my chosen solution. Within each repository, I set up a GitHub Actions workflow to ensure that the application builds successfully and that all tests pass. This automated process helped maintain code quality and ensured that changes were properly validated before release.
        </p>
        <p>
          To further enhance the quality gate, I integrated SonarCloud within the frontend project's pipeline. SonarCloud analyzed the codebase for bugs and enforced a minimum code coverage threshold of 50%. If any issues were identified or if the coverage fell below the defined limit, the pipeline would be blocked, preventing the release of flawed code.
        </p>
    </td>
  </tr>
  <tr>
    <th><strong>Proof</strong></th>
    <td>adsdas</td>
  </tr>
</table>

 ## 5. Cultural differences and ethics

<table>
  <tr>
    <th><strong>Learning Outcome</strong></th>
    <td>"You recognize and take into account cultural differences between project stakeholders and ethical aspects in software development."</td>
  </tr>
  <tr>
    <th><strong>Proficiency Rating</strong></th>
    <td>Proficient (4)</td>
  </tr>
  <tr>
    <th><strong>Explanation</strong></th>
    <td>
        <p>
          See <a href="docs/proof/9-ethics.md">this article</a>.
        </p>
    </td>
  </tr>
  <tr>
    <th><strong>Proof</strong></th>
    <td>adsdas</td>
  </tr>
</table>

 ## 6. Requirements and design

<table>
  <tr>
    <th><strong>Learning Outcome</strong></th>
    <td>"You analyze (non-functional) requirements, elaborate (architectural) designs and validate them using multiple types of test techniques."</td>
  </tr>
  <tr>
    <th><strong>Proficiency Rating</strong></th>
    <td>Proficient (4)</td>
  </tr>
  <tr>
    <th><strong>Explanation</strong></th>
    <td>
        <p>
          I have started the individual project by formulation a project idea. I then started to design the user stories, and an accompanying C4-model of the project. The same was done for the group project.
        </p>
        <p>
          The Settings API was made with an API contract in mind. The API contract is presented in <code>yml</code> format. See <a href="docs/12-apidocs.md">here</a>.
        </p>
        <p>
          During the group projects, after having reviewed the sprint with the stakeholders, we kept refining the user stories and acceptation criteria based on the feedback they gave us. The C4-Model remained roughly the same throughout the project.
        </p>
        <p>
          In my individual projects, and admittedly the GP as well, I could have formulated my user stories better. I should have split them up more and made them testable by formulating very concise acceptation criteria with clear data to base the tests upon. This will be improved upon with future projects.
        </p>
    </td>
  </tr>
  <tr>
    <th><strong>Proof</strong></th>
    <td>adsdas</td>
  </tr>
</table>


 ## 7. Business processes

<table>
  <tr>
    <th><strong>Learning Outcome</strong></th>
    <td>"You analyze and describe simple business processes that are related to your project."</td>
  </tr>
  <tr>
    <th><strong>Proficiency Rating</strong></th>
    <td>Proficient (4)</td>
  </tr>
  <tr>
    <th><strong>Explanation</strong></th>
    <td>
        <p>
          See <a href="docs/proof/10-user-flow.md">here</a> and <a href="docs/proof/13-business-process.md">here</a>.
        </p>
    </td>
  </tr>
  <tr>
    <th><strong>Proof</strong></th>
    <td>adsdas</td>
  </tr>
</table>

 ## 8. Professional

 <table>
  <tr>
    <th><strong>Learning Outcome</strong></th>
    <td>"You act in a professional manner during software development and learning."</td>
  </tr>
  <tr>
    <th><strong>Proficiency Rating</strong></th>
    <td>Proficient (4)</td>
  </tr>
  <tr>
    <th><strong>Explanation</strong></th>
    <td>
        <p>
          As a team, and to a smaller degree in my IP, I work with the Agile Methodology to work together. See <a href="docs/proof/5-agile-group-project.md">here</a>.
        </p>
        <p>
          In GP, I acted as the communications representative of the group. I planned the sprint review dates and informed the group of my communication with Mediaan.
        </p>
        <p>
          In GP, we made a Code of Conduct to which we adhered to whenever there was a disagreements.
        </p>
        <p>
          As a group we managed the stakeholders' expectations by giving them a sneak peak before the sprint review. During the sprint, we had regular contact with the stakeholders when we had any questions or confusions.
        </p>
        <p>
          As a group, we were able to say no to our stakeholder. We made it clear when we thought it would be impossible to complete a certain set of requirements/user stories. One notable 'no' was at the end when the product owner demanded every user story to be completely done. In hindsight we think that this was a test by Mediaan to see if we were able to say no.
        </p>
        <p>
          I regularly (at least once every two weeks) went to the teacher asking for feedback. This feedback was posted on Feedpulse. This moment was also used as a "milestone" to inform the teacher of my doings and experience, to convince them that I am proficient enough to go to the next semester.
        </p>
    </td>
  </tr>
  <tr>
    <th><strong>Proof</strong></th>
    <td>adsdas</td>
  </tr>
</table>

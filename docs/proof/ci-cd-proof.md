# Unit Testing in a backend NodeJS

## Intro

Unit testing is an important tool to verify a customer's needs on a technical level. Once you have your criteria set up, each time you make a change to your code, you can use the unit test to verify if your code still does what you intended it to do. Of course, this assumes the unit test you made is a valid unit test.

For testing my Node.js backend, I utilized the Jest testing framework in conjunction with SuperTest. 

You can read more about Jest and SuperTest here:
- [Jest](https://jestjs.io)
- [SuperTest](https://www.npmjs.com/package/supertest)


## Unit Testing API
I tested my appointment API. I tested every scenario, even error 500 as I was triggered by fact I cannot test it, so I found out about `sinonJS`

```
describe("Create an appointment", () =>{
  it('should return a status 200 and create an appointment', async () =>{
    
    const payload = {
      "timeslot_id": 2,
      "customer_id": 5
    }

    const response = await request.post("/appointments").send(payload)

    expect(response.statusCode).toBe(200)
  })

  it('invalid body request (timeId)', async () => {
    const payload = {
      "customer_id": 2
    }
    const response = await request.post("/appointments").send(payload)

    expect(response.statusCode).toBe(400)
  })

  it('invalid body request (custId)', async () => {
    const payload = {
      "timeslot_id": 2
    }
    const response = await request.post("/appointments").send(payload)

    expect(response.statusCode).toBe(400)
  })

  it('invalid body request (timeId, custId)', async () => {
    const payload = {
    }
    const response = await request.post("/appointments").send(payload)

    expect(response.statusCode).toBe(400)
  })

  it('should return a status 500 when there is an error creating the appointment', async () => {
    const payload = {
      "timeslot_id": 2,
      "customer_id": 5
    }

    // Mock the create method of the db.Appointment object to throw an error
    sinon.stub(db.Appointment, 'create').throws(new Error('Test error'));

    const response = await request.post("/appointments").send(payload)

    expect(response.statusCode).toBe(500)
  })
})
```



Jest provided a robust and user-friendly environment for writing and executing tests, while SuperTest allowed me to simulate HTTP requests and test the functionality of my API endpoints. I set up the testing environment by configuring Jest with appropriate configurations, including setting up test suites, defining test cases, and asserting expected outcomes. Using SuperTest, I could send HTTP requests to my API endpoints and validate the responses, ensuring the correct functioning of my Node.js application.

## Pipeline setup
I set up a CI/CD pipeline for my backend using GitHub Actions. The pipeline is triggered on every push to the master branch. The pipeline consists of five steps:

```yaml
name: CI / CD 

on:
  push:
    branches:
      - master
      
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Get code
        uses: actions/checkout@v3
      
      - name: Install dependencies
        uses: actions/setup-node@v3
        with:
          node-version: 18
        
      - name: Install ci
        run: npm ci

      - name: Run tests
        run: npm test
        
      - name: SonarCloud run
        uses: sonarsource/sonarcloud-github-action@master
        
        env:
          SONAR_TOKEN: ${{ secrets.SONAR_TOKEN }}
```
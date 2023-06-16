# Unit Testing in a backend NodeJS

## Intro

Unit testing is an important tool to verify a customer's needs on a technical level. Once you have your criteria set up, each time you make a change to your code, you can use the unit test to verify if your code still does what you intended it to do. Of course, this assumes the unit test you made is a valid unit test.

For testing my Node.js backend, I utilized the Jest testing framework in conjunction with SuperTest. 

You can read more about Jest and SuperTest here:
- [Jest](https://jestjs.io)
- [SuperTest](https://www.npmjs.com/package/supertest)

## Integration testing
Integration testing verifies the interaction and integration between different components, modules, or services of a system. It ensures that these elements work together seamlessly by validating communication, data exchange, and expected results. By identifying integration errors and interface mismatches, this testing approach helps ensure the proper functioning of the integrated components within a complex system.

Using Jest and jest-dom, I conducted comprehensive integration testing for the dropdown component in my project. In the first test, I ensured that the dropdown rendered with the correct users by mocking the response from the fetch request. The dropdown was populated with user names, and I validated that the correct number of items was displayed. Additionally, I confirmed that the selected user was properly highlighted in the dropdown and had the expected name.

In the second test, I focused on the functionality when a dropdown item was clicked. Mocking the fetch response again, I simulated a click on a dropdown item and verified that the corresponding functions were called with the expected arguments. This included updating the selected user, retrieving the finished schedule for the selected user, and setting the time slot.

By utilizing Jest and jest-dom, I conducted thorough integration testing, ensuring the correct rendering and functionality of the dropdown component and its interaction with other components and services. These tests facilitated the identification and resolution of any integration issues, contributing to the overall quality and reliability of the application.

```
test('renders dropdown with correct users', async () => {
  // Mock the response from the fetch request
  const mockUsers = [
    { Id: 1, Name: 'Barber 1' },
    { Id: 2, Name: 'Barber 2' }
  ];

  global.fetch = jest.fn().mockResolvedValue({
    json: () => Promise.resolve(mockUsers),
  });

  // Render the dropdown component with props
  render(
    <DropdownBarbers
      users={mockUsers}
      selectedUserId={2}
      setSelectedUserId={jest.fn()}
      getFinishedSchedule={jest.fn()}
      setTimeSlot={jest.fn()}
      selectedTs={''}
    />
  );

  const dropdownButton = screen.getByTestId("dropdown-button");
  expect(dropdownButton).toHaveTextContent("Barber 2");

  // Open the dropdown menu
  fireEvent.click(dropdownButton);

  // Wait for the dropdown to populate with users
  const dropdownItems = await screen.findAllByTestId('dropdown-item');

  // Check if the correct number of items is displayed
  expect(dropdownItems).toHaveLength(mockUsers.length);

  // Check if the dropdown items display the correct user names
  expect(dropdownItems[0]).toHaveTextContent('Barber 1');
  expect(dropdownItems[1]).toHaveTextContent('Barber 2');

  // Cleanup
  global.fetch.mockRestore();
});

test('calls the proper functions when a dropdown item is clicked', async () => {
  const mockUsers = [
    { Id: 1, Name: 'Barber 1' },
    { Id: 2, Name: 'Barber 2' }
  ];

  // Create mock functions
  const setSelectedUserIdMock = jest.fn();
  const getFinishedScheduleMock = jest.fn();
  const setTimeSlotMock = jest.fn();

  global.fetch = jest.fn().mockResolvedValue({
    json: () => Promise.resolve(mockUsers),
  });

  render(
    <DropdownBarbers
      users={mockUsers}
      selectedUserId={2}
      setSelectedUserId={setSelectedUserIdMock}
      getFinishedSchedule={getFinishedScheduleMock}
      setTimeSlot={setTimeSlotMock}
      selectedTs={''}
    />
  );

  const dropdownButton = screen.getByTestId("dropdown-button");
  fireEvent.click(dropdownButton); // Open the dropdown menu

  const dropdownItems = await screen.findAllByTestId('dropdown-item');

  // Simulate clicking the first dropdown item
  fireEvent.click(dropdownItems[0]);

  // Assert that the proper functions have been called with the expected arguments
  expect(setSelectedUserIdMock).toHaveBeenCalledWith(1);
  expect(getFinishedScheduleMock).toHaveBeenCalledWith(1);
  expect(setTimeSlotMock).toHaveBeenCalledWith('');

  // Cleanup
  global.fetch.mockRestore();
});
```

## Unit Testing API

I performed unit testing on the backend's "Create an appointment" functionality using Jest and Supertest. The tests covered various scenarios, including valid requests, invalid body requests, and error handling. For valid requests, I verified that a status code of 200 was returned upon successful appointment creation. 

I also tested for invalid body requests, such as missing parameters, to ensure the backend responded with a 400 status code. 

Furthermore, I included a test to handle cases where both timeslot ID and customer ID were missing from the request body, resulting in a 400 status code. 

Additionally, I tested error handling by simulating an error during the appointment creation process, confirming that the backend responded with a 500 status code. These unit tests ensured the reliability and correctness of the "Create an appointment" functionality in the backend.
I used `sinonjs` for testing error 500
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


### Sonar
[![Quality Gate Status](https://sonarcloud.io/api/project_badges/measure?project=BookYourBarber_bub_appointment_api&metric=alert_status)](https://sonarcloud.io/summary/new_code?id=BookYourBarber_bub_appointment_api) [![Coverage](https://sonarcloud.io/api/project_badges/measure?project=BookYourBarber_bub_appointment_api&metric=coverage)](https://sonarcloud.io/summary/new_code?id=BookYourBarber_bub_appointment_api) [![Bugs](https://sonarcloud.io/api/project_badges/measure?project=BookYourBarber_bub_appointment_api&metric=bugs)](https://sonarcloud.io/summary/new_code?id=BookYourBarber_bub_appointment_api) [![Vulnerabilities](https://sonarcloud.io/api/project_badges/measure?project=BookYourBarber_bub_appointment_api&metric=vulnerabilities)](https://sonarcloud.io/summary/new_code?id=BookYourBarber_bub_appointment_api)   [![Code Smells](https://sonarcloud.io/api/project_badges/measure?project=BookYourBarber_bub_appointment_api&metric=code_smells)](https://sonarcloud.io/summary/new_code?id=BookYourBarber_bub_appointment_api)


To ensure code quality in my project, I integrated Sonar for code analysis and monitoring. Sonar performed scans on both the frontend and backend repositories, identifying potential bugs, code smells, and vulnerabilities. 

By implementing Sonar within the CI (Continuous Integration) pipeline, specifically in Git actions, I enabled automatic monitoring of code quality with each push or merge to the main branch. 

This allowed for timely identification and resolution of any issues that could impact the overall code quality. The integration of Sonar as a code quality tool provided valuable insights and helped me maintain high standards in terms of code quality and best practices throughout the development process.
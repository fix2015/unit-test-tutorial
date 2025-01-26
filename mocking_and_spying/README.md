# Day 3: Mocking and Spying 🧪

### Key Points to Address:
- Review the home task from Day 2 to ensure students understand writing and running tests for basic utility functions.  
- Introduce **mocks** and **spies** in Jest, explaining their importance in testing external dependencies and monitoring function behavior.  
- Demonstrate how to mock functions and spy on method calls with Jest.  
- Emphasize the significance of testing async functions and mocking API calls for robust applications.  

---

## 0-5 minutes: Review the Home Task from Day 2
1. **Quick discussion**:
   - Ask students to share their experiences testing `filterEvenNumbers(arr)`.  
   - Highlight common challenges:  
     - Handling edge cases like empty arrays or arrays with only even/odd numbers.  
     - Testing large arrays efficiently.  
   - Reinforce the importance of edge cases and how they reveal hidden bugs.  

---

## 5-10 minutes: Understand Mocks and Spies
1. **Introduce the concept**:
   - **Mocks**: Fake versions of functions or modules that mimic behavior without relying on real implementations.  
     - Useful for isolating tests from external dependencies like APIs or databases.  
   - **Spies**: Tools to monitor calls to a function, including arguments passed, return values, and how often it was called.  
2. **Real-world examples**:
   - Mocking an API call in a weather app to simulate different responses.  
   - Spying on a logger function to ensure it’s called when expected.  
3. **Explain their importance**:
   - "Mocks and spies allow you to test how your code interacts with external dependencies or internal functions without relying on their actual behavior."  

---

## 10-20 minutes: Use Jest to Mock a Function and Test API Calls
1. **Mocking Basics**:
   - Show an example of mocking a simple function:
     ```javascript
     const mockFunction = jest.fn();

     mockFunction.mockReturnValue('Hello, world!');
     expect(mockFunction()).toBe('Hello, world!');
     ```
2. **Mocking API Calls**:
   - Example of testing an async function with a mocked API:
     ```javascript
     // Function to test
     async function fetchData(api) {
       const response = await api();
       return response.data;
     }

     // Mock API
     const mockApi = jest.fn().mockResolvedValue({ data: 'Mocked Data' });

     test('fetchData calls the API and returns data', async () => {
       const result = await fetchData(mockApi);
       expect(mockApi).toHaveBeenCalled();
       expect(result).toBe('Mocked Data');
     });
     ```
3. **Engage students**:
   - Ask: "What other scenarios can you imagine where mocking an API would be helpful?"

---

## 20-30 minutes: Practice Spying on a Function’s Behavior
1. **Introduction to Spies**:
   - "Spies let us monitor what happens when a function is called—without changing its behavior."  
2. **Demonstration**:
   ```javascript
   const logger = {
     log: jest.fn(),
   };

   function doSomething() {
     logger.log('Action performed!');
   }

   test('logs a message when doSomething is called', () => {
     doSomething();
     expect(logger.log).toHaveBeenCalledWith('Action performed!');
   });
   ```
3. **Activity**:
   - Ask students to create their own function, spy on it, and test how often it’s called and with what arguments.  

---

## Home Task: Mock a `fetch` Call to Test an Async Function
1. **Task Description**:
   - Write a function `fetchUserData(apiUrl)` that:
     - Makes a `fetch` call to `apiUrl`.  
     - Returns the user data if the response is successful.  
     - Throws an error if the request fails.  
2. **Test Requirements**:
   - Mock the `fetch` function to:
     - Simulate a successful response.  
     - Simulate a failed response.  
   - Use Jest to verify:
     - The correct data is returned for successful requests.  
     - An error is thrown for failed requests.  
3. **Examples**:
   ```javascript
   global.fetch = jest.fn();

   async function fetchUserData(apiUrl) {
     const response = await fetch(apiUrl);
     if (!response.ok) {
       throw new Error('Failed to fetch');
     }
     return await response.json();
   }

   test('fetchUserData handles successful response', async () => {
     fetch.mockResolvedValueOnce({
       ok: true,
       json: async () => ({ name: 'John Doe' }),
     });

     const data = await fetchUserData('/api/user');
     expect(data).toEqual({ name: 'John Doe' });
   });

   test('fetchUserData handles failed response', async () => {
     fetch.mockResolvedValueOnce({ ok: false });

     await expect(fetchUserData('/api/user')).rejects.toThrow('Failed to fetch');
   });
   ```

---

## Closing Notes
1. **Recap**:
   - Summarize the role of mocks and spies in testing.  
   - Emphasize their usefulness in testing external dependencies and ensuring function interactions are correct.  
2. **Encourage Questions**:
   - Address any doubts or difficulties faced during the session.  
3. **Motivate**:
   - "Testing with mocks and spies is a crucial skill for professional developers. Keep practicing to build confidence!"  

---

## Connect with Me:
- [LinkedIn - Vitalii Semianchuk](https://www.linkedin.com/in/vitalii-semianchuk-9812a786/)  
- [Telegram - @jsmentorfree](https://t.me/jsmentorfree) - We do a lot of free teaching on this channel! Join us to learn and grow in web development.  
- [Tiktok - @jsmentoring](https://www.tiktok.com/@jsmentoring) Everyday new videos  
- [Youtube - @jsmentor-uk](https://www.youtube.com/@jsmentor-uk) Mentor live streams  
- [Dev.to - fix2015](https://dev.to/fix2015) Javascript featured, live, experience  

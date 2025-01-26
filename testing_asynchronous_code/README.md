# Day 4: Testing Asynchronous Code ⏳

### Key Points to Address:
- Review the previous day’s home task to ensure students understand how to mock functions and use spies.  
- Introduce testing for **asynchronous code**, focusing on **promises** and **async/await**.  
- Demonstrate how to test an **API client function** that makes real-world asynchronous requests.  
- Explain the importance of handling errors and edge cases in asynchronous tests.  

---

## 0-5 minutes: Review the Home Task from Day 3
1. **Quick recap**:
   - Ask students to share their experience mocking the `fetch` call to test an async function.  
   - Discuss any challenges faced:
     - Did they run into issues mocking `fetch`?  
     - Were they able to test different response types (success, failure)?  
   - Reinforce the concepts of **mocking** and **spying** from Day 3 and ensure they’re comfortable with those concepts.  

---

## 5-10 minutes: Learn How to Test Promises and Async/Await Functions
1. **Promises**:
   - Explain how to test **promises** in Jest:
     ```javascript
     function fetchData() {
       return new Promise((resolve, reject) => {
         setTimeout(() => resolve('Data received'), 1000);
       });
     }

     test('fetches data correctly', () => {
       return fetchData().then(data => {
         expect(data).toBe('Data received');
       });
     });
     ```
   - Walk through how the test ensures the promise resolves as expected.

2. **Async/Await**:
   - Demonstrate testing **async/await** functions:
     ```javascript
     async function fetchData() {
       return 'Data received';
     }

     test('fetches data with async/await', async () => {
       const data = await fetchData();
       expect(data).toBe('Data received');
     });
     ```
   - Explain that **async/await** allows for cleaner, more readable asynchronous code.  
   - Discuss how Jest handles both **promises** and **async/await** for asynchronous testing.

---

## 10-20 minutes: Write Tests for an API Client Function
1. **Introduce the task**:
   - Ask students to write tests for an **API client function** that makes an asynchronous request to a mock API.  
   - Example function:
     ```javascript
     async function fetchUserData(url) {
       const response = await fetch(url);
       const data = await response.json();
       return data;
     }
     ```

2. **Test the function**:
   - Mock `fetch` to simulate different responses.
   - Example of a test for successful data retrieval:
     ```javascript
     test('fetches user data successfully', async () => {
       global.fetch = jest.fn().mockResolvedValue({
         json: jest.fn().mockResolvedValue({ name: 'John Doe' }),
       });

       const data = await fetchUserData('https://api.example.com/user');
       expect(data.name).toBe('John Doe');
     });
     ```

3. **Test failure scenario**:
   - Simulate a failed API call using `mockRejectedValue`:
     ```javascript
     test('handles API failure gracefully', async () => {
       global.fetch = jest.fn().mockRejectedValue(new Error('API Error'));

       try {
         await fetchUserData('https://api.example.com/user');
       } catch (e) {
         expect(e).toEqual(new Error('API Error'));
       }
     });
     ```

4. **Encourage students** to think about how they might handle various API scenarios (e.g., 404, 500 errors) and test for them.

---

## 20-30 minutes: Handle Errors in Asynchronous Code During Testing
1. **Importance of error handling**:
   - Explain that asynchronous code can often fail, and testing should account for both successful and failed outcomes.  
   - Discuss common error scenarios:
     - **Network failures** (e.g., `fetch` failing).
     - **API returning an error status code** (e.g., 404, 500).
     - **Invalid data** (e.g., empty or malformed responses).

2. **Test for errors**:
   - Demonstrate how to write tests for error handling:
     ```javascript
     async function fetchUserData(url) {
       const response = await fetch(url);
       if (!response.ok) {
         throw new Error('Network response was not ok');
       }
       return await response.json();
     }

     test('throws an error if the response is not ok', async () => {
       global.fetch = jest.fn().mockResolvedValue({
         ok: false,
         json: jest.fn().mockResolvedValue({}),
       });

       await expect(fetchUserData('https://api.example.com/user')).rejects.toThrow('Network response was not ok');
     });
     ```

3. **Test async/await with errors**:
   - Demonstrate using `rejects.toThrow` for async errors:
     ```javascript
     test('throws error on failure', async () => {
       global.fetch = jest.fn().mockRejectedValue(new Error('API Error'));

       await expect(fetchUserData('https://api.example.com/user')).rejects.toThrow('API Error');
     });
     ```

4. **Encourage students** to experiment with different failure conditions and how to test for them.

---

## Home Task: Write Tests for a Function that Interacts with an External API
1. **Task**:
   - Write tests for a function that interacts with an external API.  
   - The function should:
     - Make an API call using `fetch`.  
     - Handle both successful and error scenarios.  

2. **Examples to test**:
   - Test success with a valid response.  
   - Test failure with a 404 or 500 error.  
   - Test for an invalid response format (e.g., missing or incorrect data).  

3. **Encourage Testing Edge Cases**:
   - Test scenarios like network failure, timeouts, or empty responses.  

---

## Closing Notes
1. **Recap the day**:
   - Stress the importance of testing asynchronous code and handling errors.  
   - Highlight the value of writing tests that account for different real-world API scenarios.  

2. **Encourage questions**:
   - Ask students if they have any doubts about testing async functions or handling errors in Jest.  
   - Clarify any confusion about `async/await`, `mockResolvedValue`, or `mockRejectedValue`.  

3. **Motivate for the home task**:
   - Remind them that testing asynchronous code ensures robustness, especially when dealing with real-world APIs that might fail.  

---

## Connect with Me:
- [LinkedIn - Vitalii Semianchuk](https://www.linkedin.com/in/vitalii-semianchuk-9812a786/)  
- [Telegram - @jsmentorfree](https://t.me/jsmentorfree) - We do a lot of free teaching on this channel! Join us to learn and grow in web development.  
- [Tiktok - @jsmentoring](https://www.tiktok.com/@jsmentoring) Everyday new videos  
- [Youtube - @jsmentor-uk](https://www.youtube.com/@jsmentor-uk) Mentor live streams  
- [Dev.to - fix2015](https://dev.to/fix2015) Javascript featured, live, experience  

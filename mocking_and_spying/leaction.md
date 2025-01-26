# Teacher’s Guide: Day 3 - Mocking and Spying 🧑‍🏫

---

## 0-5 minutes: Review the Home Task from Day 2
1. **Ask Students to Share**:
   - Begin by asking a few students about their experience with the home task:  
     - Did they successfully write tests for `filterEvenNumbers()`?  
     - What challenges did they face?  
     - Did they explore edge cases? For example:
       - Empty arrays (`[]`).  
       - Arrays with only even numbers or only odd numbers.  
   - Use this discussion to reinforce the **Arrange-Act-Assert** pattern for structuring tests.  

2. **Highlight Learning Points**:
   - Praise students for testing edge cases—they often reveal unexpected bugs or overlooked scenarios.  
   - Remind them that thinking critically about inputs leads to better, more reliable code.

---

## 5-10 minutes: Understand Mocks and Spies
1. **Introduce Concepts**:
   - Explain **Mocks**:  
     - "Mocks are like stand-ins for real functions. Instead of calling the actual function, you use a mock that simulates the behavior you need."  
   - Explain **Spies**:  
     - "Spies let you observe what happens when a function is called—how often, with what arguments, and even what it returns—without changing its behavior."  

2. **Real-Life Examples**:
   - Mocking an API call:  
     - "Imagine you're building a weather app. You don’t want to make real API calls during testing because they might fail, be slow, or cost money."  
   - Spying on a logger function:  
     - "You might want to check if your `logger.log()` function is called every time a specific action occurs."  

3. **Interactive Question**:  
   - "Can you think of situations in your projects where mocking or spying might be useful?"

---

## 10-20 minutes: Use Jest to Mock a Function and Test API Calls
1. **Walkthrough**:
   - Demonstrate a simple mock function:  
     ```javascript
     const mockFunction = jest.fn();

     mockFunction.mockReturnValue('Hello, world!');
     expect(mockFunction()).toBe('Hello, world!');
     ```
   - Explain step-by-step what’s happening:
     - **`jest.fn()`** creates a mock function.  
     - **`mockReturnValue`** sets the value the mock should return.  
     - The test verifies that the mock behaves as expected.  

2. **API Call Example**:
   - Walk through the `fetchData` example provided in the session:  
     - Highlight how the mock simulates an API response without making a real network call.  
     - Explain why this makes tests faster, more reliable, and easier to run offline.  

3. **Engage Students**:
   - Ask them to brainstorm other scenarios where mocking external dependencies could simplify testing.

---

## 20-30 minutes: Practice Spying on a Function’s Behavior
1. **Introduce Spying**:
   - Show a practical use case for spies:
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
   - Break it down:
     - **Why use a spy?** To verify the logger was called correctly.  
     - **How does it work?** `jest.fn()` tracks calls to `logger.log` and the arguments passed.  

2. **Interactive Practice**:
   - Challenge students to:
     - Create a simple function that uses another function (e.g., a calculator calling a `log` function).  
     - Spy on the called function to verify it behaves as expected.  

3. **Encourage Questions**:
   - Address common doubts:
     - "When should I mock vs. spy?"  
     - "What happens if I don’t mock an API call?"  

---

## Home Task: Mock a `fetch` Call to Test an Async Function
1. **Explain the Task**:
   - Students will write a function `fetchUserData(apiUrl)` to:
     - Fetch user data from an API.  
     - Handle successful and failed requests appropriately.  

2. **What to Test**:
   - Verify the function:
     - Returns the correct data when the API call is successful.  
     - Throws an error when the API call fails.  

3. **Reminders for Mocking `fetch`**:
   - Mock `fetch` globally to avoid making real network calls.  
   - Use **`mockResolvedValueOnce`** for simulating successful responses.  
   - Use **`mockRejectedValueOnce`** for simulating failed responses.  

4. **Encourage Experimentation**:
   - Ask students to test different scenarios:
     - API responses with different shapes (e.g., `{ name: 'Alice' }`, `{ error: 'Not Found' }`).  
     - Simulating network errors (e.g., `fetch` throwing an exception).  

---

## Closing Notes
1. **Recap**:
   - Summarize the key takeaways:
     - Mocks simplify testing by replacing real implementations with controlled ones.  
     - Spies allow you to monitor how functions are used during tests.  
   - Emphasize the importance of these tools for isolating and testing complex code.  

2. **Encourage Questions**:
   - "Is there anything you found confusing or challenging today?"  
   - "Are there any other use cases for mocks or spies that you’d like to explore?"  

3. **Motivate for the Home Task**:
   - "Testing with mocks and spies might feel tricky at first, but with practice, it becomes second nature. Keep experimenting!"  

---

## Additional Resources for Teachers:
- Jest Documentation: [https://jestjs.io/docs/mock-functions](https://jestjs.io/docs/mock-functions)  
- Article on Mocking in JavaScript: [https://dev.to/mocking-js](https://dev.to/mocking-js)  

---

## Connect with Me:
- [LinkedIn - Vitalii Semianchuk](https://www.linkedin.com/in/vitalii-semianchuk-9812a786/)  
- [Telegram - @jsmentorfree](https://t.me/jsmentorfree) - We do a lot of free teaching on this channel! Join us to learn and grow in web development.  
- [Tiktok - @jsmentoring](https://www.tiktok.com/@jsmentoring) Everyday new videos  
- [Youtube - @jsmentor-uk](https://www.youtube.com/@jsmentor-uk) Mentor live streams  
- [Dev.to - fix2015](https://dev.to/fix2015) Javascript featured, live, experience  

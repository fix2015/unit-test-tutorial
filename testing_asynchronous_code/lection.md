# Day 4: Testing Asynchronous Code 🧪

### Teacher’s Guide: Explaining Day 4

---

## 0-5 minutes: Review the Home Task from Day 3
- **Quick Recap**:
  - Begin by asking students about their experience with mocking the `fetch` call and testing asynchronous functions.
  - **Ask Questions**:
    - "Who was able to successfully mock a `fetch` call and test an async function?"
    - "What challenges did you face while handling async behavior?"
  - **Reinforce Concepts**:
    - Remind students that when testing asynchronous code, it’s important to ensure the code waits for the asynchronous operation to complete.
    - Discuss the importance of using **`async/await`** and **`.resolves()`** or **`.rejects()`** in Jest.
  - **Encourage Sharing**:
    - Invite students to share how they mocked the `fetch` call and how they tested both success and failure cases.

---

## 5-10 minutes: Learn How to Test Promises and Async/Await Functions
- **Explain the Basics of Async Testing**:
  - "Asynchronous code runs in the background and doesn't block the rest of your program, so testing it requires handling these operations properly."
  - Explain the importance of using **`async`** and **`await`** for async functions in Jest.
  - **Show Example**:
    ```javascript
    // Function that returns a promise
    function fetchData(url) {
      return fetch(url).then(response => response.json());
    }

    // Test for the function
    describe('fetchData', () => {
      it('fetches data from the API', async () => {
        const data = await fetchData('https://api.example.com/data');
        expect(data).toHaveProperty('id');
      });
    });
    ```
  - **Explain**:
    - **`async`**: Marks the function as asynchronous.
    - **`await`**: Pauses the test execution until the promise is resolved.
    - **`expect().resolves`**: Can be used for testing promises that resolve.

---

## 10-20 minutes: Write Tests for an API Client Function
- **Introduce the Task**:
  - Provide students with a simple function that fetches data from an API.
    ```javascript
    function getUserData(userId) {
      return fetch(`https://api.example.com/users/${userId}`)
        .then(response => response.json());
    }
    ```
  - **Guide Students**:
    - Ask them to write a test that checks if the function fetches the user data correctly.
    - **Example Test**:
      ```javascript
      describe('getUserData', () => {
        it('fetches user data by ID', async () => {
          const user = await getUserData(1);
          expect(user).toHaveProperty('name');
        });
      });
      ```
  - **Challenge**:
    - Ask students to consider edge cases, such as an invalid `userId` or a failed API call.
    - **Test for Failure**:
      ```javascript
      it('handles failed API call gracefully', async () => {
        const user = await getUserData(999); // Assuming 999 is an invalid ID
        expect(user).toBeNull();
      });
      ```

---

## 20-30 minutes: Handle Errors in Asynchronous Code During Testing
- **Discuss Error Handling**:
  - "When testing async functions, you must also handle errors, such as when a promise rejects or when an API call fails."
  - **Show Example**:
    ```javascript
    function fetchData(url) {
      return fetch(url).then(response => {
        if (!response.ok) {
          throw new Error('Network response was not ok');
        }
        return response.json();
      });
    }

    describe('fetchData', () => {
      it('throws an error for bad API responses', async () => {
        await expect(fetchData('https://api.example.com/invalid'))
          .rejects
          .toThrow('Network response was not ok');
      });
    });
    ```
  - **Key Takeaway**:
    - Use **`.rejects`** to test for promise rejections.
    - Handle both successful and failed asynchronous scenarios to ensure robustness.

---

## Home Task: Write Tests for a Function That Interacts with an External API
- **Introduce the Task**:
  - Ask students to write tests for a function that fetches data from an external API, such as a weather API or a stock price API.
  - Provide an example:
    ```javascript
    function getWeather(city) {
      return fetch(`https://api.weather.com/v3/weather/${city}`)
        .then(response => response.json());
    }
    ```
  - **Encourage Edge Case Testing**:
    - Test for valid city names, invalid city names, and failed API calls (e.g., server errors).
  - **Challenge**:
    - "Think about how you can test error scenarios and timeouts in API calls."

---

## Closing Notes
- **Recap**:
  - "Today we learned how to test asynchronous functions using `async/await` and how to handle errors effectively."
  - Reinforce the importance of testing both success and failure cases to ensure the function works under various conditions.
- **Encourage Questions**:
  - Ask students if they have any questions or if they encountered any difficulties while testing async functions.
- **Homework Reminder**:
  - "Don't forget to write tests for your API-interaction functions and test both success and failure scenarios!"

---

### Tips for Effective Teaching
1. **Encourage Active Participation**:
   - Walk around the room to assist students with any issues they encounter while writing tests.
2. **Emphasize Error Handling**:
   - Remind students that robust tests need to cover both the expected success and failure scenarios.
3. **Celebrate Success**:
   - Praise students for writing clear, thorough tests and testing edge cases effectively.
4. **Share Real-World Insights**:
   - Mention that in real-world applications, asynchronous code is prevalent, and testing it ensures reliability in production environments.

---

## Connect with Me:
- [LinkedIn - Vitalii Semianchuk](https://www.linkedin.com/in/vitalii-semianchuk-9812a786/)  
- [Telegram - @jsmentorfree](https://t.me/jsmentorfree) - We do a lot of free teaching on this channel! Join us to learn and grow in web development.  
- [Tiktok - @jsmentoring](https://www.tiktok.com/@jsmentoring) Everyday new videos  
- [Youtube - @jsmentor-uk](https://www.youtube.com/@jsmentor-uk) Mentor live streams  
- [Dev.to - fix2015](https://dev.to/fix2015) Javascript featured, live, experience  

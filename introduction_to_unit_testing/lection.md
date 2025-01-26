# Day 1: Introduction to Unit Testing 🧪

### Guide for the Teacher: How to Deliver the Lesson Effectively

---

## 0-5 minutes: Introduction to Unit Testing
1. **Start with a relatable analogy**:
   - "Imagine testing a car. You don’t drive it 100 miles right away; instead, you check individual components first—like the brakes, the engine, and the tires. Unit testing works the same way in software development."
2. **Explain what unit testing is**:
   - "Unit testing focuses on testing individual functions or methods to ensure they work as intended."
3. **Emphasize the importance**:
   - Catching bugs early saves time and money.
   - Writing tests helps improve the structure and maintainability of code.
   - Tests act as a safety net for future changes.

---

## 5-15 minutes: Structure of a Unit Test
1. **Explain the three core steps**:
   - **Arrange**: Set up the necessary data or state for the test.
   - **Act**: Perform the action you’re testing.
   - **Assert**: Verify that the output matches the expected result.
2. **Example explanation**:
   - Walk students through the following code step-by-step:
     ```javascript
     // Function to test
     function add(a, b) {
       return a + b;
     }

     // Test case
     test('adds two numbers correctly', () => {
       // Arrange
       const a = 2, b = 3;

       // Act
       const result = add(a, b);

       // Assert
       expect(result).toBe(5);
     });
     ```
   - Highlight the **expect** function and explain its purpose: "This checks whether the actual result matches the expected result."

---

## 15-30 minutes: Setting Up Jest and Writing Your First Test
1. **Set the stage**:
   - Explain that Jest is one of the most popular JavaScript testing frameworks.
   - Emphasize that Jest makes testing simple with built-in tools and assertions.
2. **Guide students through installation**:
   - Demonstrate how to install Jest:
     ```bash
     npm install --save-dev jest
     ```
   - Explain the purpose of `--save-dev`: "It installs Jest as a development dependency, meaning it’s only needed during development and not in production."
3. **Set up a test script**:
   - Show them how to modify `package.json`:
     ```json
     {
       "scripts": {
         "test": "jest"
       }
     }
     ```
   - Explain: "Now, you can run all your tests by typing \`npm test\`."
4. **Write and run a test**:
   - Walk them through creating a test file:
     ```javascript
     function add(a, b) {
       return a + b;
     }

     test('adds 1 + 2 to equal 3', () => {
       expect(add(1, 2)).toBe(3);
     });
     ```
   - Show them how to run the test and interpret the results:
     ```bash
     npm test
     ```
   - Explain: "If the test passes, it means the function works as expected for the given inputs."

---

## 30-40 minutes: Assigning the Home Task
1. **Set the task**:
   - Ask students to write a test for a `subtract(a, b)` function.
   - Explain: "The function should subtract one number from another and return the result."
2. **Encourage exploration**:
   - Suggest testing edge cases: negative numbers, zero, large numbers.
   - Remind them to use the Arrange-Act-Assert pattern.
3. **Optional challenge**:
   - For advanced students, suggest creating a test for a more complex function, like one that calculates the factorial of a number.

---

## Closing Notes
1. **Recap the lesson**:
   - Highlight the benefits of unit testing: "Unit testing not only ensures your code works today but also protects it from future bugs."
2. **Invite questions**:
   - Encourage students to ask questions or share any difficulties they faced during the session.
3. **Motivate them**:
   - Remind them: "Testing is a skill that makes you a more confident and reliable developer. The effort you put in now will pay off greatly in your career."

---

## Connect with Me:
- [LinkedIn - Vitalii Semianchuk](https://www.linkedin.com/in/vitalii-semianchuk-9812a786/)
- [Telegram - @jsmentorfree](https://t.me/jsmentorfree) - We do a lot of free teaching on this channel! Join us to learn and grow in web development.
- [Tiktok - @jsmentoring](https://www.tiktok.com/@jsmentoring) Everyday new videos
- [Youtube - @jsmentor-uk](https://www.youtube.com/@jsmentor-uk) Mentor live streams
- [Dev.to - fix2015](https://dev.to/fix2015) Javascript featured, live, experience

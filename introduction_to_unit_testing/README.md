# Day 1: Introduction to Unit Testing 🧪

### Key Points to Address:
- If students are new to testing, provide a quick overview of **what testing is** and its importance in software development.  
- Explain **Unit Testing**:  
  - A type of testing where individual components or functions of an application are tested in isolation.  
  - The goal is to ensure that each "unit" of the application behaves as expected.  
  - Unit tests help catch bugs early, improve code quality, and make refactoring safer.  

---

## 0-5 minutes: What is Unit Testing and Why is it Important?
- **Definition**: Unit testing is a way to test individual pieces of code, such as functions or methods, to verify they work as intended.  
- **Importance**:
  - **Catch Bugs Early**: Problems are easier and cheaper to fix during development.
  - **Improve Code Quality**: Encourages modular and maintainable code.  
  - **Increase Confidence**: Developers can refactor code without fear of breaking functionality.  

---

## 5-15 minutes: Learn the Structure of a Test
- **Arrange, Act, Assert**: The basic structure of a test.
  1. **Arrange**: Set up the initial state and inputs.
  2. **Act**: Perform the operation being tested.
  3. **Assert**: Verify the result matches expectations.

Example:

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

---

## 15-30 minutes: Set Up a Basic Testing Environment with Jest
1. **Install Jest**:  
   ```bash
   npm install --save-dev jest
   ```
2. **Update `package.json`** to add a test script:  
   ```json
   {
     "scripts": {
       "test": "jest"
     }
   }
   ```
3. **Write a simple test** in a file named `math.test.js`:
   ```javascript
   function add(a, b) {
     return a + b;
   }

   test('adds 1 + 2 to equal 3', () => {
     expect(add(1, 2)).toBe(3);
   });
   ```
4. **Run the test**:  
   ```bash
   npm test
   ```

---
z
## Home Task: Write a Test for a Simple Math Utility Function
- Write a test for a function `subtract(a, b)` that subtracts one number from another.  
- Use Jest to verify the function works for different inputs, including edge cases like negative numbers or zero.

---

## Connect with Me:
- [LinkedIn - Vitalii Semianchuk](https://www.linkedin.com/in/vitalii-semianchuk-9812a786/)
- [Telegram - @jsmentorfree](https://t.me/jsmentorfree) - We do a lot of free teaching on this channel! Join us to learn and grow in web development.
- [Tiktok - @jsmentoring](https://www.tiktok.com/@jsmentoring) Everyday new videos
- [Youtube - @jsmentor-uk](https://www.youtube.com/@jsmentor-uk) Mentor live streams
- [Dev.to - fix2015](https://dev.to/fix2015) Javascript featured, live, experience

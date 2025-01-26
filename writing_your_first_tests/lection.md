# Day 2: Writing Your First Tests 🧪

### Teacher’s Guide: Explaining Day 2

---

## 0-5 minutes: Review the Home Task from Day 1
- Start with a quick discussion about the home task:
  - **Ask Questions**:
    - "Who was able to successfully write tests for `subtract(a, b)`?"
    - "What challenges did you face while testing edge cases like negative numbers or zero?"
  - **Reinforce Concepts**:
    - Remind them of the **Arrange-Act-Assert** pattern:
      - Arrange: Setting up variables or test data.
      - Act: Executing the function or operation.
      - Assert: Checking the output against expectations.
  - **Encourage Sharing**:
    - Have students share how they approached edge cases to foster peer learning.

---

## 5-10 minutes: Learn How to Use `describe()`, `it()`, and `expect()` in Jest
- **Explain the Need for Structure**:
  - "As we start testing more complex functions, organizing tests becomes essential. Jest provides tools like `describe()` and `it()` to group and document our tests effectively."
- **Demonstrate with Examples**:
  - Walk through this example on the board or screen:
    ```javascript
    describe('String manipulation functions', () => {
      it('capitalizes the first letter of a string', () => {
        expect(capitalize('hello')).toBe('Hello');
      });
    });
    ```
  - Explain:
    - **`describe()`**: Groups related tests (e.g., all string manipulation functions).
    - **`it()`**: Describes a single test case.
    - **`expect()`**: Verifies the actual result matches the expected result.
- **Engage Students**:
  - Ask: "Why do you think grouping tests might be useful as your projects grow?"

---

## 10-20 minutes: Write Tests for String Manipulation Functions
- **Set Up the Task**:
  - Introduce the two functions to test: `capitalize()` and `reverse()`.
  - Explain their behavior briefly:
    - `capitalize()`: Converts the first letter of a string to uppercase.
    - `reverse()`: Reverses the characters in a string.
- **Guide Through Examples**:
  - Show this test for `reverse()`:
    ```javascript
    it('reverses a string correctly', () => {
      expect(reverse('hello')).toBe('olleh');
    });
    ```
  - Ask students: "What edge cases might break this function?"
    - Example answers: Empty strings, strings with spaces, or special characters.
- **Activity**:
  - Have students write their own tests for `capitalize()` while you walk around to assist.

---

## 20-30 minutes: Discuss the Importance of Edge Cases
- **Define Edge Cases**:
  - "Edge cases are inputs that test the boundaries of what your function is designed to handle."
- **Discuss Real-World Examples**:
  - What if `capitalize()` is given a number instead of a string?
  - How should `reverse()` handle strings with emojis or non-Latin characters?
- **Interactive Brainstorming**:
  - Ask students to list potential edge cases for `capitalize()` and `reverse()`.
  - Write their ideas on the board to ensure everyone has a clear understanding.

---

## Home Task: Write Tests for Array Utility Functions
- **Introduce the Task**:
  - Explain the function `filterEvenNumbers(arr)`:
    - It takes an array of numbers and removes all even numbers.
  - Provide examples:
    ```javascript
    filterEvenNumbers([1, 2, 3, 4]); // [1, 3]
    filterEvenNumbers([]);          // []
    filterEvenNumbers([2, 4, 6]);   // []
    ```
- **Encourage Edge Case Testing**:
  - "Think about cases where the array is empty, has negative numbers, or contains very large numbers."
- **Motivate with a Challenge**:
  - "The more thorough your tests, the more confident you can be in your function. Test it until you’re convinced it can’t break!"

---

## Closing Notes
- **Recap**:
  - Highlight the importance of structured tests using `describe()` and `it()`.
  - Emphasize the value of testing edge cases for robustness.
- **Encourage Engagement**:
  - "Testing is a skill that will make you a better developer. Keep practicing and experimenting!"
- **Homework Reminder**:
  - "Don’t forget to write tests for `filterEvenNumbers(arr)` and try to break your own function!"

---

### Tips for Effective Teaching
1. **Encourage Questions**:
   - Remind students that asking questions is part of the learning process.
2. **Walk Around During Activities**:
   - Offer help individually while students write their tests.
3. **Celebrate Success**:
   - Praise students for correctly identifying edge cases or writing creative tests.
4. **Share Real-World Insights**:
   - Mention how professional developers rely on testing to build reliable software.

---

## Connect with Me:
- [LinkedIn - Vitalii Semianchuk](https://www.linkedin.com/in/vitalii-semianchuk-9812a786/)  
- [Telegram - @jsmentorfree](https://t.me/jsmentorfree) - We do a lot of free teaching on this channel! Join us to learn and grow in web development.  
- [Tiktok - @jsmentoring](https://www.tiktok.com/@jsmentoring) Everyday new videos  
- [Youtube - @jsmentor-uk](https://www.youtube.com/@jsmentor-uk) Mentor live streams  
- [Dev.to - fix2015](https://dev.to/fix2015) Javascript featured, live, experience  

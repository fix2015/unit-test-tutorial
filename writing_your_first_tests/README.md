# Day 2: Writing Your First Tests 🧪

### Key Points to Address:
- Review the previous day’s home task to ensure students understand the basics of writing and running unit tests.  
- Introduce more structured testing techniques using **describe()**, **it()**, and **expect()**.  
- Demonstrate how to write tests for common string manipulation functions, highlighting the importance of testing edge cases.  
- Encourage students to think critically about potential edge cases and how they might break their code.  

---

## 0-5 minutes: Review the Home Task from Day 1
1. **Quick recap**:
   - Ask students to share their experiences writing tests for `subtract(a, b)`.  
   - Discuss common issues:
     - Did they encounter unexpected bugs?  
     - Did they test edge cases like subtracting zero or negative numbers?  
   - Reiterate the **Arrange-Act-Assert** structure to keep their tests organized.  

---

## 5-10 minutes: Learn How to Use `describe()`, `it()`, and `expect()` in Jest
1. **Explain the purpose of `describe()`**:
   - "It helps group related tests together for better organization and readability."
2. **Explain the purpose of `it()`**:
   - "This is an alternative to `test()` and is often used to describe individual test cases."
3. **Demonstrate usage with an example**:
   ```javascript
   // String manipulation functions
   function capitalize(str) {
     return str.charAt(0).toUpperCase() + str.slice(1);
   }

   // Test suite for string functions
   describe('String manipulation functions', () => {
     it('capitalizes the first letter of a string', () => {
       expect(capitalize('hello')).toBe('Hello');
     });

     it('handles empty strings gracefully', () => {
       expect(capitalize('')).toBe('');
     });
   });
   ```
4. **Key takeaway**:
   - Use `describe()` for grouping related tests.
   - Use `it()` to describe specific behaviors being tested.
   - Use `expect()` for assertions to verify results.

---

## 10-20 minutes: Write Tests for String Manipulation Functions
1. **Introduce the task**:
   - Ask students to write tests for two functions:  
     - `capitalize(str)`: Capitalizes the first letter of a string.  
     - `reverse(str)`: Reverses the characters in a string.  
2. **Provide example test cases**:
   ```javascript
   function reverse(str) {
     return str.split('').reverse().join('');
   }

   describe('String manipulation functions', () => {
     it('reverses a string correctly', () => {
       expect(reverse('hello')).toBe('olleh');
     });

     it('handles empty strings gracefully', () => {
       expect(reverse('')).toBe('');
     });
   });
   ```
3. **Encourage experimentation**:
   - Test edge cases like strings with spaces, special characters, or numbers.  

---

## 20-30 minutes: Discuss the Importance of Edge Cases
1. **What are edge cases?**:
   - Inputs that are at the boundary of what the function is designed to handle (e.g., empty strings, null values, very large inputs).  
2. **Why test edge cases?**:
   - Edge cases often reveal hidden bugs or assumptions in code.  
3. **Example discussion**:
   - What happens if `capitalize()` is passed a string with only spaces?  
   - What if `reverse()` is passed a very long string?  
4. **Activity**:
   - Brainstorm edge cases for the functions they’ve written and test them in Jest.  

---

## Home Task: Write Tests for Array Utility Functions
1. **Task**:
   - Write tests for a function `filterEvenNumbers(arr)` that filters out all even numbers from an array.  
2. **Examples to test**:
   ```javascript
   filterEvenNumbers([1, 2, 3, 4]); // Expected: [1, 3]
   filterEvenNumbers([]);          // Expected: []
   filterEvenNumbers([2, 4, 6]);   // Expected: []
   filterEvenNumbers([1, 3, 5]);   // Expected: [1, 3, 5]
   ```
3. **Encourage testing edge cases**:
   - Arrays with no elements.  
   - Arrays with all even or all odd numbers.  
   - Arrays with negative numbers or very large numbers.  

---

## Closing Notes
1. **Recap the day**:
   - Stress the importance of structured testing with `describe()` and `it()`.  
   - Highlight how testing edge cases improves code robustness.  
2. **Encourage questions**:
   - Ask students if they faced any challenges or if anything is unclear.  
3. **Motivate for the home task**:
   - Remind them: "Testing isn’t just about finding bugs—it’s about writing better code and gaining confidence in your work."  

---

## Connect with Me:
- [LinkedIn - Vitalii Semianchuk](https://www.linkedin.com/in/vitalii-semianchuk-9812a786/)  
- [Telegram - @jsmentorfree](https://t.me/jsmentorfree) - We do a lot of free teaching on this channel! Join us to learn and grow in web development.  
- [Tiktok - @jsmentoring](https://www.tiktok.com/@jsmentoring) Everyday new videos  
- [Youtube - @jsmentor-uk](https://www.youtube.com/@jsmentor-uk) Mentor live streams  
- [Dev.to - fix2015](https://dev.to/fix2015) Javascript featured, live, experience  

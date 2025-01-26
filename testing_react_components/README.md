# Day 5: Testing React Components ⚛️

### Key Points to Address:
- Review the previous day’s home task to ensure students understand the basics of writing tests for functions and components.
- Introduce **React Testing Library** and explain how it can be used to test React components in a more realistic way.
- Demonstrate how to write tests for a simple functional React component.
- Explain how to simulate user interactions using `fireEvent` to test dynamic behavior in React components.
- Encourage students to write tests for components with props and state.

---

## 0-5 minutes: Review the Home Task from Day 4
1. **Quick recap**:
   - Ask students to share their experiences writing tests for array utility functions.  
   - Discuss challenges and best practices:
     - How did they handle edge cases for the `filterEvenNumbers` function?
     - Were there any specific edge cases that caused issues?
   - Reiterate the importance of testing edge cases for better test coverage.

---

## 5-10 minutes: Set up React Testing Library
1. **Introduction to React Testing Library**:
   - Explain the importance of React Testing Library for testing React components in a way that mimics how they will be used in the browser.
   - Discuss the differences between **React Testing Library** and **Enzyme**.
   - Show the installation steps:
     ```bash
     npm install --dev @testing-library/react @testing-library/jest-dom
     ```
2. **Key Features**:
   - **render()**: Renders the component for testing.
   - **screen**: Provides access to the rendered component’s DOM elements.
   - **fireEvent**: Allows simulating user interactions.

---

## 10-20 minutes: Write Tests for a Functional React Component
1. **Introduce the task**:
   - Present a simple functional component to test:
     ```javascript
     function Greeting({ name }) {
       return <h1>Hello, {name}!</h1>;
     }
     ```
2. **Demonstrate the test**:
   - Write a test to check if the component renders correctly:
     ```javascript
     import { render, screen } from '@testing-library/react';
     import Greeting from './Greeting';

     test('renders a greeting message', () => {
       render(<Greeting name="Alice" />);
       const greetingElement = screen.getByText(/Hello, Alice!/i);
       expect(greetingElement).toBeInTheDocument();
     });
     ```
3. **Key takeaway**:
   - Use `render()` to render the component.
   - Use `screen.getByText()` to query the rendered DOM for the text.
   - Use `expect()` to assert the expected output.

---

## 20-30 minutes: Test User Interactions Using `fireEvent`
1. **Introduce the concept of user interactions**:
   - In real-world applications, user interactions are crucial. We need to simulate actions like clicks, typing, and form submissions to test dynamic behavior.
2. **Demonstrate a button click example**:
   - Update the component to include a button:
     ```javascript
     function Greeting({ name }) {
       const [greeting, setGreeting] = useState('Hello');

       const changeGreeting = () => setGreeting('Hi');
       
       return (
         <div>
           <h1>{greeting}, {name}!</h1>
           <button onClick={changeGreeting}>Change Greeting</button>
         </div>
       );
     }
     ```
3. **Write a test to simulate the button click**:
   ```javascript
   import { render, screen, fireEvent } from '@testing-library/react';
   import Greeting from './Greeting';

   test('changes greeting on button click', () => {
     render(<Greeting name="Alice" />);
     const button = screen.getByText(/Change Greeting/i);
     fireEvent.click(button);
     const greetingElement = screen.getByText(/Hi, Alice!/i);
     expect(greetingElement).toBeInTheDocument();
   });
   ```
4. **Key takeaway**:
   - Use `fireEvent.click()` to simulate user clicks.
   - Verify that the component updates as expected after the interaction.

---

## Home Task: Write Tests for a Component with Props and State
1. **Task**:
   - Write tests for a component that accepts props and has internal state.
   - The component should render the passed-in data and allow interaction (e.g., changing state on a button click).
2. **Example Component**:
   ```javascript
   function Counter({ initialCount }) {
     const [count, setCount] = useState(initialCount);

     const increment = () => setCount(count + 1);

     return (
       <div>
         <p>Count: {count}</p>
         <button onClick={increment}>Increment</button>
       </div>
     );
   }
   ```

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

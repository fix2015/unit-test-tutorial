# Day 5: Testing React Components ⚛️

### Teacher’s Guide: Explaining Day 5

---

## 0-5 minutes: Review the Home Task from Day 4
- **Start with a quick review**:
  - Ask students how they approached testing for a component with props and state.
  - **Ask Questions**:
    - "What was the most challenging part of writing tests for components?"
    - "How did you test components with both state and props?"
  - **Reinforce Concepts**:
    - Remind them that testing React components involves rendering the component, interacting with it, and verifying its behavior.
  - **Encourage Sharing**:
    - Let students share any interesting or tricky edge cases they encountered.

---

## 5-10 minutes: Set Up React Testing Library
- **Explain the need for React Testing Library**:
  - "React Testing Library helps us test components in a way that mimics how they would behave in the real world, using actual DOM elements."
- **Walk through the installation**:
  - Ensure everyone installs the required libraries:
    ```bash
    npm install --dev @testing-library/react @testing-library/jest-dom
    ```
- **Discuss key concepts**:
  - **render()**: Renders the component for testing.
  - **screen**: Provides access to the DOM.
  - **fireEvent**: Simulates user interactions.
- **Engage Students**:
  - Ask, "Why do you think React Testing Library is better for testing React components than traditional unit tests?"

---

## 10-20 minutes: Write Tests for a Functional React Component
- **Explain the task**:
  - Introduce a simple functional component like `Greeting`.
  - Show how to write a basic test:
    ```javascript
    import { render, screen } from '@testing-library/react';
    import Greeting from './Greeting';

    test('renders a greeting message', () => {
      render(<Greeting name="Alice" />);
      const greetingElement = screen.getByText(/Hello, Alice!/i);
      expect(greetingElement).toBeInTheDocument();
    });
    ```
- **Explain key concepts**:
  - **render()**: Renders the component into the virtual DOM.
  - **screen.getByText()**: Searches the DOM for the text and returns the matching element.
  - **expect()**: Checks that the element is present in the document.
- **Ask Questions**:
  - "Why do we use `screen.getByText()` instead of directly accessing the DOM?"
  - "What might happen if we didn’t include the `i` flag in `getByText()`?"

---

## 20-30 minutes: Test User Interactions Using `fireEvent`
- **Introduce `fireEvent`**:
  - "Testing user interactions like clicks or typing is essential for ensuring that your components respond correctly."
- **Show an example**:
  - Update the `Greeting` component to include a button that changes the greeting when clicked:
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
- **Write a test to simulate a click**:
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
- **Engage Students**:
  - Ask, "What other interactions could we simulate with `fireEvent`? What about keyboard events or form submissions?"

---

## Home Task: Write Tests for a Component with Props and State
- **Introduce the task**:
  - "Now, you’ll write tests for a `Counter` component that accepts a prop and maintains internal state."
  - Provide the component:
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
- **Explain what they need to do**:
  - Write tests to verify:
    - The component renders the correct initial count.
    - The count updates when the button is clicked.
- **Encourage edge case testing**:
  - What if the initial count is negative? What if the user clicks the button multiple times in rapid succession?

---

## Closing Notes
- **Recap**:
  - Emphasize how testing React components involves rendering the component, interacting with it, and verifying its behavior.
  - Stress the importance of testing components with props and state, as they represent common patterns in React apps.
- **Encourage Engagement**:
  - "The more tests you write, the more confident you can be in the stability of your app!"
- **Homework Reminder**:
  - "Write tests for the `Counter` component and test different initial values. Try to simulate rapid button clicks!"

---

### Tips for Effective Teaching
1. **Encourage Collaboration**:
   - Allow students to pair up and review each other’s tests to promote peer learning.
2. **Demonstrate Live**:
   - Walk through the coding and testing process live so students can follow along.
3. **Praise Student Efforts**:
   - Celebrate successful tests and creative approaches to edge case testing.
4. **Real-World Insight**:
   - Mention that writing tests for components ensures that UI interactions work as expected, preventing bugs in production.

---

## Connect with Me:
- [LinkedIn - Vitalii Semianchuk](https://www.linkedin.com/in/vitalii-semianchuk-9812a786/)  
- [Telegram - @jsmentorfree](https://t.me/jsmentorfree) - We do a lot of free teaching on this channel! Join us to learn and grow in web development.  
- [Tiktok - @jsmentoring](https://www.tiktok.com/@jsmentoring) Everyday new videos  
- [Youtube - @jsmentor-uk](https://www.youtube.com/@jsmentor-uk) Mentor live streams  
- [Dev.to - fix2015](https://dev.to/fix2015) Javascript featured, live, experience

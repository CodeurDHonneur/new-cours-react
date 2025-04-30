```css
/* App.css - style global */
body {
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  background-color: #f0f2f5;
  margin: 0;
  padding: 0;
}

h1 {
  margin-top: 30px;
  color: #2c3e50;
  text-align: center;
}

/* Calculator.module.css */
.calculator {
  width: 300px;
  margin: 40px auto;
  padding: 20px 25px;
  border: 1px solid #ccc;
  border-radius: 16px;
  background: white;
  box-shadow: 0 6px 16px rgba(0, 0, 0, 0.1);
  transition: box-shadow 0.3s ease;
}

.calculator:hover {
  box-shadow: 0 10px 24px rgba(0, 0, 0, 0.2);
}

.calculatorImage {
  width: 100%;
  height: auto;
  border-radius: 12px;
  margin-bottom: 15px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.calculatorImage:hover {
  transform: scale(1.03);
  box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2);
}

/* Display.module.css */
.display {
  padding: 12px 10px;
  border-radius: 8px;
  background: #f0f0f0;
  border: 1px solid #ddd;
  font-size: 20px;
  margin-bottom: 16px;
  text-align: right;
  display: flex;
  flex-direction: column;
  gap: 6px;
}

.flexElement {
  display: flex;
  flex-direction: column;
  justify-content: space-around;
}

.result {
  color: #0077cc;
  font-weight: bold;
}

/* Button.module.css */
.button {
  width: 48px;
  height: 48px;
  font-size: 18px;
  margin: 6px;
  cursor: pointer;
  border: none;
  border-radius: 8px;
  background-color: #e4e4e4;
  transition: all 0.2s ease;
  box-shadow: 0 2px 4px rgba(0,0,0,0.1);
}

.buttonHover {
  background-color: #ccc;
}
```
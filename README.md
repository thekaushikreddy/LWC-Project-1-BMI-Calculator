# LWC-Project-1-BMI-Calculator



# Project 1: BMI Calculator — Salesforce Lightning Web Component

A responsive BMI (Body Mass Index) calculator built as a Salesforce Lightning Web Component (LWC). Users can enter their height in centimeters and weight in kilograms, calculate their BMI, view the corresponding weight category, and reset the calculator to start again.

## Features

- Accepts height in centimeters and weight in kilograms
- Calculates BMI using the metric BMI formula
- Displays the BMI value rounded to two decimal places
- Classifies the result as:
  - Underweight
  - Healthy
  - Overweight
  - Obese
- Provides a BMI category reference guide
- Includes a **Re-Calculate** option to reset the form
- Uses Salesforce Lightning Design System (SLDS) utility classes
- Can be added to a Salesforce Lightning App Page
- Supports a custom background through a Salesforce Static Resource

## BMI Formula

```text
BMI = weight in kilograms / (height in meters × height in meters)
```

Example:

```text
Height: 175 cm
Weight: 70 kg

BMI = 70 / (1.75 × 1.75)
BMI = 22.86
Category = Healthy
```

## BMI Categories

| BMI Range | Category |
|---|---|
| Below 18.5 | Underweight |
| 18.5 to 24.9 | Healthy |
| 25.0 to 29.9 | Overweight |
| 30.0 and above | Obese |

## Technology Stack

- Salesforce Lightning Web Components
- JavaScript
- HTML
- CSS
- Salesforce Lightning Design System
- Salesforce Metadata API

## Project Structure

```text
bmiCalculator/
├── bmiCalculator.html
├── bmiCalculator.js
├── bmiCalculator.css
└── bmiCalculator.js-meta.xml
```

### File Responsibilities

| File | Purpose |
|---|---|
| `bmiCalculator.html` | Defines the input form, result section, BMI reference information, and action buttons |
| `bmiCalculator.js` | Handles user input, BMI calculation, category assignment, and form reset |
| `bmiCalculator.css` | Provides custom colors, spacing, layout, typography, and background styling |
| `bmiCalculator.js-meta.xml` | Exposes the component to supported Salesforce Lightning pages |

## Prerequisites

Before deploying this component, make sure you have:

- A Salesforce org with Lightning Experience enabled
- Salesforce CLI installed
- Visual Studio Code with the Salesforce Extension Pack
- An authenticated Salesforce org
- A Salesforce DX project

## Installation

### 1. Clone the repository

```bash
git clone https://github.com/your-username/bmi-calculator.git
cd bmi-calculator
```

### 2. Add the component to your Salesforce project

Place the component folder inside:

```text
force-app/main/default/lwc/bmiCalculator/
```

The final structure should look like this:

```text
force-app/
└── main/
    └── default/
        └── lwc/
            └── bmiCalculator/
                ├── bmiCalculator.html
                ├── bmiCalculator.js
                ├── bmiCalculator.css
                └── bmiCalculator.js-meta.xml
```

### 3. Create the background Static Resource

The component CSS references the following Salesforce Static Resource:

```text
BmiAppBackground
```

Create or upload an image as a Static Resource with that exact name.

The resource is referenced in the component as:

```css
background-image: url(/sfsites/c/resource/BmiAppBackground);
```

If you do not need a background image, remove or replace this declaration in `bmiCalculator.css`.

### 4. Deploy the component

Using Salesforce CLI:

```bash
sf project deploy start --source-dir force-app/main/default/lwc/bmiCalculator
```

For older Salesforce CLI versions:

```bash
sfdx force:source:deploy -p force-app/main/default/lwc/bmiCalculator
```

## Add the Component to a Lightning App Page

1. Open **Setup** in Salesforce.
2. Search for **Lightning App Builder**.
3. Create a new App Page or edit an existing App Page.
4. Find the **bmiCalculator** component under Custom Components.
5. Drag the component onto the page.
6. Save and activate the page.

## Usage

1. Enter your height in centimeters.
2. Enter your weight in kilograms.
3. Select **Calculate**.
4. Review the calculated BMI and weight category.
5. Select **Re-Calculate** to clear the result and enter new values.

## Core Calculation Logic

```javascript
const heightInMeters = Number(this.height) / 100;
const bmi = Number(this.weight) / (heightInMeters * heightInMeters);

this.bmiValue = Number(bmi.toFixed(2));
```

The result is then classified using standard BMI ranges.

## Component Configuration

The component is currently exposed to:

```xml
<target>lightning__AppPage</target>
```

To make it available on additional Lightning pages, you can add targets such as:

```xml
<target>lightning__HomePage</target>
<target>lightning__RecordPage</target>
```

Example:

```xml
<targets>
    <target>lightning__AppPage</target>
    <target>lightning__HomePage</target>
    <target>lightning__RecordPage</target>
</targets>
```

## Possible Enhancements

- Add support for feet, inches, and pounds
- Add input validation for unrealistic height and weight values
- Add a visual BMI scale or progress indicator
- Add Jest unit tests
- Improve accessibility with validation messages and ARIA attributes
- Store previous calculations
- Add mobile-specific styling
- Replace `console.log` statements with production-ready error handling
- Add configurable labels through Custom Labels
- Support multiple languages

## Screenshots

Add screenshots to an `assets` folder and reference them here:

```markdown
![BMI Calculator](assets/bmi-calculator.png)
```

## Medical Disclaimer

This application is intended for educational and demonstration purposes only. BMI is a general screening measure and does not account for factors such as muscle mass, age, body composition, or individual medical conditions. It should not be treated as medical advice.

## Contributing

Contributions are welcome.

1. Fork the repository.
2. Create a feature branch:

   ```bash
   git checkout -b feature/your-feature-name
   ```

3. Commit your changes:

   ```bash
   git commit -m "Add your feature"
   ```

4. Push the branch:

   ```bash
   git push origin feature/your-feature-name
   ```

5. Open a pull request.

## License

This project is available for educational and portfolio use. Add a `LICENSE` file to define the exact terms under which others may use, modify, and distribute the project.

## Author

**Kaushik**

Salesforce Developer

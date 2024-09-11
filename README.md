# MultiSelectPicklistHandler

## Overview

The `MultiSelectPicklistHandler` Apex class is designed to handle Salesforce Multi-Select Picklist fields and can be invoked within Salesforce Flows as an Invocable Action. The class replaces semicolons (`;`) that separate Multi-Select Picklist options with line breaks (`\n`), allowing the selections to be displayed more clearly in outputs like emails or reports.

This repository also includes a corresponding test class (`MultiSelectPicklistHandlerTest`) to ensure the functionality of the handler method.

---

## MultiSelectPicklistHandler Class

### Purpose

The `MultiSelectPicklistHandler` class contains an Invocable Method that processes Multi-Select Picklist values passed from Salesforce Flows. Its main function is to replace semicolons, which Salesforce uses to delimit Multi-Select Picklist values, with line breaks to improve readability.

### Key Features

- **Invocable Variable**:  
  The class accepts a required input in the form of a string (`picklistValues`) that contains the selected values of a Multi-Select Picklist, separated by semicolons.

- **Invocable Method**:  
  The main method, `replaceSemicolonWithLineBreak`, processes the input and replaces all semicolons with line breaks. The method returns the transformed string, which is useful in displaying Multi-Select Picklist selections in a more readable format.

- **Inner Request Class**:  
  An inner class (`Request`) defines the structure of the input. The `picklistValues` variable is marked as `required`, ensuring that it must be populated when called from a Flow.

### Usage in Flow

This class can be used as an action in Salesforce Flows. After a Flow collects Multi-Select Picklist values, the Invocable Method can be called to format those values with line breaks, which can then be used in various output formats like email templates or screen components.

---

## MultiSelectPicklistHandlerTest Class

### Purpose

The `MultiSelectPicklistHandlerTest` class ensures that the `MultiSelectPicklistHandler` class functions as expected. It creates a test scenario where a Contact record is created and the Multi-Select Picklist values are processed, ensuring that semicolons are properly replaced with line breaks.

### Key Features

- **Contact Record Creation**:  
  A test `Contact` record is created with a sample Multi-Select Picklist value (simulated by storing semicolon-separated values in the `Description` field). This ensures that the method works with real records and demonstrates how the class would function in a live environment.

- **Bypassing Validation Rules**:  
  To avoid issues with validation rules during testing, the test class uses the `allOrNone = false` setting when inserting records. This allows the test to proceed even if certain validation rules fail.

- **Processing the Multi-Select Picklist**:  
  The test simulates setting the Multi-Select Picklist values and ensures that the `replaceSemicolonWithLineBreak` method is called properly. It verifies that the method replaces semicolons with line breaks in the returned string.

- **Assertions**:  
  The test class verifies that the output from the Invocable Method matches the expected format, with each Multi-Select Picklist option on a new line.

---

## How to Use

1. **Deploy the Apex Class**:  
   Deploy the `MultiSelectPicklistHandler` class to your Salesforce org.
   
2. **Configure in Flow**:  
   Add the Invocable Method (`Replace Semicolon with Line Break`) as an action in your Flow to process Multi-Select Picklist values.

3. **Run Tests**:  
   Run the `MultiSelectPicklistHandlerTest` class to validate that the functionality is working as expected in your org.

---

## Contact

For questions or issues, please contact the repository owner.

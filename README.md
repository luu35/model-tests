# AI Report Generation Test Suite

This repository contains a test suite for evaluating the performance of an AI model that generates reports. The suite assesses the quality of the generated reports across several key metrics:

* **Completeness:** Measures how well the report includes all expected fields.
* **Contextual Accuracy:** Evaluates the correctness of the information in the report relative to the input data.
* **Hallucination-Free:** Checks for the presence of fabricated or incorrect information.
* **Legal Comprehension:** Determines if the report correctly applies relevant legal rules.
* **Data Interpretation:** Assesses the accuracy of the report's data analysis.

## Getting Started

### Prerequisites

* Python 3.x
* `unittest` (standard library)

### Installation

1.  Clone the repository:

    ```bash
    git clone <repository_url>
    cd <repository_directory>
    ```

2.  (Optional) Create a virtual environment:

    ```bash
    python3 -m venv venv
    source venv/bin/activate  # On macOS/Linux
    venv\Scripts\activate      # On Windows
    ```

### Usage

1.  **Prepare Test Data:**
    * Modify the `load_test_data()` function in `test_report.py` to load your test data. Ensure the data is in a format that your AI model expects.

2.  **Load AI Model:**
    * Modify the `load_ai_model()` function in `test_report.py` to load your AI model. The model should have a `generate_report(data)` method that takes input data and returns a report (ideally a dictionary).

3.  **Adjust Score Calculation Logic:**
    * The `calculate_completeness_score()`, `calculate_contextual_accuracy_score()`, `calculate_hallucination_free_score()`, `calculate_legal_comprehension_score()`, and `calculate_data_interpretation_score()` functions in `test_report.py` contain example logic. You **must** replace this logic with your specific requirements and data structures.
    * Pay close attention to the regex used for legal terms, and adjust the example conditional logic in the legal and data interpretation functions.

4.  **Run the Tests:**

    ```bash
    python3 -m unittest test_report.py
    ```

5.  **View the Report:**
    * The test suite will print the report metrics for each data point in JSON format to the console.

### Test Script Explanation

The `test_report.py` script uses the `unittest` framework to automate the testing process. Key components include:

* **`TestAIReportGeneration` Class:** This class defines the test suite and contains the test methods.
* **`setUp()` Method:** This method loads the test data and AI model before each test.
* **`test_report_generation()` Method:** This method iterates through the test data, generates reports, calculates scores, and prints the results.
* **Score Calculation Functions:** These functions implement the algorithms for calculating the various metrics.
* **`load_test_data()` and `load_ai_model()` Functions:** These functions load the test data and AI model.

### Customization

* Modify the `expected_fields`, `fields_to_compare`, `legal_rules`, and `interpretations` lists to match your data.
* Implement more sophisticated logic in the score calculation functions as needed.
* Add more test cases to cover different scenarios.
* Integrate the test suite into your CI/CD pipeline.

### Example JSON Output

```json
{
    "Completeness_Score": 0.75,
    "Contextual_Accuracy_Score": 1.0,
    "Hallucination_Free_Score": 0.8,
    "Legal_Comprehension_Score": 1.0,
    "Data_Interpretation_Score": 1.0
}

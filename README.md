
# ContactLensCalculator Application

## Overview

The **ContactLensCalculator** application is a desktop tool designed for validating and calculating contact lens parameters based on user input. It provides features for analyzing eye test data (SPH, CYL, AXIS, etc.) and converting them into precise lens values (spherical and toric).
## Features

- User-friendly interface built with PyQt5.
- Validates eye test data such as SPH, CYL, and AXIS.
- Converts input data into lens types (Spheric and Toric).
- Displays results in a clear and organized table.
- Custom styling for enhanced usability and visual appeal.

## Installation

### Prerequisites
- Python 3.8 or later
- Required Python libraries: `PyQt5`

### Steps
1. Clone the repository:
   ```bash
   git clone <repository_url>
   ```
2. Navigate to the project directory:
   ```bash
   cd EyeContactLens
   ```
3. Install the required dependencies:
   ```bash
   pip install -r requirements.txt
   ```
4. Run the application:
   ```bash
   python EyeContactLens.py
   ```

## Usage

1. Launch the application.
2. Enter eye test parameters (e.g., SPH, CYL, AXIS) into the input table.
3. Click the **Calculate** button to validate and process the input data.
4. Review the calculated lens values in the results table.

## File Structure

- **EyeContactLens.py**: Main application file for GUI setup and functionality.
- **py/**: Directory containing helper modules:
  - `EyeContactLensValidator`: Validates and formats contact lens data.
  - `EyeTestValidator`: Handles eye test data validation.
  - `functian`: Provides utility functions like loading stylesheets.
- **static/**: Directory for static resources, including stylesheets (`lens_table_styles.qss`).

## Key Functions

### From `EyeTestValidator.py`

#### `is_multiple_of_quarter(value)`
Checks if a value is a multiple of 0.25.
- **Parameters:**
  - `value` (str): The value to check.
- **Returns:**
  - `bool`: True if the value is valid, False otherwise.

#### `is_valida_eye_test_power(value)`
Formats and validates eye test power values.
- **Parameters:**
  - `value` (str): The value to validate.
- **Returns:**
  - `str`: Formatted value or `False` if invalid.

#### `check_axis(value)`
Validates the axis value (1-180).
- **Parameters:**
  - `value` (str): Axis value.
- **Returns:**
  - `bool`: True if valid, False otherwise.

#### `check_pd(value)`
Validates the PD (Pupillary Distance) value (19-85).
- **Parameters:**
  - `value` (str): PD value.
- **Returns:**
  - `bool`: True if valid, False otherwise.

#### `remove_sign(value)`
Removes the sign from a value and formats it to 2 decimal places.
- **Parameters:**
  - `value` (str): Value to format.
- **Returns:**
  - `str`: Formatted value or `None` if invalid.

#### `check_add(value)`
Validates the ADD (Addition) value (0.25-4).
- **Parameters:**
  - `value` (str): Addition value.
- **Returns:**
  - `bool`: True if valid, False otherwise.

#### `power_format(data)`
Formats SPH, CYL, and AX values based on rules.
- **Parameters:**
  - `data` (dict): Dictionary of values.
- **Returns:**
  - `dict`: Formatted values.

#### `cheek_cyl_ax_not_null(data)`
Checks if CYL and AX values are not null or inconsistent.
- **Parameters:**
  - `data` (dict): Dictionary with CYL and AX values.
- **Returns:**
  - `bool`: True if valid, False otherwise.

#### `check_SG(value)`
Validates the SG value (7-50).
- **Parameters:**
  - `value` (str): SG value.
- **Returns:**
  - `bool`: True if valid, False otherwise.

#### `Check_vertex_distance(value)`
Validates the Back Vertex Distance (10-14).
- **Parameters:**
  - `value` (str): Distance value.
- **Returns:**
  - `bool`: True if valid, False otherwise.

### From `EyeContactLensValidator.py`

#### `convert_to_spheric(data)`
Converts eyeglass prescriptions to spherical contact lens prescriptions.
- **Parameters:**
  - `data` (dict): Dictionary containing SPH, CYL, AX, ADD, and BV values.
- **Returns:**
  - `dict`: Spherical contact lens prescription.

#### `convert_to_toric(data)`
Converts eyeglass prescriptions to toric contact lens prescriptions.
- **Parameters:**
  - `data` (dict): Dictionary containing SPH, CYL, AX, ADD, and BV values.
- **Returns:**
  - `dict`: Toric contact lens prescription.

#### `spheric_without_vertex_distance(sphere, vertex_distance)`
Calculates spherical power adjusted for vertex distance.
- **Parameters:**
  - `sphere` (float): Sphere value.
  - `vertex_distance` (float): Vertex distance (e.g., 12mm).
- **Returns:**
  - `float`: Adjusted spherical power.

#### `spherical_equivalent(sphere, cylinder)`
Calculates the spherical equivalent for a given sphere and cylinder.
- **Parameters:**
  - `sphere` (float): Sphere value.
  - `cylinder` (float): Cylinder value.
- **Returns:**
  - `float`: Spherical equivalent.

#### `round_to_nearest_quarter(num)`
Rounds a number to the nearest 0.25.
- **Parameters:**
  - `num` (float): Number to round.
- **Returns:**
  - `float`: Rounded number.

#### `format_result_to_quarter(value)`
Formats SPH and CYL values to the nearest 0.25.
- **Parameters:**
  - `value` (dict): Dictionary with SPH and CYL values.
- **Returns:**
  - `dict`: Formatted values.

#### `is_multiple_of_quarter(value)`
Checks if a value is a multiple of 0.25.
- **Parameters:**
  - `value` (str): Value to check.
- **Returns:**
  - `bool`: True if valid, False otherwise.

### From `EyeContactLens.py`

#### `init_ui()`
Sets up the user interface, including input tables, result tables, and buttons for validation.

#### `create_table(rows, cols, headers)`
Creates a table with the specified rows, columns, and headers.
- **Parameters:**
  - `rows` (int): Number of rows.
  - `cols` (int): Number of columns.
  - `headers` (list): List of column headers.

#### `validate_and_process_data()`
Validates the input data and processes it to calculate lens powers (spheric and toric).

#### `process_lens_data(filtered_data)`
Converts filtered eye test data into contact lens parameters.
- **Parameters:**
  - `filtered_data` (list): List of validated eye test data.
- **Returns:**
  - Processed lens data (list of dictionaries).

#### `update_result_table(lens_data)`
Populates the result table with processed lens data, applying styles and formatting.
- **Parameters:**
  - `lens_data` (list): List of dictionaries containing calculated lens parameters.

#### `validate_cell(row, col, value)`
Validates the value entered in a specific cell of the input table.
- **Parameters:**
  - `row` (int): Row index.
  - `col` (int): Column index.
  - `value` (str): Cell value.
- **Returns:**
  - A tuple indicating validity, formatted value, and whether the next cell should be updated.

## Development

### Customization
- Modify the UI or styles by updating `lens_table_styles.qss`.
- Extend functionality by editing the validator classes in the `py` directory.

### Running Tests
To test the application components:
1. Install `pytest`:
   ```bash
   pip install pytest
   ```
2. Run tests:
   ```bash
   pytest
   ```

## Acknowledgements

Developed by **Elhussein Taha**  
Version 1.0  

For queries or contributions, please contact [email@example.com].

## License

This project is licensed under the MIT License. See the `LICENSE` file for details.

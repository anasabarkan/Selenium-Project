# Weather Shopper Test Automation

This project includes automated end-to-end tests for the Weather Shopper e-commerce application using Selenium WebDriver and pytest.

## Project Structure

```
Selenium-Project/
├── conftest.py                 # Pytest configuration and fixtures
├── requirements.txt            # Python dependencies
├── pages/                      # Page Object Model classes
│   ├── home.py                # Home page interactions
│   ├── moisturizers.py        # Moisturizers page interactions
│   ├── sunscreens.py          # Sunscreens page interactions
│   ├── cart.py                # Cart page interactions
│   └── payment_page.py        # Payment/Stripe modal interactions
└── tests/
    └── test_weather_shopper.py # Main test scenarios
```

## Test Scenario

The automated test simulates a smart shopping flow based on the current temperature:

Temperature Check
Reads the current temperature from the homepage.

Product Selection Logic

If temperature < 19°C: Navigate to the moisturizers page and select products containing “Aloe” or “Almond”.

If temperature > 34°C: Navigate to the sunscreens page and select products containing “SPF-30” or “SPF-50”.

Otherwise: Skip the test.

Smart Shopping
Adds the two cheapest matching products to the cart.

Cart Verification
Verifies that two items are added and the total matches the expected price.

Payment Flow
Completes the checkout using Stripe test credentials.

## Prerequisites

* Python 3.7 or higher
* Microsoft Edge or Chrome browser installed

## Installation

1. Clone or extract the project files

   ```bash
   git clone https://github.com/ayman-gassi/Selenium-Weather-Project.git
   cd Selenium-Weather-Project
   ```
2. Install required dependencies:

```bash
pip install -r requirements.txt
```

## Running the Tests

### Basic Test Execution

```bash
pytest tests/test_weather_shopper.py -v
```

### Generate HTML Report

First create the reports directory, then run with HTML reporting:

```bash
mkdir reports
pytest tests/test_weather_shopper.py -v --html=reports/report.html --self-contained-html
```

The HTML report will be generated at `reports/report.html` and can be opened in any web browser.

## Test Configuration

### Browser Settings

* **Browser**: Microsoft Edge (configured in `conftest.py`)
* **Window**: Maximized on startup
* **Implicit Wait**: 5 seconds
* **Explicit Waits**: Up to 20 seconds for critical elements

### Test Data

The test uses Stripe's test payment credentials:

* **Email**: test@example.com
* **Card Number**: 4242424242424242
* **Expiry**: 12/34
* **CVC**: 123
* **ZIP Code**: 12345

## Page Object Model

The project follows the Page Object Model pattern with separate classes for each page:

* **HomePage**: Temperature reading and navigation
* **MoisturizersPage**: Product selection for cold weather
* **SunscreensPage**: Product selection for hot weather
* **CartPage**: Cart verification and checkout initiation
* **PaymentPage**: Stripe payment form handling

## Key Features

* **Smart Product Selection**: Automatically finds cheapest products matching temperature-based criteria
* **Robust Element Location**: Multiple fallback selectors for reliable element detection
* **Error Handling**: Comprehensive exception handling with detailed logging
* **Stripe Integration**: Handles iframe switching and payment form automation
* **Debug Capabilities**: Screenshot capture and detailed console output

## Expected Output

When running successfully, you should see output similar to:

🌡️ Detected temperature: 43°C
Searching for products with keywords: ['Aloe', 'Almond']
Found 6 matching products
🛒 Added to cart: Aloe Vera Fresh – 150 Rs
🛒 Added to cart: Almond Moist – 135 Rs
✅ Cart verified: 2 items, total = 285 Rs
✅ Test completed successfully – payment processed

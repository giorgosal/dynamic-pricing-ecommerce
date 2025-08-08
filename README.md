# AI-Powered Dynamic Pricing for E-Commerce

This project is a simple e-commerce product catalog viewer with **Dynamic Pricing** capability, implemented using both **rule-based logic** and a **machine learning model**.  
Users can filter products by category and maximum price, and the system automatically adjusts product prices based on demand, ratings, category, and weekend sales (mocked).  
The ML model is trained on mock data and considers multiple features to predict adjusted prices, including whether a weekend sale is active.

## How to Run

1. **Install requirements**  
   Make sure you have Python 3.8+ installed.  
   Install the required Python libraries:
   ```bash
   pip install pandas scikit-learn
   ```

2. **Ensure the `products.json` file is present**  
   Place the `products.json` file in the same folder as the Python script.

3. **Run the application**  
   In your terminal or command prompt, navigate to the project folder and run:
   ```bash
   python app.py
   ```
   If you are using Google Colab, simply upload both `app.py` and `products.json` and run the code cells.

4. **Follow the prompts**  
   - Enter a category (or leave blank for all)  
   - Enter a maximum price (or leave blank for no limit)  
   - Specify whether weekend sale is active (yes/no)  
   The system will then display:  
     - Original Price  
     - Rule-based Price  
     - ML Predicted Price  
     - Final Price Used (based on selection rules)

## AI Feature – Option B: Dynamic Pricing Engine

This project implements **Option B – Dynamic Pricing Engine**, enhancing the basic e-commerce catalog with automatic price adjustments.

The system uses two approaches:

1. **Rule-based logic** – Prices are adjusted according to predefined business rules:  
   - High rating (≥ 4.5) → +5% increase  
   - Popular category ("electronics") → +3% increase  
   - Expensive items (price > $500) → 5% discount  
   - Weekend sale active → 10% discount  

2. **Machine Learning model** – A simple **Linear Regression** model is trained on mock data to predict adjusted prices based on:  
   - Base price  
   - Rating  
   - Encoded category  
   - Estimated demand level (calculated automatically)  
   - Weekend sale flag (0 = no, 1 = yes)

The application compares both results and automatically selects the **final price** using these rules:
- If ML and rule-based prices differ by ≤ 5% → choose ML price.  
- If ML is >15% higher or lower than rule-based → choose rule-based price.  
- Otherwise → choose ML price.

## Bonus – Blockchain Integration Ideas

This dynamic pricing AI could be connected with blockchain technology to provide **transparent and verifiable pricing records**.  
Price changes could be stored on a blockchain ledger, allowing customers to verify that discounts and adjustments are genuine.  
A simple loyalty system could also be implemented using blockchain, where each purchase automatically adds points to a secure, tamper-proof record that the customer can redeem for future discounts.

## Tools & Libraries Used

- **Python 3.8+** – Core programming language for the application.
- **pandas** – For data manipulation and creation of the mock training dataset.
- **scikit-learn** – For encoding categorical data and training the Linear Regression model.
- **LabelEncoder** – From scikit-learn, used to transform product categories into numerical values for ML input.
- **json** – To load and manage the product catalog stored in `products.json`.
- **VS Code / Google Colab** – Development environments used for coding and testing.

## Assumptions & Limitations

- The ML model is trained on a **mock dataset** and does not use real sales data.  
- Demand level is **estimated automatically** based on product attributes and is not connected to live market data.  
- Weekend sale status is provided by the user at runtime and is not automatically detected.  
- The application runs locally and does not include a frontend UI; results are displayed in the console.


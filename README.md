# Modern API Suite

A comprehensive collection of FastAPI applications demonstrating modern web API development, including an e-commerce product management system and a machine learning-powered car price prediction API.

## 🚀 Projects Overview

### 1. FastAPI Ecommerce API (`FastAPI/fastapi-ecommerce/`)
A full-featured e-commerce product management API with CRUD operations, advanced validation, and business logic.

**Key Features:**
- Complete product CRUD operations
- Advanced filtering, sorting, and pagination
- Pydantic-based data validation with business rules
- JSON file-based persistence
- Comprehensive error handling
- Automatic API documentation

### 2. Car Price Prediction API (`model/car-price-api/`)
Machine learning API for predicting used car prices using Random Forest regression, with both REST API and Streamlit web interface.

**Key Features:**
- ML model serving via REST API
- Streamlit web application for user interaction
- One-hot encoding for categorical features
- CORS-enabled for web integration
- Pre-trained model with Cardekho dataset

## 📁 Project Structure

```
FastAPI project/
├── FastAPI/
│   └── fastapi-ecommerce/
│       ├── requirements.txt
│       └── app/
│           ├── main.py              # Main FastAPI application
│           ├── schema/
│           │   └── product.py       # Pydantic models
│           ├── service/
│           │   └── products.py      # Business logic
│           └── data/
│               └── products.json    # Sample product data
├── model/
│   └── car-price-api/
│       ├── main.py                  # FastAPI app
│       ├── schema.py                # Pydantic models
│       ├── model.py                 # ML prediction logic
│       ├── streamlit_app.py         # Web UI
│       ├── train.py                 # Model training
│       ├── requirements.txt
│       ├── random_forest_model.pkl  # Trained model
│       ├── feature_columns.pkl      # Feature metadata
│       └── cardekho_data (1).csv    # Training data
└── README.md
```

## 🛠️ Installation & Setup

### Prerequisites
- Python 3.8+
- pip package manager

### Ecommerce API Setup

```bash
cd FastAPI/fastapi-ecommerce

# Create virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install fastapi uvicorn pydantic python-dotenv

# Run the application
uvicorn app.main:app --reload
```

### Car Price Prediction API Setup

```bash
cd model/car-price-api

# Create virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Run the API
uvicorn main:app --reload

# Run the Streamlit app (in another terminal)
streamlit run streamlit_app.py
```

## 📖 API Documentation

### Ecommerce API Endpoints

#### Products Management
- `GET /` - API root with health check
- `GET /products` - List products with filtering options
  - Query parameters: `name`, `sort_by_price`, `order`, `limit`, `offset`
- `GET /products/{product_id}` - Get specific product
- `POST /products` - Create new product
- `PUT /products/{product_id}` - Update product
- `DELETE /products/{product_id}` - Delete product

#### Example Requests

**Get all products:**
```bash
curl http://localhost:8000/products
```

**Create a product:**
```bash
curl -X POST "http://localhost:8000/products" \
  -H "Content-Type: application/json" \
  -d '{
    "sku": "TEST-001-001",
    "name": "Test Product",
    "description": "A test product",
    "category": "electronics",
    "brand": "TestBrand",
    "price": 100.0,
    "stock": 10,
    "is_active": true,
    "rating": 4.5,
    "image_urls": ["https://example.com/image.jpg"],
    "dimensions_cm": {"length": 10, "width": 5, "height": 2},
    "seller": {
      "id": "123e4567-e89b-12d3-a456-426614174000",
      "name": "Test Seller",
      "email": "test@teststore.in",
      "website": "https://teststore.in"
    }
  }'
```

### Car Price Prediction API Endpoints

- `GET /` - Health check
- `POST /predict` - Predict car price

#### Example Request

```bash
curl -X POST "http://localhost:8000/predict" \
  -H "Content-Type: application/json" \
  -d '{
    "Car_Name": "swift",
    "Year": 2014,
    "Present_Price": 5.59,
    "Kms_Driven": 27000,
    "Fuel_Type": "Petrol",
    "Seller_Type": "Dealer",
    "Transmission": "Manual",
    "Owner": 0
  }'
```

## 🎯 Features & Validation

### Ecommerce API Features
- **Data Validation**: SKU format, email domains, business rules
- **Business Logic**: Stock management, discount validation
- **Computed Fields**: Final price calculation, volume computation
- **Error Handling**: Comprehensive HTTP exceptions
- **Filtering**: Name search, price sorting, pagination

### Car Price Prediction Features
- **ML Model**: Random Forest regression
- **Preprocessing**: Automatic one-hot encoding
- **Feature Engineering**: Categorical variable handling
- **Web Interface**: Streamlit-based user interface

## 🔧 Development

### Running Tests
```bash
# For ecommerce API
cd FastAPI/fastapi-ecommerce
python -m pytest

# For car price API
cd model/car-price-api
python -m pytest
```

### API Documentation Access
- Ecommerce API: http://localhost:8000/docs
- Car Price API: http://localhost:8000/docs

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📄 License

This project is released for research and educational use.


---

**Built with:**
- [FastAPI](https://fastapi.tiangolo.com/) - Modern Python web framework
- [Pydantic](https://pydantic-docs.helpmanual.io/) - Data validation
- [scikit-learn](https://scikit-learn.org/) - Machine learning
- [Streamlit](https://streamlit.io/) - Web app framework</content>

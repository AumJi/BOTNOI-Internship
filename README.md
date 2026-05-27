# Demand Forecasting & Inventory Optimization for Thai SME Supply Chain (BOTNOI-Intership)

<b>DS solution: </b> SME ในกลุ่ม supply chain ไทยลดความสูญเสียจาก stockout และ overstock ด้วย ML-powered demand forecasting และ inventory optimization

## Dataset
**Retail Store Inventory Forecasting Dataset** จาก Kaggle  
🔗 [https://www.kaggle.com/datasets/anirudhchauhan/retail-store-inventory-forecasting-dataset](https://www.kaggle.com/datasets/anirudhchauhan/retail-store-inventory-forecasting-dataset)

### ภาพรวมข้อมูล
- **จำนวนแถว:** 73,100 rows
- **ช่วงเวลา:** 2 ปี (2022-01-01 ถึง 2024-01-01)
- **จำนวนร้าน:** 5 stores
- **จำนวนสินค้า:** 20 products
- **หมวดหมู่:** 5 categories (Groceries, Toys, Electronics, Furniture, Clothing)

---

## 📋 คำอธิบาย Columns

| Column | ชื่อภาษาไทย | คำอธิบาย | ตัวอย่าง |
|--------|-------------|----------|----------|
| **Date** | วันที่ | วันที่ทำธุรกรรม | 2022-01-01 |
| **Store ID** | รหัสร้าน | รหัสเฉพาะของร้านค้า | S001, S002, ... |
| **Product ID** | รหัสสินค้า | รหัสเฉพาะของสินค้า | P0001, P0002, ... |
| **Category** | หมวดหมู่ | หมวดหมู่สินค้า | Groceries, Electronics, Clothing, Furniture, Toys |
| **Region** | ภูมิภาค | พื้นที่ทางภูมิศาสตร์ของร้านค้า | North, South, East, West |
| **Inventory Level** | สต็อกคงเหลือ | จำนวนสินค้าคงคลัง ณ ต้นวัน (หน่วย) | 231 |
| **Units Sold** | จำนวนที่ขายได้ | จำนวนหน่วยที่ขายได้ในวันนั้น | 127 |
| **Units Ordered** | จำนวนที่สั่งซื้อ | จำนวนหน่วยที่สั่งซื้อจาก supplier | 55 |
| **Demand Forecast** | พยากรณ์อุปสงค์ | อุปสงค์ที่คาดการณ์จากแนวโน้มในอดีต | 135.47 |
| **Price** | ราคาขาย | ราคาขายต่อหน่วย (บาท) | 33.50 |
| **Discount** | ส่วนลด | เปอร์เซ็นต์ส่วนลดที่ให้ (%) | 20 |
| **Weather Condition** | สภาพอากาศ | สภาพอากาศในวันนั้น | Sunny, Rainy, Cloudy, Snowy |
| **Holiday/Promotion** | วันหยุด/โปรโมชั่น | ตัวบ่งชี้ว่ามีโปรโมชั่นหรือไม่ | 0 (ไม่มี), 1 (มี) |
| **Competitor Pricing** | ราคาคู่แข่ง | ราคาของคู่แข่งสำหรับสินค้าเดียวกัน (บาท) | 29.69 |
| **Seasonality** | ฤดูกาล | ฤดูกาลของปี | Spring, Summer, Autumn, Winter |

---

## 🎯 Target Variables

**Primary Target:**
- `Units Sold` — จำนวนที่ขายได้ (สำหรับ demand forecasting)

**Secondary Targets:**
- `Inventory Level` — ระดับสต็อก (สำหรับ inventory optimization)
- `Units Ordered` — จำนวนสั่งซื้อ (สำหรับ reorder point calculation)

---

## 🔑 Key Features สำหรับ ML Model

### Time-based Features
- `Date` — วันที่สำหรับ time series analysis
- `Seasonality` — ฤดูกาลที่ส่งผลต่อ demand pattern

### Product & Store Features
- `Product ID`, `Category` — product hierarchy
- `Store ID`, `Region` — geographic patterns

### Pricing Features
- `Price` — ราคาขาย
- `Discount` — ส่วนลดที่มีผลต่อ demand
- `Competitor Pricing` — dynamic ของตลาด

### External Features
- `Weather Condition` — สภาพอากาศที่ส่งผลต่อพฤติกรรมการซื้อ
- `Holiday/Promotion` — event-driven demand spike

### Baseline
- `Demand Forecast` — baseline prediction เพื่อเทียบกับ model เรา

---

## 📁 Data Dictionary

### Categorical Variables
```
Category: 5 unique values [Groceries, Toys, Electronics, Furniture, Clothing]
Region: 4 unique values [North, South, East, West]
Weather Condition: 4 unique values [Sunny, Rainy, Cloudy, Snowy]
Seasonality: 4 unique values [Spring, Summer, Autumn, Winter]
```

### Numerical Variables
```
Inventory Level: integer (stock units)
Units Sold: integer (sales volume)
Units Ordered: integer (order quantity)
Demand Forecast: float (predicted demand)
Price: float (THB per unit)
Discount: integer (0-20%)
Competitor Pricing: float (THB per unit)
```

### Binary Variables
```
Holiday/Promotion: binary (0 = ไม่มีโปรโมชั่น, 1 = มีโปรโมชั่น)
```

---

## 🚀 Use Cases

1. **Demand Forecasting** — ทำนายยอดขายล่วงหน้า 4-12 สัปดาห์
2. **Inventory Optimization** — คำนวณ optimal reorder point และ safety stock
3. **Pricing Analysis** — วิเคราะห์ผลกระทบของราคาต่อ demand
4. **Promotion Planning** — ประเมิน ROI ของโปรโมชั่น
5. **Seasonal Trend Analysis** — เข้าใจ demand pattern ตามฤดูกาล

---

## 📖 Example Analyses

### 1. Exploratory Data Analysis (EDA)
- Sales trend by category, region, seasonality
- Correlation analysis ระหว่าง price, discount กับ sales
- Outlier detection และ data quality check

### 2. Time Series Forecasting
- ARIMA / SARIMA models
- Prophet (Facebook's forecasting tool)
- LSTM / GRU (Deep Learning)
- XGBoost / LightGBM (Gradient Boosting)

### 3. Inventory Optimization
- Safety stock calculation จาก demand variability
- Reorder point optimization
- Stockout risk analysis

---

## 📝 Notes

- Dataset เป็น **synthetic data** สำหรับฝึกทักษะ inventory management และ demand forecasting
- เหมาะสำหรับ proof-of-concept และ academic projects
- ข้อมูลครอบคลุม external factors (weather, competitor) ที่หายากใน public datasets

---

## 📚 Citation

```
Anirudh Chauhan. (2024). Retail Store Inventory Forecasting Dataset. 
Kaggle. https://www.kaggle.com/datasets/anirudhchauhan/retail-store-inventory-forecasting-dataset
```

---

## 📧 Contact

สำหรับคำถามเกี่ยวกับโปรเจคนี้ กรุณาติดต่อผ่าน [ช่องทางของคุณ]
# Restaurant Delivery Management System

A comprehensive web-based management system for restaurant delivery operations, including order tracking, delivery personnel assignments, and real-time status updates.

## Features

✅ **Manage Restaurant Orders** - Create and track all restaurant orders
✅ **Assign Deliveries to Staff** - Allocate deliveries to delivery personnel
✅ **Track Delivery Status** - Real-time delivery status tracking
✅ **Customer Feedback** - Collect ratings and feedback on deliveries
✅ **Delivery Time Analysis** - Analyze delivery times for optimization
✅ **Staff Management** - Manage delivery personnel and their performance
✅ **Advanced Reporting** - Daily reports, staff performance, delayed orders
✅ **Database Procedures & Functions** - SQL procedures for complex operations
✅ **Views & Queries** - Pre-built views and nested queries for analytics

## Technology Stack

- **Backend**: Flask (Python)
- **Database**: MySQL
- **Frontend**: HTML5, CSS3, JavaScript
- **Server**: Flask Development Server

## Project Structure

```
restaurant_delivery/
├── app.py                          # Main Flask application
├── requirements.txt                # Python dependencies
├── README.md                       # This file
├── database/
│   └── restaurant_delivery.sql     # SQL database schema
├── templates/                      # HTML templates
│   ├── index.html                 # Home page
│   ├── dashboard.html             # Dashboard
│   ├── customers.html             # Customer management
│   ├── orders.html                # Order management
│   ├── staff.html                 # Staff management
│   ├── deliveries.html            # Delivery management
│   ├── customer_orders.html       # Customer order history
│   ├── daily_report.html          # Daily delivery report
│   ├── staff_performance.html     # Staff performance report
│   └── delayed_orders.html        # Delayed orders report
├── static/
│   ├── css/
│   │   └── style.css              # Main stylesheet
│   └── js/
│       └── script.js              # Client-side JavaScript
```

## Prerequisites

- Python 3.7 or higher
- MySQL Server (running)
- pip (Python package manager)

## Installation & Setup

### Step 1: Install Python Dependencies

```bash
cd restaurant_delivery
pip install -r requirements.txt
```

### Step 2: Setup MySQL Database

1. Open MySQL command prompt or MySQL Workbench
2. Run the SQL script to create the database:

```bash
mysql -u root -p < database/restaurant_delivery.sql
```

Or manually:
1. Open MySQL Workbench
2. Connect to your MySQL server
3. File → Open SQL Script → Select `database/restaurant_delivery.sql`
4. Click the lightning bolt icon to execute

### Step 3: Configure Database Connection

Open `app.py` and update the MySQL configuration:

```python
app.config['MYSQL_HOST'] = 'localhost'      # Your MySQL host
app.config['MYSQL_USER'] = 'root'           # Your MySQL username
app.config['MYSQL_PASSWORD'] = ''           # Your MySQL password
app.config['MYSQL_DB'] = 'restaurant_delivery'
```

### Step 4: Run the Application

```bash
python app.py
```

The application will start on `http://localhost:5000`

## Usage

### 1. **Dashboard**
   - View system statistics
   - Quick access to main features
   - See summary of operations

### 2. **Customers Management**
   - Add new customers
   - View customer details
   - View customer order history
   - Delete customers

### 3. **Orders Management**
   - Create new orders
   - Assign orders to customers
   - Update order status
   - Track order details

### 4. **Staff Management**
   - Add delivery staff members
   - View staff details
   - Manage staff status (Active/Inactive)

### 5. **Deliveries Management**
   - Assign deliveries to staff
   - Update delivery status
   - Record delivery time
   - Collect customer feedback and ratings

### 6. **Reports & Analytics**
   - **Daily Delivery Report** - Summary of daily deliveries
   - **Staff Performance** - Individual staff performance metrics
   - **Delayed Orders** - Orders delivered beyond 45 minutes

## SQL Features

### Stored Procedures
1. **AssignDeliveryStaff()** - Assigns a delivery to a staff member
2. **UpdateOrderStatus()** - Updates order status with automatic delivery synchronization

### Functions
1. **CalculateAverageDeliveryTime()** - Calculates average delivery time for a staff member

### Views
1. **DailyDeliveryReport** - Daily summary of deliveries
2. **StaffDeliveryPerformance** - Staff performance metrics
3. **OrdersWithDelayedDelivery** - Orders with delivery > 45 minutes

### Queries
1. **Orders not delivered within 30 minutes** - Nested query
2. **Staff with most deliveries** - Aggregated query with subquery
3. **Customer with highest orders** - Customer analytics
4. **Order and delivery status** - Join-based query
5. **Delivery summary by date** - Date-wise aggregation
6. **Staff-wise delivery count** - Staff performance metrics

## API Endpoints

### Customers
- `GET /customers` - View all customers
- `POST /customers` - Add new customer
- `GET /customer/<id>/orders` - View customer orders
- `POST /customer/<id>/delete` - Delete customer

### Orders
- `GET /orders` - View all orders
- `POST /orders` - Create new order
- `PUT /order/<id>/status` - Update order status

### Staff
- `GET /staff` - View all staff
- `POST /staff` - Add new staff member
- `POST /staff/<id>/delete` - Delete staff

### Deliveries
- `GET /deliveries` - View all deliveries
- `POST /deliveries` - Assign delivery
- `PUT /delivery/<id>/update` - Update delivery status

### Reports
- `GET /reports/daily` - Daily delivery report
- `GET /reports/staff-performance` - Staff performance report
- `GET /reports/delayed-orders` - Delayed orders report
- `GET /dashboard` - Dashboard statistics

## Sample Data

The database includes sample data:

**Customers**
- Ravi Kumar (9123456789)
- Priya Singh (8234567890)
- Amit Patel (7345678901)
- Sneha Sharma (6456789012)
- Rahul Verma (5567890123)

**Delivery Staff**
- Ajay Kumar (9876543210)
- Bhavesh Nair (9876543211)
- Chirag Singh (9876543212)
- Deepak Rao (9876543213)

**Sample Orders & Deliveries**
- Multiple orders assigned to customers
- Sample deliveries with times and ratings

## Features & Functionality

### 1. Real-time Status Updates
Track orders from Pending → In Transit → Delivered

### 2. Delivery Assignment
Intelligently assign deliveries to available staff members

### 3. Performance Metrics
- Average delivery time per staff member
- Customer satisfaction ratings
- Delivery completion rates

### 4. Advanced Filtering
- Find delayed deliveries
- Identify high-performing staff
- Analyze customer ordering patterns

### 5. Customer Feedback
- Collect ratings and feedback
- Track customer satisfaction
- Improve service quality

## Troubleshooting

### Issue: "No module named 'flask'"
**Solution**: Run `pip install -r requirements.txt`

### Issue: MySQL connection error
**Solution**: 
1. Ensure MySQL is running
2. Check username and password in app.py
3. Verify database exists: `SHOW DATABASES;`

### Issue: Database not created
**Solution**: Run the SQL script: `mysql -u root -p < database/restaurant_delivery.sql`

### Issue: Port 5000 already in use
**Solution**: Modify the port in app.py: `app.run(port=5001)`

## Key Functions

### Database Functions

```sql
-- Get average delivery time for a staff member
SELECT CalculateAverageDeliveryTime(staff_id);

-- Assign delivery to staff
CALL AssignDeliveryStaff(order_id, staff_id, delivery_date);

-- Update order status
CALL UpdateOrderStatus(order_id, new_status);
```

### Python Routes

```python
@app.route('/') - Home page
@app.route('/dashboard') - Dashboard
@app.route('/customers') - Customer management
@app.route('/orders') - Order management
@app.route('/staff') - Staff management
@app.route('/deliveries') - Delivery management
@app.route('/reports/<report_type>') - Various reports
```

## Performance Tips

1. **Database Indexing**: Indexes are automatically created on primary/foreign keys
2. **Query Optimization**: Use views for complex queries
3. **Caching**: Consider implementing caching for frequently accessed reports
4. **Database Connection Pool**: Use connection pooling for better performance

## Security Considerations

1. Change the secret key in production: `app.secret_key = 'your-secret-key-here'`
2. Use environment variables for database credentials
3. Implement user authentication and authorization
4. Validate all user inputs
5. Use HTTPS in production

## Future Enhancements

- [ ] User authentication and authorization
- [ ] Email notifications for delivery status
- [ ] SMS alerts to customers
- [ ] Mobile app integration
- [ ] Real-time GPS tracking
- [ ] Invoice generation
- [ ] Advanced search and filtering
- [ ] Data export (PDF, Excel)
- [ ] Dashboard charts and graphs
- [ ] Payment gateway integration

## Support & Documentation

For more information, please refer to:
- Flask Documentation: https://flask.palletsprojects.com/
- MySQL Documentation: https://dev.mysql.com/doc/
- Flask-MySQLdb: https://flask-mysqldb.readthedocs.io/

## License

This project is open source and available under the MIT License.

## Author

The Restaurant Delivery Management System was created to demonstrate full-stack web development with Flask and MySQL.

---

**Last Updated**: March 11, 2025
**Version**: 1.0.0

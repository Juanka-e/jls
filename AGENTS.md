# CRM (Customer Relationship Management) Application

## Project Overview
Build a full-stack CRM application with the following technology stack:
- **Frontend**: React.js with modern hooks and state management
- **Backend**: Node.js with Express.js
- **Database**: MySQL
- **Authentication**: JWT-based authentication
- **File Upload**: Multer for handling file uploads
interface must be Turkish.
## Core Features

### 1. Authentication & Authorization
- User registration and login
- JWT token-based authentication
- Role-based access control (Admin, Manager, Sales Rep)
- Password hashing with bcrypt
- Protected routes on both frontend and backend

### 2. Dashboard
- Overview statistics (total customers, deals, revenue)
- Recent activities timeline
- Sales pipeline visualization
- Performance metrics charts
- Quick action buttons

### 3. Customer Management
- CRUD operations for customers
- Customer profile with detailed information
- Contact history tracking
- Customer segmentation and tagging
- Search and filter functionality
- Export customer data (CSV/Excel)
- Customer notes and attachments

### 4. Contact Management
- Multiple contacts per customer
- Contact details (name, email, phone, position)
- Communication history
- Contact preferences

### 5. Deals/Opportunities
- Deal pipeline management
- Deal stages (Lead, Qualified, Proposal, Negotiation, Closed Won, Closed Lost)
- Drag-and-drop deal cards between stages
- Deal value tracking
- Expected close date
- Deal probability
- Associated customer and contacts
- Deal activity log

### 6. Tasks & Activities
- Create and assign tasks
- Task categories (Call, Email, Meeting, Follow-up)
- Due dates and reminders
- Task priority levels
- Calendar view
- Activity timeline per customer

### 7. Reporting & Analytics
- Sales reports
- Customer acquisition reports
- Revenue analytics
- Deal conversion funnel
- User performance metrics
- Custom date range filters
- Export reports as PDF

### 8. User Management (Admin only)
- Create/edit/delete users
- Assign roles and permissions
- User activity tracking
- Team management

### 9. Settings
- Company profile settings
- Email integration settings
- Notification preferences
- Custom fields configuration
- Pipeline customization

## Technical Requirements

### Frontend (React)

#### Project Structure
src/
├── components/
│ ├── common/
│ │ ├── Button.jsx
│ │ ├── Input.jsx
│ │ ├── Modal.jsx
│ │ ├── Table.jsx
│ │ ├── Sidebar.jsx
│ │ ├── Navbar.jsx
│ │ └── Loader.jsx
│ ├── auth/
│ │ ├── Login.jsx
│ │ ├── Register.jsx
│ │ └── ProtectedRoute.jsx
│ ├── dashboard/
│ │ ├── Dashboard.jsx
│ │ ├── StatsCard.jsx
│ │ └── RecentActivities.jsx
│ ├── customers/
│ │ ├── CustomerList.jsx
│ │ ├── CustomerForm.jsx
│ │ ├── CustomerDetail.jsx
│ │ └── CustomerCard.jsx
│ ├── deals/
│ │ ├── DealPipeline.jsx
│ │ ├── DealCard.jsx
│ │ ├── DealForm.jsx
│ │ └── DealDetail.jsx
│ ├── tasks/
│ │ ├── TaskList.jsx
│ │ ├── TaskForm.jsx
│ │ └── TaskCalendar.jsx
│ └── reports/
│ ├── SalesReport.jsx
│ └── AnalyticsChart.jsx
├── contexts/
│ ├── AuthContext.jsx
│ └── ThemeContext.jsx
├── hooks/
│ ├── useAuth.js
│ ├── useFetch.js
│ └── useDebounce.js
├── services/
│ ├── api.js
│ ├── authService.js
│ ├── customerService.js
│ ├── dealService.js
│ └── taskService.js
├── utils/
│ ├── helpers.js
│ ├── validators.js
│ └── constants.js
├── App.jsx
└── index.js

text


#### Key Libraries
- React Router DOM for routing
- Axios for API calls
- React Query or SWR for data fetching
- Formik + Yup for form handling and validation
- React Beautiful DnD for drag-and-drop
- Chart.js or Recharts for data visualization
- Date-fns or Moment.js for date handling
- React Toastify for notifications
- Tailwind CSS or Material-UI for styling

#### State Management
- Context API for global state (auth, theme)
- React Query for server state
- Local state with useState and useReducer

### Backend (Node.js + Express)

#### Project Structure
server/
├── config/
│ ├── database.js
│ └── jwt.js
├── controllers/
│ ├── authController.js
│ ├── customerController.js
│ ├── dealController.js
│ ├── taskController.js
│ ├── userController.js
│ └── reportController.js
├── middleware/
│ ├── auth.js
│ ├── errorHandler.js
│ ├── validation.js
│ └── upload.js
├── models/
│ ├── User.js
│ ├── Customer.js
│ ├── Contact.js
│ ├── Deal.js
│ └── Task.js
├── routes/
│ ├── authRoutes.js
│ ├── customerRoutes.js
│ ├── dealRoutes.js
│ ├── taskRoutes.js
│ ├── userRoutes.js
│ └── reportRoutes.js
├── utils/
│ ├── emailService.js
│ └── helpers.js
├── validators/
│ ├── customerValidator.js
│ ├── dealValidator.js
│ └── taskValidator.js
├── app.js
└── server.js

text


#### Key Packages
- express
- mysql2
- jsonwebtoken
- bcryptjs
- dotenv
- cors
- helmet
- express-validator
- multer
- nodemailer
- morgan (logging)
- compression

#### API Endpoints

**Authentication**
- POST /api/auth/register
- POST /api/auth/login
- POST /api/auth/refresh-token
- GET /api/auth/me

**Customers**
- GET /api/customers
- GET /api/customers/:id
- POST /api/customers
- PUT /api/customers/:id
- DELETE /api/customers/:id
- GET /api/customers/:id/contacts
- POST /api/customers/:id/notes

**Deals**
- GET /api/deals
- GET /api/deals/:id
- POST /api/deals
- PUT /api/deals/:id
- PATCH /api/deals/:id/stage
- DELETE /api/deals/:id
- GET /api/deals/pipeline

**Tasks**
- GET /api/tasks
- GET /api/tasks/:id
- POST /api/tasks
- PUT /api/tasks/:id
- DELETE /api/tasks/:id
- PATCH /api/tasks/:id/complete

**Users**
- GET /api/users
- GET /api/users/:id
- POST /api/users
- PUT /api/users/:id
- DELETE /api/users/:id

**Reports**
- GET /api/reports/sales
- GET /api/reports/customers
- GET /api/reports/deals
- GET /api/reports/performance

### Database Design

See `schema.sql` for complete database schema.

## Security Requirements
- Input validation and sanitization
- SQL injection prevention (parameterized queries)
- XSS protection
- CSRF protection
- Rate limiting on API endpoints
- Helmet.js for security headers
- Environment variables for sensitive data
- Password strength requirements
- Secure session management

## Performance Optimization
- Database indexing on frequently queried columns
- Pagination for large data sets
- Lazy loading for React components
- API response caching where appropriate
- Image optimization for uploads
- Compression middleware
- Database connection pooling

## Error Handling
- Centralized error handling middleware
- Proper HTTP status codes
- User-friendly error messages on frontend
- Error logging for debugging
- Validation error responses

## Responsive Design
- Mobile-first approach
- Responsive tables with horizontal scroll
- Hamburger menu for mobile navigation
- Touch-friendly interface elements
- Responsive charts and graphs

## Additional Features (Optional)
- Email notifications
- Real-time updates with WebSocket
- Dark mode toggle
- Multi-language support (i18n)
- Advanced search with filters
- Bulk operations
- Import customers from CSV
- Integration with third-party services (Gmail, Calendar)
- Activity logs and audit trail
- Custom dashboard widgets

## Development Guidelines

### Code Quality
- ESLint and Prettier configuration
- Consistent naming conventions
- Modular and reusable components
- Comments for complex logic
- PropTypes or TypeScript for type checking

### Git Workflow
- Feature branch workflow
- Meaningful commit messages
- Pull request reviews
- Semantic versioning

### Testing (Optional but Recommended)
- Unit tests with Jest
- Integration tests for API endpoints
- Component tests with React Testing Library
- E2E tests with Cypress

## Environment Variables

### Frontend (.env)
REACT_APP_API_URL=http://localhost:5000/api
REACT_APP_JWT_SECRET=your_jwt_secret

text


### Backend (.env)
PORT=5000
DB_HOST=localhost
DB_USER=root
DB_PASSWORD=your_password
DB_NAME=crm_db
JWT_SECRET=your_jwt_secret_key
JWT_EXPIRE=7d
NODE_ENV=development

text


## Deployment Considerations
- Frontend: Vercel, Netlify, or AWS S3 + CloudFront
- Backend: Heroku, AWS EC2, or DigitalOcean
- Database: AWS RDS, PlanetScale, or managed MySQL
- Environment-specific configurations
- SSL certificates for HTTPS
- Domain configuration
- CI/CD pipeline setup

## Getting Started Instructions

### Backend Setup
```bash
cd server
npm install
cp .env.example .env
# Configure your .env file
mysql -u root -p < schema.sql
npm run dev
Frontend Setup
Bash

cd client
npm install
cp .env.example .env
# Configure your .env file
npm start
Success Criteria
Users can register and login securely
CRUD operations work for all entities
Dashboard displays accurate statistics
Deal pipeline is interactive and functional
Tasks can be created and managed
Reports generate accurate data
Application is responsive on all devices
No security vulnerabilities
Clean and intuitive UI/UX
Fast page load times (<3 seconds)
Deliverables
Complete React frontend application
Complete Node.js/Express backend API
MySQL database schema and seed data
README.md with setup instructions
API documentation
Environment variable templates
Basic test coverage (if applicable)
text


---

# schema.sql

```sql
-- CRM Database Schema
-- MySQL Database

-- Drop existing database if exists (use with caution in production)
DROP DATABASE IF EXISTS crm_db;
CREATE DATABASE crm_db;
USE crm_db;

-- Users Table
CREATE TABLE users (
    id INT PRIMARY KEY AUTO_INCREMENT,
    first_name VARCHAR(50) NOT NULL,
    last_name VARCHAR(50) NOT NULL,
    email VARCHAR(100) UNIQUE NOT NULL,
    password VARCHAR(255) NOT NULL,
    role ENUM('admin', 'manager', 'sales_rep') DEFAULT 'sales_rep',
    phone VARCHAR(20),
    avatar VARCHAR(255),
    is_active BOOLEAN DEFAULT TRUE,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
    INDEX idx_email (email),
    INDEX idx_role (role)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;

-- Customers Table
CREATE TABLE customers (
    id INT PRIMARY KEY AUTO_INCREMENT,
    company_name VARCHAR(100) NOT NULL,
    industry VARCHAR(50),
    website VARCHAR(100),
    email VARCHAR(100),
    phone VARCHAR(20),
    address VARCHAR(255),
    city VARCHAR(50),
    state VARCHAR(50),
    country VARCHAR(50),
    postal_code VARCHAR(20),
    customer_type ENUM('lead', 'prospect', 'customer', 'partner') DEFAULT 'lead',
    customer_status ENUM('active', 'inactive', 'churned') DEFAULT 'active',
    revenue_potential DECIMAL(15, 2),
    assigned_to INT,
    created_by INT,
    notes TEXT,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
    FOREIGN KEY (assigned_to) REFERENCES users(id) ON DELETE SET NULL,
    FOREIGN KEY (created_by) REFERENCES users(id) ON DELETE SET NULL,
    INDEX idx_company (company_name),
    INDEX idx_type (customer_type),
    INDEX idx_assigned (assigned_to),
    FULLTEXT idx_search (company_name, email, notes)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;

-- Contacts Table
CREATE TABLE contacts (
    id INT PRIMARY KEY AUTO_INCREMENT,
    customer_id INT NOT NULL,
    first_name VARCHAR(50) NOT NULL,
    last_name VARCHAR(50) NOT NULL,
    email VARCHAR(100),
    phone VARCHAR(20),
    mobile VARCHAR(20),
    position VARCHAR(100),
    department VARCHAR(50),
    is_primary BOOLEAN DEFAULT FALSE,
    notes TEXT,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
    FOREIGN KEY (customer_id) REFERENCES customers(id) ON DELETE CASCADE,
    INDEX idx_customer (customer_id),
    INDEX idx_email (email)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;

-- Deals/Opportunities Table
CREATE TABLE deals (
    id INT PRIMARY KEY AUTO_INCREMENT,
    title VARCHAR(200) NOT NULL,
    customer_id INT NOT NULL,
    contact_id INT,
    value DECIMAL(15, 2) NOT NULL,
    currency VARCHAR(3) DEFAULT 'USD',
    stage ENUM('lead', 'qualified', 'proposal', 'negotiation', 'closed_won', 'closed_lost') DEFAULT 'lead',
    probability INT DEFAULT 0,
    expected_close_date DATE,
    actual_close_date DATE,
    description TEXT,
    assigned_to INT,
    created_by INT,
    lost_reason TEXT,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
    FOREIGN KEY (customer_id) REFERENCES customers(id) ON DELETE CASCADE,
    FOREIGN KEY (contact_id) REFERENCES contacts(id) ON DELETE SET NULL,
    FOREIGN KEY (assigned_to) REFERENCES users(id) ON DELETE SET NULL,
    FOREIGN KEY (created_by) REFERENCES users(id) ON DELETE SET NULL,
    INDEX idx_customer (customer_id),
    INDEX idx_stage (stage),
    INDEX idx_assigned (assigned_to),
    INDEX idx_close_date (expected_close_date)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;

-- Tasks Table
CREATE TABLE tasks (
    id INT PRIMARY KEY AUTO_INCREMENT,
    title VARCHAR(200) NOT NULL,
    description TEXT,
    task_type ENUM('call', 'email', 'meeting', 'follow_up', 'other') DEFAULT 'other',
    priority ENUM('low', 'medium', 'high', 'urgent') DEFAULT 'medium',
    status ENUM('pending', 'in_progress', 'completed', 'cancelled') DEFAULT 'pending',
    due_date DATETIME,
    completed_date DATETIME,
    customer_id INT,
    deal_id INT,
    assigned_to INT,
    created_by INT,
    reminder_sent BOOLEAN DEFAULT FALSE,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
    FOREIGN KEY (customer_id) REFERENCES customers(id) ON DELETE CASCADE,
    FOREIGN KEY (deal_id) REFERENCES deals(id) ON DELETE CASCADE,
    FOREIGN KEY (assigned_to) REFERENCES users(id) ON DELETE SET NULL,
    FOREIGN KEY (created_by) REFERENCES users(id) ON DELETE SET NULL,
    INDEX idx_status (status),
    INDEX idx_due_date (due_date),
    INDEX idx_assigned (assigned_to)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;

-- Activities/Notes Table
CREATE TABLE activities (
    id INT PRIMARY KEY AUTO_INCREMENT,
    activity_type ENUM('note', 'call', 'email', 'meeting', 'task_completed', 'stage_change') NOT NULL,
    subject VARCHAR(200),
    content TEXT,
    customer_id INT,
    deal_id INT,
    task_id INT,
    created_by INT,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (customer_id) REFERENCES customers(id) ON DELETE CASCADE,
    FOREIGN KEY (deal_id) REFERENCES deals(id) ON DELETE CASCADE,
    FOREIGN KEY (task_id) REFERENCES tasks(id) ON DELETE CASCADE,
    FOREIGN KEY (created_by) REFERENCES users(id) ON DELETE SET NULL,
    INDEX idx_customer (customer_id),
    INDEX idx_deal (deal_id),
    INDEX idx_created_at (created_at)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;

-- Customer Tags Table
CREATE TABLE tags (
    id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(50) UNIQUE NOT NULL,
    color VARCHAR(7) DEFAULT '#3B82F6',
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;

-- Customer-Tag Relationship Table
CREATE TABLE customer_tags (
    customer_id INT,
    tag_id INT,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    PRIMARY KEY (customer_id, tag_id),
    FOREIGN KEY (customer_id) REFERENCES customers(id) ON DELETE CASCADE,
    FOREIGN KEY (tag_id) REFERENCES tags(id) ON DELETE CASCADE
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;

-- File Attachments Table
CREATE TABLE attachments (
    id INT PRIMARY KEY AUTO_INCREMENT,
    filename VARCHAR(255) NOT NULL,
    original_name VARCHAR(255) NOT NULL,
    file_path VARCHAR(500) NOT NULL,
    file_size INT,
    mime_type VARCHAR(100),
    customer_id INT,
    deal_id INT,
    uploaded_by INT,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (customer_id) REFERENCES customers(id) ON DELETE CASCADE,
    FOREIGN KEY (deal_id) REFERENCES deals(id) ON DELETE CASCADE,
    FOREIGN KEY (uploaded_by) REFERENCES users(id) ON DELETE SET NULL,
    INDEX idx_customer (customer_id),
    INDEX idx_deal (deal_id)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;

-- Email Templates Table
CREATE TABLE email_templates (
    id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(100) NOT NULL,
    subject VARCHAR(200) NOT NULL,
    body TEXT NOT NULL,
    category VARCHAR(50),
    is_active BOOLEAN DEFAULT TRUE,
    created_by INT,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
    FOREIGN KEY (created_by) REFERENCES users(id) ON DELETE SET NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;

-- Settings Table
CREATE TABLE settings (
    id INT PRIMARY KEY AUTO_INCREMENT,
    setting_key VARCHAR(100) UNIQUE NOT NULL,
    setting_value TEXT,
    setting_type VARCHAR(50),
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;

-- Notifications Table
CREATE TABLE notifications (
    id INT PRIMARY KEY AUTO_INCREMENT,
    user_id INT NOT NULL,
    title VARCHAR(200) NOT NULL,
    message TEXT,
    type VARCHAR(50),
    is_read BOOLEAN DEFAULT FALSE,
    link VARCHAR(255),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (user_id) REFERENCES users(id) ON DELETE CASCADE,
    INDEX idx_user (user_id),
    INDEX idx_read (is_read)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;

-- ============================================
-- SEED DATA
-- ============================================

-- Insert default admin user (password: Admin@123)
INSERT INTO users (first_name, last_name, email, password, role) VALUES
('Admin', 'User', 'admin@crm.com', '$2a$10$XQgzz0cYVSZ6F5j6K6JQSO6J.QqH8DZ9YdvEGLvBF9bJ2C2QJZT6e', 'admin'),
('John', 'Doe', 'john@crm.com', '$2a$10$XQgzz0cYVSZ6F5j6K6JQSO6J.QqH8DZ9YdvEGLvBF9bJ2C2QJZT6e', 'manager'),
('Jane', 'Smith', 'jane@crm.com', '$2a$10$XQgzz0cYVSZ6F5j6K6JQSO6J.QqH8DZ9YdvEGLvBF9bJ2C2QJZT6e', 'sales_rep');

-- Insert sample customers
INSERT INTO customers (company_name, industry, email, phone, city, country, customer_type, assigned_to, created_by) VALUES
('Acme Corporation', 'Technology', 'contact@acme.com', '+1-555-0100', 'San Francisco', 'USA', 'customer', 2, 1),
('Global Solutions Ltd', 'Consulting', 'info@globalsolutions.com', '+1-555-0101', 'New York', 'USA', 'prospect', 3, 1),
('Tech Innovations Inc', 'Software', 'hello@techinnovations.com', '+1-555-0102', 'Austin', 'USA', 'lead', 3, 2);

-- Insert sample contacts
INSERT INTO contacts (customer_id, first_name, last_name, email, phone, position, is_primary) VALUES
(1, 'Robert', 'Johnson', 'robert@acme.com', '+1-555-0200', 'CEO', TRUE),
(1, 'Sarah', 'Williams', 'sarah@acme.com', '+1-555-0201', 'CTO', FALSE),
(2, 'Michael', 'Brown', 'michael@globalsolutions.com', '+1-555-0202', 'Director', TRUE),
(3, 'Emily', 'Davis', 'emily@techinnovations.com', '+1-555-0203', 'VP Sales', TRUE);

-- Insert sample deals
INSERT INTO deals (title, customer_id, contact_id, value, stage, probability, expected_close_date, assigned_to, created_by) VALUES
('Enterprise Software License', 1, 1, 50000.00, 'negotiation', 75, '2024-02-15', 2, 1),
('Consulting Services Contract', 2, 3, 75000.00, 'proposal', 50, '2024-03-01', 3, 1),
('Annual Support Package', 1, 2, 25000.00, 'qualified', 60, '2024-02-28', 2, 2),
('New Implementation', 3, 4, 100000.00, 'lead', 25, '2024-04-15', 3, 2);

-- Insert sample tasks
INSERT INTO tasks (title, description, task_type, priority, status, due_date, customer_id, deal_id, assigned_to, created_by) VALUES
('Follow up call with Acme', 'Discuss contract terms', 'call', 'high', 'pending', '2024-01-25 10:00:00', 1, 1, 2, 1),
('Send proposal to Global Solutions', 'Prepare and send detailed proposal', 'email', 'urgent', 'in_progress', '2024-01-23 15:00:00', 2, 2, 3, 1),
('Schedule demo meeting', 'Product demonstration', 'meeting', 'medium', 'pending', '2024-01-26 14:00:00', 3, 4, 3, 2);

-- Insert sample tags
INSERT INTO tags (name, color) VALUES
('VIP', '#EF4444'),
('Hot Lead', '#F59E0B'),
('Partner', '#10B981'),
('Enterprise', '#3B82F6'),
('Small Business', '#6366F1');

-- Insert sample customer tags
INSERT INTO customer_tags (customer_id, tag_id) VALUES
(1, 1),
(1, 4),
(2, 2),
(3, 2);

-- Insert sample activities
INSERT INTO activities (activity_type, subject, content, customer_id, created_by) VALUES
('note', 'Initial Contact', 'Had a great first call. Customer is interested in our enterprise package.', 1, 2),
('call', 'Follow-up Call', 'Discussed pricing and implementation timeline.', 2, 3),
('email', 'Proposal Sent', 'Sent detailed proposal document via email.', 2, 3);

-- Insert sample settings
INSERT INTO settings (setting_key, setting_value, setting_type) VALUES
('company_name', 'My CRM Company', 'text'),
('currency', 'USD', 'text'),
('timezone', 'America/New_York', 'text'),
('date_format', 'YYYY-MM-DD', 'text'),
('items_per_page', '25', 'number');

-- ============================================
-- USEFUL VIEWS
-- ============================================

-- View for deal pipeline summary
CREATE VIEW deal_pipeline_summary AS
SELECT 
    stage,
    COUNT(*) as deal_count,
    SUM(value) as total_value,
    AVG(probability) as avg_probability
FROM deals
GROUP BY stage;

-- View for customer overview
CREATE VIEW customer_overview AS
SELECT 
    c.id,
    c.company_name,
    c.customer_type,
    c.customer_status,
    COUNT(DISTINCT co.id) as contact_count,
    COUNT(DISTINCT d.id) as deal_count,
    SUM(d.value) as total_deal_value,
    CONCAT(u.first_name, ' ', u.last_name) as assigned_to_name
FROM customers c
LEFT JOIN contacts co ON c.id = co.customer_id
LEFT JOIN deals d ON c.id = d.customer_id
LEFT JOIN users u ON c.assigned_to = u.id
GROUP BY c.id;

-- View for user performance
CREATE VIEW user_performance AS
SELECT 
    u.id,
    CONCAT(u.first_name, ' ', u.last_name) as user_name,
    COUNT(DISTINCT c.id) as customers_managed,
    COUNT(DISTINCT d.id) as deals_managed,
    SUM(CASE WHEN d.stage = 'closed_won' THEN d.value ELSE 0 END) as revenue_generated,
    COUNT(CASE WHEN t.status = 'completed' THEN 1 END) as tasks_completed
FROM users u
LEFT JOIN customers c ON u.id = c.assigned_to
LEFT JOIN deals d ON u.id = d.assigned_to
LEFT JOIN tasks t ON u.id = t.assigned_to
GROUP BY u.id;

-- ============================================
-- STORED PROCEDURES
-- ============================================

DELIMITER //

-- Procedure to update deal stage
CREATE PROCEDURE update_deal_stage(
    IN deal_id INT,
    IN new_stage VARCHAR(50),
    IN user_id INT
)
BEGIN
    DECLARE old_stage VARCHAR(50);
    
    SELECT stage INTO old_stage FROM deals WHERE id = deal_id;
    
    UPDATE deals SET stage = new_stage WHERE id = deal_id;
    
    INSERT INTO activities (activity_type, subject, content, deal_id, created_by)
    VALUES ('stage_change', 'Deal Stage Updated', 
            CONCAT('Stage changed from ', old_stage, ' to ', new_stage), 
            deal_id, user_id);
END //

-- Procedure to complete task
CREATE PROCEDURE complete_task(
    IN task_id INT,
    IN user_id INT
)
BEGIN
    UPDATE tasks 
    SET status = 'completed', completed_date = NOW() 
    WHERE id = task_id;
    
    INSERT INTO activities (activity_type, subject, content, task_id, created_by)
    SELECT 'task_completed', title, description, task_id, user_id
    FROM tasks WHERE id = task_id;
END //

DELIMITER ;

-- ============================================
-- TRIGGERS
-- ============================================

DELIMITER //

-- Trigger to create activity when new customer is added
CREATE TRIGGER after_customer_insert
AFTER INSERT ON customers
FOR EACH ROW
BEGIN
    INSERT INTO activities (activity_type, subject, content, customer_id, created_by)
    VALUES ('note', 'Customer Created', 
            CONCAT('New customer "', NEW.company_name, '" was added to the system.'),
            NEW.id, NEW.created_by);
END //

-- Trigger to update deal close date when stage is closed
CREATE TRIGGER before_deal_update
BEFORE UPDATE ON deals
FOR EACH ROW
BEGIN
    IF NEW.stage IN ('closed_won', 'closed_lost') AND OLD.stage NOT IN ('closed_won', 'closed_lost') THEN
        SET NEW.actual_close_date = NOW();
    END IF;
END //

DELIMITER ;

-- ============================================
-- INDEXES FOR PERFORMANCE
-- ============================================

-- Additional composite indexes for common queries
CREATE INDEX idx_customer_assigned_type ON customers(assigned_to, customer_type);
CREATE INDEX idx_deal_assigned_stage ON deals(assigned_to, stage);
CREATE INDEX idx_task_assigned_status ON tasks(assigned_to, status);
CREATE INDEX idx_activities_customer_date ON activities(customer_id, created_at);

-- ============================================
-- GRANTS (Optional - for specific user)
-- ============================================

-- CREATE USER 'crm_user'@'localhost' IDENTIFIED BY 'secure_password';
-- GRANT ALL PRIVILEGES ON crm_db.* TO 'crm_user'@'localhost';
-- FLUSH PRIVILEGES;
Save these two files:

crm-prompt.md - The main prompt
schema.sql - The database schema
This will give you a complete, production-ready CRM application structure! 🚀
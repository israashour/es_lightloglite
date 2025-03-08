# Installing and Using es_lightloglite in Laravel  

This guide walks you through installing, configuring, and using the **es_lightloglite** package to efficiently track and manage exceptions in your Laravel project.  

---

##  Prerequisites  

Before installing **es_lightloglite**, ensure you have the following:  
- **Laravel 10** or later  
- **PHP 8.0** or later  
- **Composer** installed  

---

## 1. Installation  

To install **es_lightloglite**, follow these steps:  

### **1. Install via Composer**  
Run the following command in your terminal:  
```bash
composer require israashour/es_lightloglite
````

### **2. Publish Configuration File**

```bash
php artisan vendor:publish --tag=es_lightloglite-config
```

### **3. Migrate Database (If Required)**

```bash
php artisan migrate
```

### **4. Set Up Environment Variables**

Add these lines to your `.env` file:

```env
ES_LIGHTLOGLITE_ENABLED=true
ES_LIGHTLOGLITE_LEVEL=error
```

---

## 2. Usage Guide

### **1. Access the Dashboard**

Navigate to:

```
http://your-app-url/es_lightloglite
```

### **2. Viewing Logs**

- Filter logs by **date**, **severity level**, or **error type**.
- Use the search bar for quick lookup.

### **3. Exception Statistics & Trends**

- View graphs and analytics on errors.
- Track recurring issues over time.

### **4. Documentation**

For more details, visit the **[GitHub Repository](https://github.com/israashour/package-test.git)**.

---

## 3. Example Code Usage

To manually log an error:

```php
use EsLightLogLite\Facades\EsLightLogLite;

EsLightLogLite::logError('This is a test error message');
```

Or inside a controller:

```php
namespace App\Http\Controllers;

use EsLightLogLite\Facades\EsLightLogLite;
use Exception;
use Illuminate\Http\Request;

class ExampleController extends Controller
{
    public function store(Request $request)
    {
        try {
            // Some processing logic
        } catch (Exception $e) {
            EsLightLogLite::logError($e->getMessage());
            return response()->json(['error' => 'An error occurred'], 500);
        }
    }
}
```

---

##  4. Uninstallation (If Needed)

### **1. Remove the Package**

```bash
composer remove israashour/es_lightloglite
```

### **2. Rollback Database Changes (if applicable)**

```bash
php artisan migrate:rollback
```

**Note:** You may also delete the configuration file at:

```
config/es_lightloglite.php
```

---

This guide ensures that you can **install, configure, and use** **es_lightloglite** effectively in your Laravel project. 

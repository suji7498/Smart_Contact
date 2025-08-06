# SmartContact JSON Storage System

## Overview
The SmartContact plugin now uses JSON file storage instead of database storage for form submissions. This eliminates database load and stores all submissions in a structured JSON file.

## Storage Location
- **File Path:** `wp-content/plugins/smartcontact-webhook-form/data/submissions.json`
- **Directory Protection:** `.htaccess` file prevents direct web access to the data directory

## JSON File Structure
```json
{
    "submissions": [
        {
            "id": 1,
            "name": "John Doe",
            "email": "john@example.com",
            "subject": "Contact Request",
            "message": "Hello, I have a question...",
            "custom_fields": {
                "Phone": "123-456-7890",
                "Company": "Example Corp"
            },
            "page_url": "https://example.com/contact",
            "page_title": "Contact Us",
            "referrer_url": "https://google.com",
            "webhook_response": {
                "status_code": 200,
                "body": "Success"
            },
            "submission_time": "2024-01-15 10:30:00",
            "ip_address": "192.168.1.1",
            "user_agent": "Mozilla/5.0..."
        }
    ],
    "last_id": 1,
    "total_submissions": 1,
    "created_at": "2024-01-15 10:00:00",
    "updated_at": "2024-01-15 10:30:00"
}
```

## Features

### ✅ **Zero Database Load**
- No database queries for form submissions
- No database table creation or maintenance
- Reduced server resource usage

### ✅ **File-Based Storage**
- All data stored in human-readable JSON format
- Easy backup and restore
- Portable data structure

### ✅ **Security**
- Data directory protected with `.htaccess`
- File permissions managed automatically
- Atomic file writes with `LOCK_EX`

### ✅ **Performance**
- Fast read/write operations
- Efficient pagination and sorting
- Optimized for small to medium submission volumes

### ✅ **Data Integrity**
- Automatic file corruption detection and recovery
- Backup-friendly structure
- JSON validation and error handling

## File Management

### Automatic Operations
- **Directory Creation:** Automatically creates `data/` directory on plugin activation
- **File Initialization:** Creates initial JSON structure if file doesn't exist
- **Corruption Recovery:** Automatically reinitializes corrupted files
- **Security:** Creates `.htaccess` to prevent direct web access

### Manual Operations
- **Backup:** Simply copy the `submissions.json` file
- **Restore:** Replace the file and refresh the admin page
- **Migration:** Export from old database and import to new JSON structure

## Performance Considerations

### ✅ **Advantages**
- No database connection overhead
- Faster for small datasets
- Reduced server memory usage
- No SQL query optimization needed

### ⚠️ **Limitations**
- Not suitable for very large datasets (10,000+ submissions)
- File I/O operations for each submission
- No concurrent write protection beyond file locking

## Migration from Database

If you're upgrading from the database version:

1. **Export existing data** from the database
2. **Deactivate the old plugin**
3. **Activate the new JSON-based plugin**
4. **Import data** using the admin interface (if available)

## Backup Recommendations

### Regular Backups
- Backup the entire `data/` directory
- Include the `.htaccess` file
- Consider automated backup scripts

### File Permissions
- Ensure the `data/` directory is writable by the web server
- Recommended: `755` for directory, `644` for JSON file

## Troubleshooting

### Common Issues
1. **Permission Errors:** Check directory and file permissions
2. **Corrupted File:** Plugin will automatically recreate the file
3. **Large File Size:** Consider archiving old submissions

### File Location
The JSON file is located at:
```
/wp-content/plugins/smartcontact-webhook-form/data/submissions.json
```

### Logging
Check WordPress error logs for any JSON storage related errors:
```
SmartContact: Failed to save submissions to JSON file
```

## Future Enhancements
- Data compression for large files
- Automatic archiving of old submissions
- Cloud storage integration
- Data encryption options 
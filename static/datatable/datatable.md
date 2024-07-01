Here are the Django models corresponding to the provided SQL tables, arranged in tabular form:

### 1. SIGUP
| Field     | Data Type | Length | Description               |
|-----------|------------|--------|---------------------------|
| Login_id  | INT        | 11     | Unique id for users in each login (Primary key) |
| Username  | VARCHAR    | 45     | Users name                |
| U_id      | INT        | 11     | Unique id for users       |
| Email     | VARCHAR    | 25     | Users email               |
| Phone     | INT        | 12     | Users phone               |

```python
from django.db import models

class Signup(models.Model):
    login_id = models.AutoField(primary_key=True)
    username = models.CharField(max_length=45)
    u_id = models.IntegerField()
    email = models.EmailField(max_length=25)
    phone = models.BigIntegerField()
```

### 2. USER REGISTRATION
| Field              | Data Type | Length | Description               |
|--------------------|-----------|--------|---------------------------|
| User_id            | INT       | 11     | Unique id for users (Primary key) |
| DOB                | DATE      |        | Users date of birth       |
| Hobbies            | VARCHAR   | 45     | Users hobbies             |
| Interest           | VARCHAR   | 45     | Users interest            |
| Smoking            | VARCHAR   | 45     | If the user smokes        |
| Drinking_habit     | VARCHAR   | 45     | If the user has a drinking habit |
| Qualification      | VARCHAR   | 45     | Users qualifications      |
| Profile_pic        | BLOB      |        | Users profile pic         |
| Multiple_image     | BLOB      |        | Users multiple images     |
| Short_reals        | VARCHAR   | 45     | Users short reals (up to 30 sec) |
| Username           | VARCHAR   | 45     | Users name                |
| Password           | PASSWORD  | 10     | Password setting for security |
| Conform_password   | PASSWORD  | 10     | Confirming the password   |
| Verified           | VARCHAR   | 45     | To confirm the OTP is verified |
| OTP                | INT       | 11     | System-generated OTP for verification |
| Exp                | DATETIME  |        | OTP validity duration     |

```python
class UserRegistration(models.Model):
    user_id = models.AutoField(primary_key=True)
    dob = models.DateField()
    hobbies = models.CharField(max_length=45)
    interest = models.CharField(max_length=45)
    smoking = models.CharField(max_length=45)
    drinking_habit = models.CharField(max_length=45)
    qualification = models.CharField(max_length=45)
    profile_pic = models.BinaryField()
    multiple_image = models.BinaryField()
    short_reals = models.CharField(max_length=45)
    username = models.CharField(max_length=45)
    password = models.CharField(max_length=10)
    conform_password = models.CharField(max_length=10)
    verified = models.CharField(max_length=45)
    otp = models.IntegerField()
    exp = models.DateTimeField()
```

### 3. NOTIFICATIONS
| Field           | Data Type | Length | Description               |
|-----------------|-----------|--------|---------------------------|
| Notification_id | INT       | 11     | Notification id (Primary key) |
| User_id         | INT       | 11     | Unique id of users (Foreign key) |
| Notification    | VARCHAR   | 200    | Notification sent by users |
| Date            | DATE      |        | Date the notification was sent |
| Time            | TIME      |        | Time the notification was sent |

```python
class Notifications(models.Model):
    notification_id = models.AutoField(primary_key=True)
    user_id = models.ForeignKey(Signup, on_delete=models.CASCADE)
    notification = models.CharField(max_length=200)
    date = models.DateField()
    time = models.TimeField()
```

### 4. CHAT
| Field       | Data Type | Length | Description               |
|-------------|-----------|--------|---------------------------|
| Chat_id     | INT       | 11     | Unique chat id for each user (Primary key) |
| User_id     | INT       | 11     | Users unique id (Foreign key) |
| Sender_id   | INT       | 11     | Id of users who sent the message |
| Receiver_id | INT       | 11     | Id of users who received the message |
| Message     | VARCHAR   | 200    | Content of the message     |
| Date        | DATE      |        | Date the chat occurred     |
| Time        | TIME      |        | Time the chat occurred     |

```python
class Chat(models.Model):
    chat_id = models.AutoField(primary_key=True)
    user_id = models.ForeignKey(Signup, on_delete=models.CASCADE, related_name='chats')
    sender_id = models.IntegerField()
    receiver_id = models.IntegerField()
    message = models.CharField(max_length=200)
    date = models.DateField()
    time = models.TimeField()
```

### 5. BANNER
| Field       | Data Type | Length | Description               |
|-------------|-----------|--------|---------------------------|
| Banner_id   | INT       | 11     | Unique Banner id (Primary key) |
| User_id     | INT       | 11     | Unique id who sent the banner (Foreign key) |
| Date        | DATE      |        | Date the banner is shown  |
| Time        | TIME      |        | Time the banner is shown  |
| Banner      | VARCHAR   | 200    | Content of the banner      |

```python
class Banner(models.Model):
    banner_id = models.AutoField(primary_key=True)
    user_id = models.ForeignKey(Signup, on_delete=models.CASCADE)
    date = models.DateField()
    time = models.TimeField()
    banner = models.CharField(max_length=200)
```

### 6. REPORT
| Field      | Data Type | Length | Description               |
|------------|-----------|--------|---------------------------|
| Report_id  | INT       | 11     | Unique reporting id (Primary key) |
| User_id    | INT       | 11     | Users unique id (Foreign key) |
| Time       | TIME      |        | Time the report was made  |
| Date       | DATE      |        | Date the report was made  |
| Report     | VARCHAR   | 200    | Content of the report      |

```python
class Report(models.Model):
    report_id = models.AutoField(primary_key=True)
    user_id = models.ForeignKey(Signup, on_delete=models.CASCADE)
    time = models.TimeField()
    date = models.DateField()
    report = models.CharField(max_length=200)
```

### 7. PAYMENT
| Field              | Data Type | Length | Description               |
|--------------------|-----------|--------|---------------------------|
| Payment_id         | INT       | 11     | Unique payment id (Primary key) |
| User_id            | INT       | 11     | Users unique id (Foreign key) |
| Card_Holder_Name   | VARCHAR   | 45     | Users card holder name     |
| Card_Number        | BIGINT    | 11     | Users card number          |
| CVV                | INT       | 3      | Users CVV number           |
| Amount             | VARCHAR   | 45     | Amount for payment         |

```python
class Payment(models.Model):
    payment_id = models.AutoField(primary_key=True)
    user_id = models.ForeignKey(Signup, on_delete=models.CASCADE)
    card_holder_name = models.CharField(max_length=45)
    card_number = models.BigIntegerField()
    cvv = models.IntegerField()
    amount = models.CharField(max_length=45)
```

### 8. CATEGORY
| Field       | Data Type | Length | Description               |
|-------------|-----------|--------|---------------------------|
| Category_id | INT       | 11     | Unique Category id (Primary key) |
| User_id     | INT       | 11     | Users unique id (Foreign key) |
| Designation | VARCHAR   | 45     | The designation of the user |
| Location    | VARCHAR   | 45     | The location of the user  |
| Education   | VARCHAR   | 45     | The education of the user  |

```python
class Category(models.Model):
    category_id = models.AutoField(primary_key=True)
    user_id = models.ForeignKey(Signup, on_delete=models.CASCADE)
    designation = models.CharField(max_length=45)
    location = models.CharField(max_length=45)
    education = models.CharField(max_length=45)
```

### 9. EMPLOYEE/EMPLOYER
| Field           | Data Type | Length | Description               |
|-----------------|-----------|--------|---------------------------|
| Category_id     | INT       | 11     | Unique Category id (Foreign key) |
| Category_name   | VARCHAR   | 11     | Category name             |
| User_id         | INT       | 11     | Users unique id (Foreign key) |
| Company_name    | VARCHAR   | 45     | Name of the company       |
| Designation     | VARCHAR   | 45     | Designation of the employee/employer |
| Location        | VARCHAR   | 45     | Location of the employee/employer |

```python
class EmployeeEmployer(models.Model):
    category = models.ForeignKey(Category, on_delete=models.CASCADE)
    category_name = models.CharField(max_length=11)
    user_id
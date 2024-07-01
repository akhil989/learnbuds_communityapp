Here's a tabulated view of the tables converted into Django MongoDB documents:

| Table Name       | Field Name         | Data Type          | Length | Description                                 |
|------------------|--------------------|--------------------|--------|---------------------------------------------|
| **SIGNUP**       | login_id           | IntegerField       | 11     | Primary key, Unique id for users in each login |
|                  | username           | CharField          | 45     | Users name                                  |
|                  | u_id               | IntegerField       | 11     | Unique id for users                         |
|                  | email              | EmailField         | 25     | Users email                                 |
|                  | phone              | CharField          | 12     | Users phone                                 |
| **USER REGISTRATION** | user_id           | IntegerField       | 11     | Primary key, Unique id for users            |
|                  | dob                | DateField          |        | Users date of birth                         |
|                  | hobbies            | CharField          | 45     | Users hobbies                               |
|                  | interest           | CharField          | 45     | Users interest                              |
|                  | smoking            | CharField          | 45     | If the user smokes or not                   |
|                  | drinking_habit     | CharField          | 45     | If the user has a drinking habit or not     |
|                  | qualification      | CharField          | 45     | Users qualifications                        |
|                  | profile_pic        | BinaryField        |        | Users profile picture                       |
|                  | multiple_image     | BinaryField        |        | Users multiple images                       |
|                  | short_reels        | CharField          | 45     | Users short reels (max 30 sec)              |
|                  | username           | CharField          | 45     | Users name                                  |
|                  | password           | CharField          | 10     | Password for security                       |
|                  | confirm_password   | CharField          | 10     | Confirming the password                     |
|                  | verified           | CharField          | 45     | To confirm if the OTP is verified           |
|                  | otp                | IntegerField       | 11     | System-generated OTP for verification       |
|                  | exp                | DateTimeField      |        | OTP validity duration                       |
| **NOTIFICATIONS**| notification_id    | IntegerField       | 11     | Primary key, Notification id                |
|                  | user_id            | IntegerField       | 11     | Unique id of users, Foreign key             |
|                  | notification       | CharField          | 200    | Notification sent by users                  |
|                  | date               | DateField          |        | Date the notification was sent              |
|                  | time               | TimeField          |        | Time the notification was sent              |
| **CHAT**         | chat_id            | IntegerField       | 11     | Primary key, Unique chat id for each user   |
|                  | user_id            | IntegerField       | 11     | Users unique id, Foreign key                |
|                  | sender_id          | IntegerField       | 11     | ID of the user who sent the message         |
|                  | receiver_id        | IntegerField       | 11     | ID of the user who received the message     |
|                  | message            | CharField          | 200    | Content of the message                      |
|                  | date               | DateField          |        | Date the chat occurred                      |
|                  | time               | TimeField          |        | Time the chat occurred                      |
| **BANNER**       | banner_id          | IntegerField       | 11     | Primary key, Unique banner id               |
|                  | user_id            | IntegerField       | 11     | Unique id of user who sent the banner, Foreign key |
|                  | date               | DateField          |        | Date the banner is shown                    |
|                  | time               | TimeField          |        | Time the banner is shown                    |
|                  | banner             | CharField          | 200    | Content of the banner                       |
| **REPORT**       | report_id          | IntegerField       | 11     | Primary key, Unique reporting id            |
|                  | user_id            | IntegerField       | 11     | Users unique id, Foreign key                |
|                  | time               | TimeField          |        | Time the report was made                    |
|                  | date               | DateField          |        | Date the report was made                    |
|                  | report             | CharField          | 200    | Content of the report                       |
| **PAYMENT**      | payment_id         | IntegerField       | 11     | Primary key, Unique payment id              |
|                  | user_id            | IntegerField       | 11     | Users unique id, Foreign key                |
|                  | card_holder_name   | CharField          | 45     | Users card holder name for payment          |
|                  | card_number        | BigIntegerField    | 11     | Users card number for payment               |
|                  | cvv                | IntegerField       | 3      | Users CVV number for payment                |
|                  | amount             | CharField          | 45     | Amount for payment                          |
| **CATEGORY**     | category_id        | IntegerField       | 11     | Primary key, Unique category id             |
|                  | user_id            | IntegerField       | 11     | Users unique id, Foreign key                |
|                  | designation        | CharField          | 45     | Designation of the user looking for a job   |
|                  | location           | CharField          | 45     | Location of the user looking for a job      |
|                  | education          | CharField          | 45     | Education of the user looking for a job     |
| **EMPLOYEE/EMPLOYER** | category_id    | IntegerField       | 11     | Unique category id, Foreign key             |
|                  | category_name      | CharField          | 11     | Category name                               |
|                  | user_id            | IntegerField       | 11     | Users unique id, Foreign key                |
|                  | company_name       | CharField          | 45     | Company name of the employee/employer       |
|                  | designation        | CharField          | 45     | Designation of the employee/employer        |
|                  | location           | CharField          | 45     | Location of the employee/employer           |
| **JOB SEEKER**   | category_id        | IntegerField       | 11     | Unique category id, Foreign key             |
|                  | category_name      | CharField          | 45     | Category name                               |
|                  | user_id            | IntegerField       | 11     | Users unique id, Foreign key                |
|                  | job_title          | CharField          | 45     | Job title the user is looking for           |
|                  | expertise_level    | CharField          | 45     | Expertise level of the user (beginner, intermediate, expert) |

This table includes the field names, their data types, lengths, and descriptions for each of the Django models.
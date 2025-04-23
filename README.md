# Ex02 Django ORM Web Application
# Date: 20/4/25
# AIM
To develop a Django application to store and retrieve data from a bank loan database using Object Relational Mapping(ORM).

# ENTITY RELATIONSHIP DIAGRAM
![ORM](https://github.com/user-attachments/assets/8e72c0df-381d-4645-8e01-15497943a9c9)

## DESIGN STEPS
## STEP 1:
Clone the problem from GitHub

## STEP 2:
Create a new app in Django project

## STEP 3:
Enter the code for admin.py and models.py

## STEP 4:
Execute Django admin and create details for 10 books

# PROGRAM
```
from django.db import models

class Loan(models.Model):
    loan_id = models.AutoField(primary_key=True)  
    customer_name = models.CharField(max_length=100)  
    loan_amount = models.DecimalField(max_digits=15, decimal_places=2)  
    loan_type = models.CharField(max_length=50)  
    interest_rate = models.DecimalField(max_digits=5, decimal_places=2)  
    loan_term = models.IntegerField()  #
    loan_status = models.CharField(max_length=20, choices=[('approved', 'Approved'), ('pending', 'Pending'), ('rejected', 'Rejected')])  
    def __str__(self):
        return f"Loan {self.loan_id} - {self.customer_name}"

    class Meta:
        db_table = 'bank_loan'

from django.contrib import admin
from .models import Loan

class LoanAdmin(admin.ModelAdmin):
    list_display = ('loan_id', 'customer_name', 'loan_amount', 'loan_type', 'interest_rate', 'loan_term', 'loan_status')
    search_fields = ('customer_name', 'loan_id', 'loan_type')  
    list_filter = ('loan_status', 'loan_type')  
    list_per_page = 10  
    fieldsets = (
        (None, {
            'fields': ('customer_name', 'loan_amount', 'loan_type', 'interest_rate', 'loan_term', 'loan_status')
        }),
    )
    ordering = ('loan_id',)  
admin.site.register(Loan, LoanAdmin)
```
# OUTPUT
![WhatsApp Image 2025-04-23 at 6 01 43 PM](https://github.com/user-attachments/assets/0000421d-1d0c-4167-9d79-6a01f3b8db0d)
![WhatsApp Image 2025-04-23 at 6 02 05 PM](https://github.com/user-attachments/assets/bbe73708-e199-41d9-8a6c-237816e8fcf4)
![WhatsApp Image 2025-04-23 at 6 02 30 PM](https://github.com/user-attachments/assets/72fc49f6-12f6-4220-b285-5a5e171c8d69)



# RESULT
Thus the program for creating a database using ORM hass been executed successfully

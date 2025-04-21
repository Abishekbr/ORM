# Ex02 Django ORM Web Application
# Date: 21/04/25
# AIM
To develop a Django application to store and retrieve data from a bank loan database using Object Relational Mapping(ORM).

# ENTITY RELATIONSHIP DIAGRAM
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
# OUTPUT
![Screenshot 2025-04-21 184147](https://github.com/user-attachments/assets/4e645c76-41f5-45ac-94d3-cf979df2ed65)
![Screenshot 2025-04-21 184219](https://github.com/user-attachments/assets/f228bae2-f5e3-4757-b777-500d1e71cd4d)


# RESULT
Thus the program for creating a database using ORM hass been executed successfully

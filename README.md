# CHALLENGE_07

For reference, this is how the Restauran code looked like:
```python
# Define the base class for menu items
class MenuItem:
    def __init__(self, name, price):
        self.name = name
        self.price = price

    def calculate_total_price(self, quantity):
        return self.price * quantity

# Define subclasses for different types of menu items

class FoodItem:
    def __init__(self, name, price, category):
        self.name = name
        self.price = price
        self.category = category

class Starters(FoodItem):
    def __init__(self, name, price):
        super().__init__(name, price, "Starters")

class Soupes(FoodItem):
    def __init__(self, name, price):
        super().__init__(name, price, "Soupes")

class MainCourse(FoodItem):
    def __init__(self, name, price):
        super().__init__(name, price, "Main Course")

class Drinks(FoodItem):
    def __init__(self, name, price):
        super().__init__(name, price, "Drinks")

class Dessert(FoodItem):
    def __init__(self, name, price):
        super().__init__(name, price, "Dessert")


# Define the Order class
class Order:
    def __init__(self):
        self.items = []

    def add_item(self, item, quantity):
        self.items.append((item, quantity))

    def calculate_total_price(self):
        total = 0
        for item, quantity in self.items:
            total += item.price * quantity
        return total
    
    def ask_for_discount(self):
        categories = ["programmer", "mentally_ill", "student", "senior_citizen", "veteran", "unemployed", "homeless", "refugee", "disabled"]
        print("Please enter your population category. if you are not in any of these categories, please press enter")
        print("Available categories are:")
        for category in categories:
            print(category)
        user_category = input()
        if user_category in categories:
            return 10
        else:
            print("Sorry, you are not eligible for a discount.")
            return 0


    def apply_discount(self):
        discount = self.ask_for_discount()
        total_bill = self.calculate_total_price()
        return total_bill - (total_bill * discount / 100)

# Create instances of menu items
menu_items = [
    Starters("Diazepam, ONLY_FOR_SALE_WITH_PRESCRIPTION", 1.99,),
    Starters("Xanax, ONLY_FOR_SALE_WITH_PRESCRIPTION", 0.99),
    Starters("Propanonol, ONLY_FOR_SALE_WITH_PRESCRIPTION", 0.99), 
    Soupes("Programmer's tears with Mexican tortilla", 5.99),
    Soupes("Spinach with tomato", 3.99),
    Soupes("Lentil with bacon", 4.99),
    MainCourse("Korean boy beef burger", 201.99),
    MainCourse("Chicken fetus crepe", 122.99),
    MainCourse("Vegan salad with tuna", 7.99),
    MainCourse("Turkey pizza", 100),
    MainCourse("Venezuelan Pasta", 0.99),
    MainCourse("Fish and Chips with cornflakes", 12.99),
    Drinks("Fanta", 1.99),
    Drinks("Taylor Swift's sweat", 900.99),
    Drinks("Coca Cola", 1.99),
    Drinks("Pepsi", 1.99),
    Drinks("Water from arctic glaciers", 300.99),
    Dessert("Ice cream with an american sausage", 2.99),
    Dessert("Fruit salad without fruit or transgenic fruit", 2.99),
    Dessert("Fruit salad with organic fruit", 200.99),
    Dessert("Snow white apple, REQUIRES_SIGNED_CONSENT", 6.99),
]
# User interaction functions
def show_menu():
    print("Menu:")
    for index, item in enumerate(menu_items):
        print(f"{index + 1}. {item.name} - ${item.price} - Category: {item.category}")
def user_order():
    show_menu()
    order = Order()
    while True:
        choice = input("Enter the menu item number (or 'done' to finish): ")
        if choice.lower() == 'done':
            break
        quantity = int(input("Enter the quantity: "))
        order.add_item(menu_items[int(choice) - 1], quantity)
    return order

# Main program
if __name__ == "__main__":
    print("WELCOME TO THE PYTHON PSYCHIATRIC RESTAURANT!")
    customer_order = user_order()
    print(f"Your total bill is: ${customer_order.calculate_total_price():.2f}")
    print(f"Your total bill after discount is: ${customer_order.apply_discount():.2f}")
    print("Thank you for dining with us!")

```
In general, this code defines a class Order that represents an order in a restaurant. Here is a step-by-step explanation of what each part of the code does:

1. Class Definition:
Order: A class to manage the items in an order and calculate the total price, including any applicable discounts.

2. Constructor:
__init__(self): Initializes an empty list items to store the items in the order.

3. Methods:
add_item(self, item, quantity): Adds an item and its quantity to the order. The item is expected to have a price attribute.
calculate_total_price(self): Calculates the total price of all items in the order by summing up the price of each item multiplied by its quantity.
ask_for_discount(self): Prompts the user to enter their population category to check if they are eligible for a discount. If the user belongs to one of the predefined categories, a 10% discount is applied; otherwise, no discount is given.
apply_discount(self): Applies the discount (if any) to the total price of the order. It first calls ask_for_discount to determine the discount percentage, then calculates the total price using calculate_total_price, and finally applies the discount to the total price.

4. User Interaction:
The ask_for_discount method interacts with the user via the console to determine their eligibility for a discount based on their population category.

# CHALLENGE_07...
implement a new Class that creates and iterable with all the items in an order, it should allow looping and contain all item attributes.

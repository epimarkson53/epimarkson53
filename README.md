# Building Materials Company Management System

class Product:
    def __init__(self, name, category, price, stock_quantity):
        self.name = name
        self.category = category
        self.price = price
        self.stock_quantity = stock_quantity

    def __str__(self):
        return f"{self.name} ({self.category}) - ${self.price} | Stock: {self.stock_quantity}"

class Company:
    def __init__(self, company_name):
        self.company_name = company_name
        self.products = []
        self.orders = []

    def add_product(self, name, category, price, stock_quantity):
        new_product = Product(name, category, price, stock_quantity)
        self.products.append(new_product)
        print(f"Product {name} added successfully!")

    def view_products(self):
        if not self.products:
            print("No products available.")
            return
        print("\nAvailable Products:")
        for product in self.products:
            print(product)

    def place_order(self, product_name, quantity):
        product = self.find_product(product_name)
        if product and product.stock_quantity >= quantity:
            product.stock_quantity -= quantity
            order_details = {"product": product_name, "quantity": quantity, "total": product.price * quantity}
            self.orders.append(order_details)
            print(f"Order placed for {quantity} units of {product_name}. Total: ${order_details['total']}")
        else:
            print(f"Not enough stock for {product_name} or product does not exist.")

    def view_orders(self):
        if not self.orders:
            print("No orders placed.")
            return
        print("\nAll Orders:")
        for order in self.orders:
            print(f"Product: {order['product']} | Quantity: {order['quantity']} | Total: ${order['total']}")

    def find_product(self, name):
        for product in self.products:
            if product.name.lower() == name.lower():
                return product
        return None


# Example Usage:

if __name__ == "__main__":
    # Create company instance
    building_company = Company("BuildRight Materials Co.")

    # Add products
    building_company.add_product("Cement", "Construction", 10.5, 100)
    building_company.add_product("Bricks", "Construction", 0.5, 500)
    building_company.add_product("Steel Rods", "Steel", 15, 200)

    # View available products
    building_company.view_products()

    # Place an order
    building_company.place_order("Cement", 20)
    building_company.place_order("Bricks", 100)

    # View placed orders
    building_company.view_orders()

    # View products after order placement
    building_company.view_products()



<!---
epimarkson53/epimarkson53 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->

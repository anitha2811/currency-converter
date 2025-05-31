# Simple Currency Converter in Python

def convert_currency(amount, from_currency, to_currency):
    # Exchange rates (base: USD)
    rates = {
        'USD': 1.0,
        'INR': 83.2,
        'EUR': 0.92,
        'JPY': 157.15,
        'GBP': 0.78
    }

    # Check if given currencies exist in our rates
    if from_currency not in rates:
        return f"Sorry, we don't support {from_currency}."
    if to_currency not in rates:
        return f"Sorry, we don't support {to_currency}."

    # Convert amount to USD first
    amount_in_usd = amount / rates[from_currency]

    # Then convert USD to target currency
    converted_amount = amount_in_usd * rates[to_currency]

    # Return rounded result
    return round(converted_amount, 2)


# --- Main Program ---

print("Welcome to Simple Currency Converter!")
print("Supported currencies: USD, INR, EUR, JPY, GBP")

try:
    amount = float(input("Enter amount: "))
    from_currency = input("Convert from (e.g. USD): ").upper()
    to_currency = input("Convert to (e.g. INR): ").upper()

    result = convert_currency(amount, from_currency, to_currency)

    print(f"\n{amount} {from_currency} is equal to {result} {to_currency}")

except ValueError:
    print("Please enter a valid number for amount.")

print("\nThank you for using the converter! 🙂")

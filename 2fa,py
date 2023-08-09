import pyotp

def generate_totp_token(secret_key):
    totp = pyotp.TOTP(secret_key)
    return totp.now()

def verify_totp_token(secret_key, token):
    totp = pyotp.TOTP(secret_key)
    return totp.verify(token)

if __name__ == "__main__":
    secret_keys = []

    num_services = int(input("Enter the number of services: "))

    for i in range(num_services):
        service_key = input(f"Enter the secret key for service {i + 1}: ")
        secret_keys.append(service_key)

    while True:
        print("\nAvailable Services:")
        for i, secret_key in enumerate(secret_keys):
            print(f"{i + 1}. Service {i + 1}")

        choice = input("\nEnter the service number (or 'q' to quit): ")
        if choice == 'q':
            break

        service_index = int(choice) - 1

        if 0 <= service_index < len(secret_keys):
            current_key = secret_keys[service_index]
            print(f"\nGenerating TOTP token for Service {service_index + 1} with secret key: {current_key}")1

            # Generate the TOTP token
            token = generate_totp_token(current_key)
            print(f"Generated TOTP token: {token}")

            # Simulate user input for verification
            user_input_token = input("Enter the TOTP token: ")

            # Verify the TOTP token
            if verify_totp_token(current_key, user_input_token):
                print("TOTP token is valid. Access granted.\n")
            else:
                print("TOTP token is invalid. Access denied.\n")
        else:
            print("Invalid choice. Please enter a valid service number.\n")

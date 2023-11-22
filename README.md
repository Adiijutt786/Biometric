import random

class Staff:
    def _init_(self, name, employee_id, fingerprint_data):
        self.name = name
        self.employee_id = employee_id
        self.fingerprint_data = fingerprint_data

class BiometricSystem:
    def _init_(self):
        self.registered_staff = []

    def register_staff(self, name, employee_id):
        fingerprint_data = self.generate_random_fingerprint()
        staff = Staff(name, employee_id, fingerprint_data)
        self.registered_staff.append(staff)
        print(f"Staff {name} with ID {employee_id} registered.")

    def verify_staff(self, employee_id, input_fingerprint):
        for staff in self.registered_staff:
            if staff.employee_id == employee_id:
                if self.compare_fingerprints(staff.fingerprint_data, input_fingerprint):
                    return f"Verification successful. Welcome, {staff.name}!"
                else:
                    return "Verification failed. Fingerprint doesn't match."
        return "Employee ID not found."

    def generate_random_fingerprint(self):
        # Simulating random fingerprint data generation
        return [random.randint(0, 1) for _ in range(100)]  # Simulated fingerprint data length

    def compare_fingerprints(self, fingerprint_data1, fingerprint_data2):
        # Simulating comparison of two fingerprint data
        # In a real system, this would involve complex algorithms for fingerprint matching
        return fingerprint_data1 == fingerprint_data2  # Simulated comparison

# Usage of BiometricSystem
biometric_system = BiometricSystem()

# Register staff members
biometric_system.register_staff("John Doe", 1001)
biometric_system.register_staff("Alice Smith", 1002)

# Simulate verification
input_fingerprint = biometric_system.generate_random_fingerprint()  # Simulated input fingerprint
verification_result = biometric_system.verify_staff(1002, input_fingerprint)
print(verification_result)# Biometric

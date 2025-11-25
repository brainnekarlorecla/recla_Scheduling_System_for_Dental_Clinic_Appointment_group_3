class AccountSystem:
    def __init__(self):
        self.users = {}  # Store usernames and passwords
        self.admin_username = ("admin")
        self.admin_password = ("admin123") 

    def sign_up(self):
        print("\n=== SIGN UP ===")
        username = input("Create a username: ")
        if username in self.users:
            print("Username already exists! Please try logging in.")
            return None

        password = input("Create a password: ")
        self.users[username] = password
        print("Account created successfully!")

    def log_in(self):
        print("\n=== LOG IN ===")
        username = input("Username: ")
        password = input("Password: ")
        if username in self.users and self.users[username] == password:
            print(f"Welcome to the Clinic, {username}!")
            return username
        elif username == self.admin_username and password == self.admin_password:
            print("Welcome Admin!")
            return "admin"
        else:
            print("Invalid username or password. Please try again.")
            return False

class Appointment:
    def __init__(self, patient_name, date, time):
        self.patient_name = patient_name
        self.date = date
        self.time = time
    def __str__(self):
        return (f"Patient: {self.patient_name}, Date: {self.date}, Time: {self.time}")
       
class Clinic:
    appointments = []

    def __init__(self):   
        pass 
    def book_appointment(self, username=None):       
        if username is None:
            patient_name = input("Enter patient's name: ")
        else:
            patient_name = username
        date = input("Enter appointment date (MM-DD-YYYY): ")
        time = input("Enter appointment time (HH:MM AM/PM): ")
        appointment = Appointment(patient_name, date, time)
        Clinic.appointments.append(appointment)
        print("Appointment booked successfully! ")

    def view_appointments(self, username=None):
        if not Clinic.appointments:   
            print("No appointment found.")
            return
        print("\nAppointments:")
        for index, appointment in enumerate(Clinic.appointments, start=1):            
            if username is None or appointment.patient_name == username:
                print(f"{index}. {appointment}")

    def cancel_appointment(self, username=None):   
        self.view_appointments(username)
        if Clinic.appointments:   
            index = int(input("Enter the appointment number to cancel: ")) -1
            if 0 <= index < len(Clinic.appointments):   
                app = Clinic.appointments[index]
                if username is None or app.patient_name == username:
                    canceled_appointment = Clinic.appointments.pop(index)
                    print(f"Canceled appointment: {canceled_appointment}")
                else:
                    print("You can only cancel your own appointments.")
            else:  
                print("Invalid appointment number.")

    def menu(self, username=None):  
        while True:
            print("\n=== Dental Clinic Appointment Menu ===")
            print("Book Appointment (Book)")
            print("View Appointment (View)")
            print("Cancel Appointment (Cancel)")
            print("Exit (E)")

            choice = input("Choose an option: ")

            if choice == "Book": 
                self.book_appointment(username)
            elif choice == 'View': 
                self.view_appointments(username)
            elif choice == 'Cancel': 
                self.cancel_appointment(username)
            elif choice == 'E':    
                print("You are now Exiting the Clinic Menu. ")
                break
            else:  
                print("Invalid choice. Please select again.")

if __name__ == "__main__":
    system = AccountSystem()

    while True:
        print("\n=== Welcome to the Dental Clinic Appointment System ===")
        print("Sign Up (S)")
        print("Log In (L)")
        print("Exit (E)")
        
        choice = input("Choose an option: ")
        if choice == "S":
            system.sign_up()
        elif choice == "L":
            logged_in = system.log_in()
            if logged_in:     
                clinic = Clinic()
                clinic.menu(logged_in if logged_in != "admin" else None)       
        elif choice == "E":
            print("Goodbye!")  
            break
        else: 
            print("Invalid choice. Please try again.")

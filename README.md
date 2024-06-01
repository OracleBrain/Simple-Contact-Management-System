# Prodigy_SD_03
PRODIGY_SD_03

```markdown
# Simple Contact Management System

This project is a simple contact management system that allows users to store and manage contact information. Users can add new contacts, view their contact list, edit existing contacts, and delete contacts. The program stores the contacts in memory during its execution.

## Features

- **Add a new contact:** Users can add contacts by entering their name, phone number, and email address.
- **View all contacts:** Users can view the list of all saved contacts.
- **Edit a contact:** Users can edit the details of an existing contact by name.
- **Delete a contact:** Users can delete a contact by name.
- **Persistent storage:** Contacts are stored in memory for the duration of the program execution.

## How to Use

1. Clone this repository to your local machine:

    ```sh
    git clone https://github.com/oraclebrain/contact-management-system.git
    ```

2. Navigate to the project directory:

    ```sh
    cd contact-management-system
    ```

3. Compile the Java program:

    ```sh
    javac ContactManager.java
    ```

4. Run the program:

    ```sh
    java ContactManager
    ```

5. Follow the on-screen prompts to manage your contacts.

## Example Usage

```
Contact Manager
1. Add a new contact
2. View all contacts
3. Edit a contact
4. Delete a contact
5. Exit
Enter your choice: 1
Enter name: Aashis Jha
Enter phone number: 1234567890
Enter email address: aashisjha@example.com
Contact added successfully!

Contact Manager
1. Add a new contact
2. View all contacts
3. Edit a contact
4. Delete a contact
5. Exit
Enter your choice: 2
Contacts:
Name: Aashis Jha, Phone Number: 1234567890, Email Address: aashisjha@example.com
```

## Code Overview

```java
import java.util.ArrayList;
import java.util.Scanner;

class Contact {
    private String name;
    private String phoneNumber;
    private String emailAddress;

    public Contact(String name, String phoneNumber, String emailAddress) {
        this.name = name;
        this.phoneNumber = phoneNumber;
        this.emailAddress = emailAddress;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public String getPhoneNumber() {
        return phoneNumber;
    }

    public void setPhoneNumber(String phoneNumber) {
        this.phoneNumber = phoneNumber;
    }

    public String getEmailAddress() {
        return emailAddress;
    }

    public void setEmailAddress(String emailAddress) {
        this.emailAddress = emailAddress;
    }

    @Override
    public String toString() {
        return "Name: " + name + ", Phone Number: " + phoneNumber + ", Email Address: " + emailAddress;
    }
}

public class ContactManager {
    private static ArrayList<Contact> contacts = new ArrayList<>();
    private static Scanner scanner = new Scanner(System.in);

    public static void main(String[] args) {
        boolean exit = false;

        while (!exit) {
            System.out.println("\nContact Manager");
            System.out.println("1. Add a new contact");
            System.out.println("2. View all contacts");
            System.out.println("3. Edit a contact");
            System.out.println("4. Delete a contact");
            System.out.println("5. Exit");
            System.out.print("Enter your choice: ");

            int choice = scanner.nextInt();
            scanner.nextLine(); // Consume newline character

            switch (choice) {
                case 1:
                    addContact();
                    break;
                case 2:
                    viewContacts();
                    break;
                case 3:
                    editContact();
                    break;
                case 4:
                    deleteContact();
                    break;
                case 5:
                    exit = true;
                    System.out.println("Exiting...");
                    break;
                default:
                    System.out.println("Invalid choice. Please enter a number between 1 and 5.");
            }
        }

        scanner.close();
    }

    private static void addContact() {
        System.out.print("Enter name: ");
        String name = scanner.nextLine();

        System.out.print("Enter phone number: ");
        String phoneNumber = scanner.nextLine();

        System.out.print("Enter email address: ");
        String emailAddress = scanner.nextLine();

        Contact contact = new Contact(name, phoneNumber, emailAddress);
        contacts.add(contact);
        System.out.println("Contact added successfully!");
    }

    private static void viewContacts() {
        if (contacts.isEmpty()) {
            System.out.println("No contacts found.");
        } else {
            System.out.println("Contacts:");
            for (Contact contact : contacts) {
                System.out.println(contact);
            }
        }
    }

    private static void editContact() {
        System.out.print("Enter the name of the contact to edit: ");
        String name = scanner.nextLine();

        for (Contact contact : contacts) {
            if (contact.getName().equalsIgnoreCase(name)) {
                System.out.print("Enter new phone number: ");
                String newPhoneNumber = scanner.nextLine();
                contact.setPhoneNumber(newPhoneNumber);

                System.out.print("Enter new email address: ");
                String newEmailAddress = scanner.nextLine();
                contact.setEmailAddress(newEmailAddress);

                System.out.println("Contact updated successfully!");
                return;
            }
        }

        System.out.println("Contact not found.");
    }

    private static void deleteContact() {
        System.out.print("Enter the name of the contact to delete: ");
        String name = scanner.nextLine();

        for (int i = 0; i < contacts.size(); i++) {
            if (contacts.get(i).getName().equalsIgnoreCase(name)) {
                contacts.remove(i);
                System.out.println("Contact deleted successfully!");
                return;
            }
        }

        System.out.println("Contact not found.");
    }
}
```

- The `Contact` class represents an individual contact with attributes for name, phone number, and email address.
- The `ContactManager` class provides a menu-driven interface for managing contacts, including adding, viewing, editing, and deleting contacts.

## Contributing

Contributions are welcome! Please open an issue or submit a pull request for any enhancements or bug fixes.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
```

Feel free to customize this `README.md` file further to suit your specific project needs or preferences.
```

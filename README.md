#include <iostream>
#include <fstream>
using namespace std;

class Account {
public:
    string name;
    int balance;

    void createAccount() {
        cout << "Enter name: ";
        cin >> name;
        cout << "Enter balance: ";
        cin >> balance;
    }

    void saveToFile() {
        ofstream file("accounts.txt", ios::app);
        file << name << " " << balance << endl;
        file.close();
    }

    void displayAccounts() {
        ifstream file("accounts.txt");
        string n;
        int b;

        while (file >> n >> b) {
            cout << "Name: " << n << ", Balance: " << b << endl;
        }
        file.close();
    }
};

int main() {
    Account acc;
    int choice;

    do {
        cout << "\n1. Create Account\n2. Display Accounts\n3. Exit\n";
        cin >> choice;

        switch (choice) {
            case 1:
                acc.createAccount();
                acc.saveToFile();
                break;
            case 2:
                acc.displayAccounts();
                break;
        }
    } while (choice != 3);

    return 0;
}

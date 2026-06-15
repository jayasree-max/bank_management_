# bank_management_
#include <iostream>
#include <fstream>
using namespace std;

class Bank {
private:
    int accNo;
    string name;
    float balance;

public:
    void createAccount() {
        cout << "\nEnter Account Number: ";
        cin >> accNo;

        cin.ignore();
        cout << "Enter Customer Name: ";
        getline(cin, name);

        cout << "Enter Initial Deposit: ";
        cin >> balance;

        saveFile();
        cout << "\nAccount Created Successfully!\n";
    }

    void saveFile() {
        ofstream file("bank.txt", ios::app);
        file << accNo << " "
             << name << " "
             << balance << endl;
        file.close();
    }

    void deposit() {
        float amount;

        cout << "Enter Current Balance: ";
        cin >> balance;

        cout << "Enter Deposit Amount: ";
        cin >> amount;

        balance += amount;

        cout << "Updated Balance: " << balance << endl;
    }

    void withdraw() {
        float amount;

        cout << "Enter Current Balance: ";
        cin >> balance;

        cout << "Enter Withdraw Amount: ";
        cin >> amount;

        if (amount <= balance) {
            balance -= amount;
            cout << "Withdrawal Successful\n";
        } else {
            cout << "Insufficient Balance\n";
        }

        cout << "Remaining Balance: " << balance << endl;
    }

    void checkBalance() {
        cout << "Enter Balance: ";
        cin >> balance;

        cout << "Current Balance: " << balance << endl;
    }
};

int main() {
    Bank b;
    int choice;

    do {
        cout << "\n===== BANK MANAGEMENT SYSTEM =====\n";
        cout << "1. Create Account\n";
        cout << "2. Deposit\n";
        cout << "3. Withdraw\n";
        cout << "4. Balance Check\n";
        cout << "5. Exit\n";

        cout << "Enter Choice: ";
        cin >> choice;

        switch(choice) {
            case 1:
                b.createAccount();
                break;

            case 2:
                b.deposit();
                break;

            case 3:
                b.withdraw();
                break;

            case 4:
                b.checkBalance();
                break;

            case 5:
                cout << "Thank You\n";
                break;

            default:
                cout << "Invalid Choice\n";
        }

    } while(choice != 5);

    return 0;
}
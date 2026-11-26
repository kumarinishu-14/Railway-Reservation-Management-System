# Railway-Reservation-Management-System
A console-based Railway Reservation Management System to handle ticket booking ,cancellation and PNR status tracking
#include <iostream>
#include <string>
using namespace std;

class Railway {
private:
    int pnr;
    string name;
    int age;
    string source, destination;
    string trainName;
    int seatNo;
    bool booked;

public:
    Railway() {
        booked = false;
    }

    void bookTicket() {
        if (booked) {
            cout << "Ticket already booked!\n";
            return;
        }

        cout << "\nEnter Passenger Name: ";
        cin >> ws;
        getline(cin, name);

        cout << "Enter Age: ";
        cin >> age;

        cout << "Enter Source: ";
        cin >> source;

        cout << "Enter Destination: ";
        cin >> destination;

        cout << "Enter Train Name: ";
        cin >> ws;
        getline(cin, trainName);

        cout << "Enter Seat Number: ";
        cin >> seatNo;

        cout << "Enter PNR Number: ";
        cin >> pnr;

        booked = true;

        cout << "\nTicket Booked Successfully!\n";
        cout << "Your PNR Number is: " << pnr << endl;
    }

    void displayTicket() {
        if (!booked) {
            cout << "\nNo Reservation Found!\n";
            return;
        }

        cout << "\n----- Passenger Details -----\n";
        cout << "PNR Number: " << pnr << endl;
        cout << "Name: " << name << endl;
        cout << "Age: " << age << endl;
        cout << "Train: " << trainName << endl;
        cout << "Source: " << source << endl;
        cout << "Destination: " << destination << endl;
        cout << "Seat Number: " << seatNo << endl;
    }

    void cancelTicket() {
        if (!booked) {
            cout << "\nNo Ticket Available!\n";
            return;
        }

        booked = false;
        cout << "\nTicket Cancelled Successfully!\n";
    }

    void searchTicket() {
        if (!booked) {
            cout << "\nNo Reservation Found!\n";
            return;
        }

        int searchPNR;
        cout << "Enter PNR Number: ";
        cin >> searchPNR;

        if (searchPNR == pnr) {
            displayTicket();
        } else {
            cout << "\nInvalid PNR Number!\n";
        }
    }
};

int main() {
    Railway r;
    int choice;

    do {
        cout << "\n===== RAILWAY RESERVATION SYSTEM =====\n";
        cout << "1. Book Ticket\n";
        cout << "2. Display Ticket\n";
        cout << "3. Cancel Ticket\n";
        cout << "4. Search Ticket\n";
        cout << "5. Exit\n";

        cout << "\nEnter Your Choice: ";
        cin >> choice;

        switch (choice) {
            case 1:
                r.bookTicket();
                break;

            case 2:
                r.displayTicket();
                break;

            case 3:
                r.cancelTicket();
                break;

            case 4:
                r.searchTicket();
                break;

            case 5:
                cout << "\nThank You for Using Railway System!\n";
                break;

            default:
                cout << "\nInvalid Choice! Try Again.\n";
        }

    } while (choice != 5);

    return 0;
}
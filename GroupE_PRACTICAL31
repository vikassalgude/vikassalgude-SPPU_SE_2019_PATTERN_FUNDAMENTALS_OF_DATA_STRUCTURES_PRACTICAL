#include <iostream>
#include <string>

using namespace std;

class CircularQueue {
private:
    int front, rear, maxSize;
    string* queue;

public:
    CircularQueue(int size) {
        maxSize = size;
        queue = new string[maxSize];
        front = -1;
        rear = -1;
    }

    ~CircularQueue() {
        delete[] queue;
    }

    bool isFull() {
        return (rear + 1) % maxSize == front;
    }

    bool isEmpty() {
        return front == -1;
    }

    void enqueue(string order) {
        if (isFull()) {
            cout << "Order queue is full. Cannot accept more orders." << endl;
            return;
        }
        if (isEmpty()) {
            front = 0; // Set front to 0 if queue was empty
        }
        rear = (rear + 1) % maxSize; // Circular increment
        queue[rear] = order; // Add new order
        cout << "Order placed: " << order << endl;
    }

    void dequeue() {
        if (isEmpty()) {
            cout << "No orders to serve." << endl;
            return;
        }
        cout << "Serving order: " << queue[front] << endl;
        if (front == rear) { // Queue has only one element
            front = -1; // Reset queue
            rear = -1;
        } else {
            front = (front + 1) % maxSize; // Circular increment
        }
    }

    void displayOrders() {
        if (isEmpty()) {
            cout << "No orders in the queue." << endl;
            return;
        }
        
        cout << "Current Orders in the Queue: ";
        int i = front;
        while (true) {
            cout << queue[i] << " ";
            if (i == rear) break; // Stop when we reach the rear
            i = (i + 1) % maxSize; // Circular increment
        }
        cout << endl;
    }
};

int main() {
    int maxOrders;

    cout << "Enter maximum number of orders the pizza parlor can accept: ";
    cin >> maxOrders;

    CircularQueue orderQueue(maxOrders);
    
    int choice;
    string order;

    do {
        cout << "\nPizza Parlor Order System\n";
        cout << "1. Place Order\n";
        cout << "2. Serve Order\n";
        cout << "3. Display Current Orders\n";
        cout << "4. Exit\n";
        cout << "Enter your choice: ";
        cin >> choice;

        switch (choice) {
            case 1:
                cout << "Enter the order description: ";
                cin.ignore(); // Clear the input buffer
                getline(cin, order);
                orderQueue.enqueue(order);
                break;

            case 2:
                orderQueue.dequeue();
                break;

            case 3:
                orderQueue.displayOrders();
                break;

            case 4:
                cout << "Exiting the system." << endl;
                break;

            default:
                cout << "Invalid choice. Please try again." << endl;
                break;
        }
    } while (choice != 4);

return 0;
}

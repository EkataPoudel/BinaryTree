# BinaryTree
Implementing the BinaryTree using C++
@Author: Ekata Poudel
@Description: This is the queue class that also implement the queue
*/

#include <iostream>
#include <array>

using namespace std;

class Queue
{
private:
    int *queue;
    int queueSize;
    int head;
    int tail;

public:
    Queue()
    {
        head = 0;
        tail = 0;
        queue = new int[10];
    }

    Queue(int queueSize)
    {
        this->queueSize = queueSize;
        queue = new int[queueSize];
    }

    ~Queue()
    {
        delete[] queue;
    }

    void enqueue(int element)
    {
        if (isFull())
        {
            throw " The queue is full.\n";
        }
        (queue[tail] = element); // ading element to the tail
        tail++;                          // increment the tail
    }

    void deque()
    {
        if (isEmpty())
        {
            throw " The queue is empty.\n";
        }
        for (int i = 0; i < tail - 1; i++)
        {
            queue[i] = queue[i + 1];
        }
        tail--; // derement the tail
    }

    bool isFull()
    {
        return queueSize == tail;
    }

    bool isEmpty()
    {
        return head == tail; // first == last
    }

    int Size()
    {
        return tail - head;
    }

    void printQueue()
    {
        if (isEmpty())
        {
            throw " The queue is empty";
        }

        for (int i = head; i < tail; i++)
        {
           cout << queue[i] << endl;
        }
        cout << endl;
    }
};
int main()
{
    Queue q;
    try{
    cout << " The queue is now created....:" <<endl;
    q.enqueue(1);
    q.enqueue(3);
    q.enqueue(2);
    q.enqueue(4);
    q.enqueue(5);
    q.enqueue(6);
    cout << "The size of the queue is:" << q.Size() << endl ;
    q.printQueue();
    q.deque();
    q.deque();
    cout << "The queue afeter dequeueing......" <<endl;
    q.printQueue();
    } catch (char* msg){
        cout << msg;

    }

}

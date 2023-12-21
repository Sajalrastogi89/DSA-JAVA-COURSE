public class CircularQueue {
    private int[] elements;
    private int front;
    private int rear;
    private int size;
    private int capacity;

    public CircularQueue(int capacity) {
        this.capacity = capacity;
        elements = new int[capacity];
        front = -1; // Initialize front and rear pointers
        rear = -1;
        size = 0;   // Current number of elements in the queue
    }

    public void enqueue(int value) {
        if (isFull()) {
            System.out.println("Queue is full. Cannot enqueue " + value);
            return;
        }
        rear = (rear + 1) % capacity; // Circular increment for rear
        elements[rear] = value;
        if (isEmpty()) {
            front = rear; // First element inserted, set front
        }
        size++;
        System.out.println("Enqueued: " + value);
    }

    public int dequeue() {
        if (isEmpty()) {
            System.out.println("Queue is empty. Cannot dequeue.");
            return -1;
        }
        int dequeuedValue = elements[front];
        if (front == rear) {
            front = -1;
            rear = -1;
        } else {
            front = (front + 1) % capacity; // Circular increment for front
        }
        size--;
        System.out.println("Dequeued: " + dequeuedValue);
        return dequeuedValue;
    }

    public int peek() {
        if (isEmpty()) {
            System.out.println("Queue is empty. No element to peek.");
            return -1;
        }
        return elements[front];
    }

    public boolean isEmpty() {
        return size == 0;
    }

    public boolean isFull() {
        return size == capacity;
    }

    public int size() {
        return size;
    }

    public static void main(String[] args) {
        CircularQueue queue = new CircularQueue(5);

        queue.enqueue(10);
        queue.enqueue(20);
        queue.enqueue(30);
        queue.enqueue(40);
        queue.enqueue(50);

        queue.dequeue();
        queue.dequeue();

        queue.enqueue(60);
        queue.enqueue(70);

        System.out.println("Front element: " + queue.peek());
        System.out.println("Queue size: " + queue.size());

        queue.dequeue();
        queue.dequeue();
        queue.dequeue();
        queue.dequeue();

        queue.dequeue();
    }
}

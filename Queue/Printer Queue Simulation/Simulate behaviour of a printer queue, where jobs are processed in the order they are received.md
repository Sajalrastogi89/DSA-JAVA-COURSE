import java.util.LinkedList;
import java.util.Queue;

// Class to represent a print job
class PrintJob {
    private String document;

    public PrintJob(String document) {
        this.document = document;
    }

    public void print() {
        System.out.println("Printing document: " + document);
    }
}

// PrinterQueue class to manage print jobs
public class PrinterQueue {
    private Queue<PrintJob> queue;

    public PrinterQueue() {
        // Initialize a FIFO queue to store print jobs
        queue = new LinkedList<>();
    }

    public void addJob(PrintJob job) {
        // Add a job to the end of the queue
        queue.offer(job);
        System.out.println("Added job: " + job.toString());
    }

    public void processJobs() {
        // Process jobs in the order they were added
        while (!queue.isEmpty()) {
            PrintJob job = queue.poll();
            job.print(); // Print the document
        }
    }

    public static void main(String[] args) {
        // Create a printer queue instance
        PrinterQueue printerQueue = new PrinterQueue();

        // Add print jobs to the printer queue
        printerQueue.addJob(new PrintJob("Document1"));
        printerQueue.addJob(new PrintJob("Document2"));
        printerQueue.addJob(new PrintJob("Document3"));

        // Process all jobs in the queue
        System.out.println("\nProcessing print jobs:");
        printerQueue.processJobs();
    }
}

import java.util.Stack;

// Example class representing an application state
class ApplicationState {
    private String content;

    public ApplicationState(String content) {
        this.content = content;
    }

    public String getContent() {
        return content;
    }

    public void setContent(String content) {
        this.content = content;
    }
}

// Class to manage undo and redo operations
public class UndoRedoStack {
    private Stack<ApplicationState> undoStack;
    private Stack<ApplicationState> redoStack;

    public UndoRedoStack() {
        undoStack = new Stack<>();
        redoStack = new Stack<>();
    }

    // Method to save current state
    public void saveState(ApplicationState state) {
        undoStack.push(state);
        redoStack.clear(); // Clear redo stack after new save
    }

    // Method to perform undo
    public ApplicationState undo() {
        if (canUndo()) {
            ApplicationState currentState = undoStack.pop();
            redoStack.push(currentState);
            return undoStack.isEmpty() ? null : undoStack.peek();
        }
        return null;
    }

    // Method to perform redo
    public ApplicationState redo() {
        if (canRedo()) {
            ApplicationState nextState = redoStack.pop();
            undoStack.push(nextState);
            return nextState;
        }
        return null;
    }

    // Check if undo operation is possible
    public boolean canUndo() {
        return !undoStack.isEmpty();
    }

    // Check if redo operation is possible
    public boolean canRedo() {
        return !redoStack.isEmpty();
    }

    public static void main(String[] args) {
        // Example usage of UndoRedoStack
        UndoRedoStack stack = new UndoRedoStack();
        ApplicationState initialState = new ApplicationState("Initial Content");

        // Save initial state
        stack.saveState(initialState);

        // Simulate state changes
        ApplicationState state1 = new ApplicationState("State 1");
        stack.saveState(state1);

        ApplicationState state2 = new ApplicationState("State 2");
        stack.saveState(state2);

        // Perform undo
        ApplicationState undoState = stack.undo();
        if (undoState != null) {
            System.out.println("Undo to: " + undoState.getContent());
        }

        // Perform redo
        ApplicationState redoState = stack.redo();
        if (redoState != null) {
            System.out.println("Redo to: " + redoState.getContent());
        }
    }
}

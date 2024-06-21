// Node class representing a node in the binary tree
class TreeNode {
    int val;
    TreeNode left, right;

    public TreeNode(int val) {
        this.val = val;
        this.left = this.right = null;
    }
}

// BinaryTree class with methods for DFS traversal
public class DepthFirstSearch {

    TreeNode root;

    // Constructor
    public DepthFirstSearch() {
        root = null;
    }

    // Method to perform DFS traversal (inorder: left, root, right)
    public void inorderDFS(TreeNode node) {
        if (node != null) {
            inorderDFS(node.left); // Visit left subtree recursively
            System.out.print(node.val + " "); // Visit root node
            inorderDFS(node.right); // Visit right subtree recursively
        }
    }

    // Method to perform DFS traversal (preorder: root, left, right)
    public void preorderDFS(TreeNode node) {
        if (node != null) {
            System.out.print(node.val + " "); // Visit root node
            preorderDFS(node.left); // Visit left subtree recursively
            preorderDFS(node.right); // Visit right subtree recursively
        }
    }

    // Method to perform DFS traversal (postorder: left, right, root)
    public void postorderDFS(TreeNode node) {
        if (node != null) {
            postorderDFS(node.left); // Visit left subtree recursively
            postorderDFS(node.right); // Visit right subtree recursively
            System.out.print(node.val + " "); // Visit root node
        }
    }

    // Driver method to test DFS traversals
    public static void main(String[] args) {
        DepthFirstSearch tree = new DepthFirstSearch();
        tree.root = new TreeNode(1);
        tree.root.left = new TreeNode(2);
        tree.root.right = new TreeNode(3);
        tree.root.left.left = new TreeNode(4);
        tree.root.left.right = new TreeNode(5);

        System.out.println("Inorder DFS traversal:");
        tree.inorderDFS(tree.root);

        System.out.println("\nPreorder DFS traversal:");
        tree.preorderDFS(tree.root);

        System.out.println("\nPostorder DFS traversal:");
        tree.postorderDFS(tree.root);
    }
}

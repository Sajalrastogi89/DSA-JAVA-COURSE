import java.util.Stack;

// Node class representing a node in the binary tree
class TreeNode {
    int val;
    TreeNode left, right;

    // Constructor to create a new node
    public TreeNode(int val) {
        this.val = val;
        left = right = null;
    }
}

// BinaryTree class containing methods for converting to mirror image using DFS
class BinaryTree {
    TreeNode root;

    // Method to convert binary tree to its mirror image using DFS
    void convertToMirror() {
        if (root == null) {
            return;
        }

        // Create a stack for iterative DFS
        Stack<TreeNode> stack = new Stack<>();
        stack.push(root);

        // Perform iterative DFS
        while (!stack.isEmpty()) {
            TreeNode node = stack.pop();

            // Swap left and right children of the current node
            TreeNode temp = node.left;
            node.left = node.right;
            node.right = temp;

            // Push left and right children to stack if they exist
            if (node.left != null) {
                stack.push(node.left);
            }
            if (node.right != null) {
                stack.push(node.right);
            }
        }
    }

    // Method to print inorder traversal of the binary tree
    void inorderTraversal(TreeNode node) {
        if (node == null) {
            return;
        }
        inorderTraversal(node.left);
        System.out.print(node.val + " ");
        inorderTraversal(node.right);
    }

    // Main method to test converting to mirror image using DFS
    public static void main(String[] args) {
        BinaryTree tree = new BinaryTree();

        // Creating a sample binary tree
        tree.root = new TreeNode(1);
        tree.root.left = new TreeNode(2);
        tree.root.right = new TreeNode(3);
        tree.root.left.left = new TreeNode(4);
        tree.root.left.right = new TreeNode(5);

        // Printing original tree (inorder traversal)
        System.out.println("Original tree (inorder traversal):");
        tree.inorderTraversal(tree.root);
        System.out.println();

        // Converting tree to its mirror image using DFS
        tree.convertToMirror();

        // Printing mirror tree (inorder traversal)
        System.out.println("Mirror tree (inorder traversal):");
        tree.inorderTraversal(tree.root);
        System.out.println();
    }
}

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

// BinaryTree class containing methods for finding diameter of binary tree using recursive approach
class BinaryTree {
    // Method to find diameter of binary tree using recursive approach
    public int diameterOfBinaryTree(TreeNode root) {
        if (root == null) {
            return 0;
        }

        // Get the height of left and right subtrees
        int leftHeight = height(root.left);
        int rightHeight = height(root.right);

        // Get the diameter of left and right subtrees recursively
        int leftDiameter = diameterOfBinaryTree(root.left);
        int rightDiameter = diameterOfBinaryTree(root.right);

        // Diameter of the tree is the maximum of:
        // 1. Diameter of left subtree
        // 2. Diameter of right subtree
        // 3. Longest path between a node in left subtree and a node in right subtree passing through the root
        return Math.max(leftHeight + rightHeight, Math.max(leftDiameter, rightDiameter));
    }

    // Method to calculate height of binary tree
    private int height(TreeNode node) {
        if (node == null) {
            return 0;
        }
        // Height of a node is 1 + maximum of the heights of its left and right subtrees
        return 1 + Math.max(height(node.left), height(node.right));
    }

    // Main method to test finding diameter of binary tree
    public static void main(String[] args) {
        BinaryTree tree = new BinaryTree();

        // Creating a sample binary tree
        TreeNode root = new TreeNode(1);
        root.left = new TreeNode(2);
        root.right = new TreeNode(3);
        root.left.left = new TreeNode(4);
        root.left.right = new TreeNode(5);

        // Finding diameter of the binary tree
        int diameter = tree.diameterOfBinaryTree(root);

        // Output the diameter of the binary tree
        System.out.println("Diameter of the binary tree is: " + diameter); // Output: 3
    }
}

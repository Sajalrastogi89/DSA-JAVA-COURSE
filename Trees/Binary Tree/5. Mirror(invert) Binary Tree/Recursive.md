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

// BinaryTree class containing methods for converting to mirror image
class BinaryTree {
    TreeNode root;

    // Method to recursively convert binary tree to its mirror image
    void convertToMirror(TreeNode node) {
        if (node == null) {
            return;
        }

        // Swap left and right subtrees
        TreeNode temp = node.left;
        node.left = node.right;
        node.right = temp;

        // Recursively convert left and right subtrees
        convertToMirror(node.left);
        convertToMirror(node.right);
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

    // Main method to test converting to mirror image
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

        // Converting tree to its mirror image
        tree.convertToMirror(tree.root);

        // Printing mirror tree (inorder traversal)
        System.out.println("Mirror tree (inorder traversal):");
        tree.inorderTraversal(tree.root);
        System.out.println();
    }
}

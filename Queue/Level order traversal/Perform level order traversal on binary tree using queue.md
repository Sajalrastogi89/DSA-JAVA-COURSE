// Node class representing a node in the binary tree
class TreeNode {
    int val;
    TreeNode left, right;

    public TreeNode(int val) {
        this.val = val;
        this.left = this.right = null;
    }
}

import java.util.LinkedList;
import java.util.Queue;

// BinaryTree class with methods for level order traversal
public class BinaryTree {
    TreeNode root;

    // Constructor
    public BinaryTree() {
        root = null;
    }

    // Method to perform level order traversal
    public void levelOrderTraversal() {
        if (root == null)
            return;

        Queue<TreeNode> queue = new LinkedList<>();
        queue.offer(root);

        while (!queue.isEmpty()) {
            TreeNode node = queue.poll();
            System.out.print(node.val + " ");

            // Enqueue left child
            if (node.left != null)
                queue.offer(node.left);

            // Enqueue right child
            if (node.right != null)
                queue.offer(node.right);
        }
    }

    // Driver method to test level order traversal
    public static void main(String[] args) {
        // Create a binary tree
        BinaryTree tree = new BinaryTree();
        tree.root = new TreeNode(1);
        tree.root.left = new TreeNode(2);
        tree.root.right = new TreeNode(3);
        tree.root.left.left = new TreeNode(4);
        tree.root.left.right = new TreeNode(5);

        System.out.println("Level Order Traversal of Binary Tree:");
        tree.levelOrderTraversal();
    }
}

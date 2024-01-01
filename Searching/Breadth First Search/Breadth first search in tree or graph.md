                import java.util.LinkedList;
import java.util.Queue;

class TreeNode {
    int val;
    TreeNode left, right;

    TreeNode(int val) {
        this.val = val;
        this.left = this.right = null;
    }
}

public class BinaryTreeBFS {

    TreeNode root;

    // Constructor
    public BinaryTreeBFS() {
        root = null;
    }

    // Method to perform BFS on a binary tree
    public void bfs(TreeNode node) {
        if (node == null) {
            return;
        }

        Queue<TreeNode> queue = new LinkedList<>();
        queue.offer(node);

        while (!queue.isEmpty()) {
            TreeNode current = queue.poll();
            System.out.print(current.val + " ");

            if (current.left != null) {
                queue.offer(current.left);
            }
            if (current.right != null) {
                queue.offer(current.right);
            }
        }
    }

    // Driver method to test BFS
    public static void main(String[] args) {
        BinaryTreeBFS tree = new BinaryTreeBFS();
        tree.root = new TreeNode(1);
        tree.root.left = new TreeNode(2);
        tree.root.right = new TreeNode(3);
        tree.root.left.left = new TreeNode(4);
        tree.root.left.right = new TreeNode(5);

        System.out.println("Breadth-First Search traversal of the binary tree:");
        tree.bfs(tree.root);
    }
}

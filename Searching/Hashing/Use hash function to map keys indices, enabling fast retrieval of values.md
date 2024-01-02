import java.util.LinkedList;

class HashNode<K, V> {
    K key;
    V value;
    HashNode<K, V> next;

    public HashNode(K key, V value) {
        this.key = key;
        this.value = value;
        this.next = null;
    }
}

class HashTable<K, V> {
    private LinkedList<HashNode<K, V>>[] chainArray;
    private int M; // Number of chains
    private int size;

    public HashTable(int M) {
        this.M = M;
        this.chainArray = new LinkedList[M];
        for (int i = 0; i < M; i++) {
            chainArray[i] = new LinkedList<>();
        }
        this.size = 0;
    }

    private int hash(K key) {
        return Math.abs(key.hashCode()) % M;
    }

    public void insert(K key, V value) {
        int index = hash(key);
        LinkedList<HashNode<K, V>> chain = chainArray[index];

        for (HashNode<K, V> node : chain) {
            if (node.key.equals(key)) {
                node.value = value; // Update the value if key already exists
                return;
            }
        }

        chain.add(new HashNode<>(key, value));
        size++;
    }

    public V search(K key) {
        int index = hash(key);
        LinkedList<HashNode<K, V>> chain = chainArray[index];

        for (HashNode<K, V> node : chain) {
            if (node.key.equals(key)) {
                return node.value;
            }
        }

        return null; // Return null if key is not found
    }

    public boolean delete(K key) {
        int index = hash(key);
        LinkedList<HashNode<K, V>> chain = chainArray[index];

        for (HashNode<K, V> node : chain) {
            if (node.key.equals(key)) {
                chain.remove(node);
                size--;
                return true;
            }
        }

        return false; // Return false if key is not found
    }

    public int size() {
        return size;
    }

    // Method to display the hash table
    public void display() {
        for (int i = 0; i < M; i++) {
            System.out.print("Chain " + i + ": ");
            for (HashNode<K, V> node : chainArray[i]) {
                System.out.print("(" + node.key + ", " + node.value + ") ");
            }
            System.out.println();
        }
    }

    public static void main(String[] args) {
        HashTable<String, Integer> hashTable = new HashTable<>(10);

        hashTable.insert("one", 1);
        hashTable.insert("two", 2);
        hashTable.insert("three", 3);
        hashTable.insert("four", 4);
        hashTable.insert("five", 5);

        System.out.println("Value for 'three': " + hashTable.search("three"));
        System.out.println("Deleting 'two': " + hashTable.delete("two"));
        System.out.println("Value for 'two' after deletion: " + hashTable.search("two"));

        hashTable.display();
        System.out.println("Size of hash table: " + hashTable.size());
    }
}

# Collection-interview
1. What is the Java Collections Framework?
Answer:
The Java Collections Framework (JCF) is a unified architecture for representing and manipulating collections, allowing them to be manipulated independently of the implementation details. It includes interfaces (List, Set, Map, etc.), implementations (ArrayList, HashSet, HashMap, etc.), and algorithms (sorting, searching, etc.).

2. Difference between Collection and Collections?
Answer:

Collection: An interface in java.util representing a group of objects.

Collections: A utility class in java.util with static methods like sort(), reverse(), shuffle().

List<String> names = new ArrayList<>();
Collections.addAll(names, "Chetan", "Ravi", "Amit");
Collections.sort(names);
System.out.println(names); // [Amit, Chetan, Ravi]

3. What is the difference between List and Set?
Answer:
List: Allows duplicates, maintains insertion order.
Set: No duplicates, may not maintain insertion order.
List<String> list = new ArrayList<>(List.of("A", "B", "A"));
System.out.println(list); // [A, B, A]

Set<String> set = new HashSet<>(Set.of("A", "B", "A"));
System.out.println(set); // [A, B]

4. What are the types of Lists in Java?
Answer:
ArrayList
LinkedList
Vector
Stack

List<String> list = new LinkedList<>();
list.add("Java");
list.add("Python");
System.out.println(list); // [Java, Python]

5. What is the difference between ArrayList and LinkedList?
Answer:
Feature                    	ArrayList	                              LinkedList
Backed by	                  Dynamic array	                          Doubly linked list
Access time	                Fast (O(1))	                            Slow (O(n))
Insertion/Deletion	        Slow at middle (O(n))	                  Fast at ends (O(1))

6. How to reverse a List in Java?
Answer:
Use Collections.reverse():
List<Integer> numbers = new ArrayList<>(List.of(1, 2, 3, 4));
Collections.reverse(numbers);
System.out.println(numbers); // [4, 3, 2, 1]
7. How to convert an array to a List?
Answer:
String[] array = {"A", "B", "C"};
List<String> list = Arrays.asList(array);
System.out.println(list); // [A, B, C]

9. How to sort a List of custom objects?
Answer:
class Student {
    String name;
    int marks;

    Student(String name, int marks) {
        this.name = name;
        this.marks = marks;
    }

    public String toString() {
        return name + " - " + marks;
    }
}

List<Student> students = new ArrayList<>();
students.add(new Student("Amit", 80));
students.add(new Student("Chetan", 95));

students.sort(Comparator.comparingInt(s -> s.marks));
System.out.println(students); // Sorted by marks

9. How to remove duplicates from a List?
Answer:
List<String> list = new ArrayList<>(List.of("A", "B", "A", "C"));
Set<String> unique = new LinkedHashSet<>(list);
System.out.println(new ArrayList<>(unique)); // [A, B, C]

10. How to iterate over a List in Java?
Answer:
List<String> list = List.of("Java", "Python", "C++");

// For-each
for (String lang : list) {
    System.out.println(lang);
}

// Iterator
Iterator<String> iterator = list.iterator();
while (iterator.hasNext()) {
    System.out.println(iterator.next());
}


11. What is a Set in Java?
Answer:
A Set is a collection that does not allow duplicate elements. It's part of the Java Collections Framework and implemented by classes like HashSet, LinkedHashSet, and TreeSet.

12. What is the difference between HashSet and TreeSet?
Answer:

Feature                  	HashSet                            	TreeSet
Order	                    Unordered	                          Sorted (natural order or comparator)
Performance	              Faster (O(1) ops)	                  Slower (O(log n))
Null	                    Allows one null	                    Does not allow null if comparator is used

13. How does HashSet work internally?
Answer:
HashSet is backed by a HashMap.
When you add an element to a HashSet, it uses hashCode() and equals() methods to ensure uniqueness.
Example:
Set<String> set = new HashSet<>();
set.add("Java");
set.add("Java"); // Duplicate ignored
System.out.println(set); // [Java]

15. What is LinkedHashSet and how is it different from HashSet?
Answer:
LinkedHashSet maintains insertion order.
HashSet does not maintain any order.

Set<String> lhs = new LinkedHashSet<>();
lhs.add("A");
lhs.add("B");
lhs.add("C");
System.out.println(lhs); // [A, B, C]

15. How do you remove duplicates from a list using Set?
Answer:
List<String> names = Arrays.asList("A", "B", "A", "C");
Set<String> set = new LinkedHashSet<>(names);
System.out.println(set); // [A, B, C]

17. What happens if you store null in a HashSet?
Answer:
HashSet allows one null value.
Example:
Set<String> set = new HashSet<>();
set.add(null);
set.add(null);
System.out.println(set); // [null]

17. What is the time complexity of add(), remove(), and contains() in HashSet?
Answer:
Average case: O(1)
Worst case (hash collisions): O(n)

18. How do you sort elements of a HashSet?
Answer:
Convert to a List and sort it.
Set<Integer> set = new HashSet<>(Set.of(3, 1, 2));
List<Integer> sorted = new ArrayList<>(set);
Collections.sort(sorted);
System.out.println(sorted); // [1, 2, 3]

20. Can we store custom objects in HashSet?
Answer:
Yes, but you must override equals() and hashCode() properly.

class Person {
    String name;
    Person(String name) { this.name = name; }

    public boolean equals(Object o) {
        return (o instanceof Person) && ((Person)o).name.equals(this.name);
    }

    public int hashCode() {
        return name.hashCode();
    }
}

Set<Person> set = new HashSet<>();
set.add(new Person("Amit"));
set.add(new Person("Amit"));
System.out.println(set.size()); // 1

20. Difference between TreeSet and LinkedHashSet?
Answer:
Feature	                          TreeSet	                                            LinkedHashSet
Order	                            Sorted order	                                      Insertion order
Nulls allowed	                    No (throws exception if comparator used)	          Yes (only one)
Performance	                      O(log n)	                                          O(1)

21. What is a Map in Java?
Answer:
A Map is an object that maps keys to values. It does not allow duplicate keys but allows duplicate values.
Map<Integer, String> map = new HashMap<>();
map.put(1, "Java");
map.put(2, "Python");

23. What is the difference between HashMap and Hashtable?
Feature	                        HashMap                                      	Hashtable
Thread Safety	                  Not thread-safe	                              Thread-safe
Nulls Allowed	                  One null key, many null values	              No null key or value
Performance                    	Faster	                                      Slower

24. How does HashMap work internally in Java?
Answer:
Backed by an array of buckets.
Hashing: hashCode() of key is used to find the bucket.
Collision resolution: uses LinkedList (before Java 8) or Balanced Tree (after Java 8 for many collisions).
equals() is used to confirm key match inside the bucket.

24. Can we have a null key in HashMap?
Answer:
Yes. HashMap allows one null key.
Map<String, Integer> map = new HashMap<>();
map.put(null, 1);
map.put(null, 2);
System.out.println(map.get(null)); // 2

26. How do you iterate over a HashMap?
Answer:
for (Map.Entry<Integer, String> entry : map.entrySet()) {
    System.out.println(entry.getKey() + " => " + entry.getValue());
}

26. What happens if two keys have the same hashCode?
Answer:
A hash collision occurs.
Keys are stored in the same bucket.
Then equals() is used to distinguish between them.

27. Difference between HashMap and LinkedHashMap?
Feature	                              HashMap	                                  LinkedHashMap
Order	                                No order                                	Maintains insertion order
Performance	                          Faster	                                  Slightly slower

28. How to sort a HashMap by keys?
Answer:
Map<Integer, String> map = new HashMap<>();
map.put(3, "C"); map.put(1, "A"); map.put(2, "B");
Map<Integer, String> sorted = new TreeMap<>(map);
System.out.println(sorted); // {1=A, 2=B, 3=C}

30. How to sort a HashMap by values?
Answer:
map.entrySet()
   .stream()
   .sorted(Map.Entry.comparingByValue())
   .forEach(System.out::println);
    
30. What is TreeMap and how is it different from HashMap?
Feature                          	TreeMap	                                    HashMap
Order	                            Sorted by keys	                            Unordered
Null key	                        Not allowed (throws NPE)                   	Allows one null key
Performance	                      O(log n)	                                  O(1) on average

31. What is a Queue in Java Collections?
Answer:
A Queue is a collection used to hold multiple elements prior to processing. It typically follows FIFO (First-In-First-Out) order.
Queue<Integer> queue = new LinkedList<>();
queue.add(1);
queue.add(2);
System.out.println(queue.poll()); // 1

33. What is the difference between Queue and Deque?
Feature	                          Queue	                                    Deque (Double Ended Queue)
Operations	                      FIFO	                                    FIFO + LIFO (both ends)
Interface                        	Queue                                    	Deque
Example	                          LinkedList                              	ArrayDeque, LinkedList

34. What is a PriorityQueue in Java?
Answer:
A PriorityQueue is a queue where elements are ordered by priority rather than insertion order.
PriorityQueue<Integer> pq = new PriorityQueue<>();
pq.add(10);
pq.add(5);
pq.add(7);
System.out.println(pq.poll()); // 5 (smallest)

34. How does PriorityQueue maintain order internally?
Answer:
It uses a binary heap (min-heap by default) to ensure that the smallest (or highest priority) element is always at the head.

35. What is the time complexity of inserting and deleting from a PriorityQueue?
Answer:
Insertion: O(log n)
Deletion (poll): O(log n)
Peek (head element): O(1)

36. Can we use custom objects in PriorityQueue?
Answer:
Yes, but you must implement Comparable or provide a Comparator.
class Person implements Comparable<Person> {
    int age;
    public Person(int age) { this.age = age; }

    public int compareTo(Person p) {
        return this.age - p.age;
    }
}

PriorityQueue<Person> pq = new PriorityQueue<>();
pq.add(new Person(30));
pq.add(new Person(25));
System.out.println(pq.poll().age); // 25

37. What are common implementations of Queue in Java?
Answer:
LinkedList
PriorityQueue
ArrayDeque
ConcurrentLinkedQueue (Thread-safe)

38. How to implement a Stack using Deque in Java?
Answer:
Deque<Integer> stack = new ArrayDeque<>();
stack.push(10);  // add to head
stack.push(20);
System.out.println(stack.pop()); // 20

40. What is the difference between ArrayDeque and LinkedList as a Deque?
Feature                      	ArrayDeque	                                    LinkedList
Performance                  	Faster (no overhead)	                        Slightly slower
Null Elements	                Not allowed                                  	Allowed
Backing	                      Resizable array                              	Doubly linked list

41. When to use PriorityQueue vs TreeSet?
Feature                        	PriorityQueue                                            	TreeSet
Order                          	Priority (heap order)	                                    Sorted (natural/custom)
Duplicates	                    Allowed                                                  	Not allowed
Access	                        Only head (poll/peek)                                    	Full access via iteration


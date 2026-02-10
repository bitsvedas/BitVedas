# THREAD – COMPLETE BASIC NOTES (FOR STUDENTS)

---

## 1. Thread क्या होता है? (Computer Level)

**Thread** किसी program के अंदर execution की सबसे छोटी इकाई (smallest unit of execution) होती है।

जब कोई program चलता है, तो वह कई छोटे-छोटे tasks में बँटकर चलता है।  
इन tasks को **threads** कहा जाता है।

### Structure:

`Program → Process → Thread`

### Definitions:

- **Program**: Disk में पड़ा हुआ code
    
- **Process**: Running program
    
- **Thread**: Process के अंदर चलने वाला independent task
    

👉 एक process में एक या एक से ज्यादा threads हो सकते हैं।

---

## 2. CPU में Thread कैसे काम करता है?

CPU instructions execute करता है।  
लेकिन CPU बहुत fast होता है, इसलिए वह:

- पहले Thread-1 execute करता है
    
- फिर Thread-2
    
- फिर Thread-3
    

यह switching इतनी तेज होती है कि user को लगता है कि सब कुछ एक साथ चल रहा है।

इस process को **Context Switching** कहते हैं।

👉 Single CPU होने पर भी multithreading possible है।

---

## 3. Java Thread क्या होता है?

Java में **Thread** एक class है जो program में multiple tasks को parallel (एक साथ) चलाने की सुविधा देती है।

Java thread का उपयोग:

- Multiple tasks को simultaneously run करने के लिए
    
- Program को fast और responsive बनाने के लिए
    
- Games, servers, animations, background tasks में
    

---

## 4. Non-Thread Program (Single Thread Program)

### Example: class MyThread extends Thread {

    public void run() {

        System.out.println("Thread is running");

    }

}

  

public class Test {

    public static void main(String[] args) {

        MyThread t = new MyThread();

        t.start();

    }

}

##### output: 
Task 1: 1
Task 1: 2
Task 1: 3
Task 1: 4
Task 1: 5
Task 2: 1
Task 2: 2
Task 2: 3
Task 2: 4
Task 2: 5
### Explanation:

- यह **single thread program** है
    
- Task 1 पूरा होने के बाद ही Task 2 शुरू होगा
    
- कोई भी काम parallel नहीं हो रहा
    

---

## 5. Java में Thread कैसे बनाते हैं? (Basic Creation)

### Thread class को extend करके

class MyThread extends Thread {

    public void run() {

        System.out.println("Thread is running");

    }

}


  

public class Test {

    public static void main(String[] args) {

        MyThread t = new MyThread();

        t.start();

    }

}

### Important Points:

- `run()` method में thread का code लिखा जाता है
    
- `start()` method नया thread बनाता है
    
- `run()` को directly call नहीं करना चाहिए
    

---

## 6. Multithreading Program (Thread वाला Program)

### Example: दो threads एक साथ चल रहे हैं

class Task1 extends Thread {
    public void run() {
        for(int i = 1; i <= 5; i++) {
            System.out.println("Task 1: " + i);
        }
    }
}

class Task2 extends Thread {
    public void run() {
        for(int i = 1; i <= 5; i++) {
            System.out.println("Task 2: " + i);
        }
    }
}

public class Test {
    public static void main(String[] args) {
        Task1 t1 = new Task1();
        Task2 t2 = new Task2();

        t1.start();
        t2.start();
    }
}

### Possible Output:

Task 1: 1
Task 2: 1
Task 1: 2
Task 2: 2
Task 2: 3
Task 1: 3
Task 1: 4
Task 2: 4
Task 1: 5
Task 2: 5
### Explanation:

- यहाँ **दो threads** हैं
    
- दोनों CPU को share कर रहे हैं
    
- Output का order fix नहीं होता
    
- दोनों tasks **simultaneously execute** होते हैं
    

---

## 7. Single Thread vs Multithreading

| Single Thread        | Multithreading        |
| -------------------- | --------------------- |
| एक ही task एक समय पर | Multiple tasks एक साथ |
| Slow execution       | Fast execution        |
| Blocking problem     | Better performance    |
| Simple programs      | Games, servers, apps  |

---

## 8. Important Exam Points

- Thread execution `start()` method से शुरू होता है
    
- हर thread का अपना stack होता है
    
- Output order predictable नहीं होता
    
- Java में multithreading performance बढ़ाती है
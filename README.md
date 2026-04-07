# COMPX234 Lab 2: Readers-Writers Problem

**Name: Junhui Luan**

**Student Number: 20243007059**

## 1. Design Explanation

This program implements a monitor-style solution for the classic Readers-Writers problem using Python's `threading.Condition` and `threading.Lock`. 

There are 4 Writers and 4 Readers initialized.

The monitor enforces the following synchronization rules:

**Multiple Readers:** Multiple reader threads can access the shared resource simultaneously as long as there is no active writer (`active_writers == 0`).

**Exclusive Writers:** A writer thread must wait if there are any active readers (`active_readers > 0`) or another active writer (`active_writers > 0`).

**Condition Checking:** `while` loops are used before `wait()` to safely re-check conditions and prevent spurious wakeups.

**Thread Signaling:** `notify_all()` is used in `end_read` (when the last reader finishes) and `end_write` to wake up waiting threads and allow them to re-evaluate the shared state.

## 2. How to Run the Program
Ensure you have Python 3 installed. Navigate to the directory containing the file and run the following command in your terminal:

```bash
python3 readers_writers_starter.py
```

## 3. Sample Output
```plaintext
Reader 2 wants to read
Reader 2 started reading. Active readers: 1
Reader 2 is READING
Reader 4 wants to read
Reader 4 started reading. Active readers: 2
Reader 4 is READING
Writer 4 wants to write
Now there are active readers/writers, writer must wait
Reader 3 wants to read
Reader 3 started reading. Active readers: 3
Reader 3 is READING
Reader 1 wants to read
Reader 1 started reading. Active readers: 4
Reader 1 is READING
Reader 4 finished reading. Active readers: 3
Reader 4 finished reading
Reader 2 finished reading. Active readers: 2
Reader 2 finished reading
Reader 4 wants to read
Reader 4 started reading. Active readers: 3
Reader 4 is READING
Writer 2 wants to write
Now there are active readers/writers, writer must wait
Reader 3 finished reading. Active readers: 2
Reader 3 finished reading
Writer 1 wants to write
Now there are active readers/writers, writer must wait
Writer 3 wants to write
Now there are active readers/writers, writer must wait
Reader 2 wants to read
Reader 2 started reading. Active readers: 3
Reader 2 is READING
Reader 1 finished reading. Active readers: 2
Reader 1 finished reading
Reader 3 wants to read
Reader 3 started reading. Active readers: 3
Reader 3 is READING
Reader 2 finished reading. Active readers: 2
Reader 2 finished reading
Reader 4 finished reading. Active readers: 1
Reader 4 finished reading
Reader 2 wants to read
Reader 2 started reading. Active readers: 2
Reader 2 is READING
Reader 1 wants to read
Reader 1 started reading. Active readers: 3
Reader 1 is READING
Reader 3 finished reading. Active readers: 2
Reader 3 finished reading
Reader 4 wants to read
Reader 4 started reading. Active readers: 3
Reader 4 is READING
Reader 1 finished reading. Active readers: 2
Reader 1 finished reading
Reader 3 wants to read
Reader 3 started reading. Active readers: 3
Reader 3 is READING
Reader 2 finished reading. Active readers: 2
Reader 2 finished reading
Reader 1 wants to read
Reader 1 started reading. Active readers: 3
Reader 1 is READING
Reader 3 finished reading. Active readers: 2
Reader 3 finished reading
Reader 1 finished reading. Active readers: 1
Reader 1 finished reading
Reader 4 finished reading. Active readers: 0
Reader 4 finished reading
Writer 1 started writing. Active writers: 1
Writer 1 is WRITING
Now there are active readers/writers, writer must wait
Now there are active readers/writers, writer must wait
Now there are active readers/writers, writer must wait
Writer 1 finished writing. Active writers: 0
Writer 1 finished writing
Writer 4 started writing. Active writers: 1
Writer 4 is WRITING
Now there are active readers/writers, writer must wait
Now there are active readers/writers, writer must wait
Writer 1 wants to write
Now there are active readers/writers, writer must wait
Writer 4 finished writing. Active writers: 0
Writer 4 finished writing
Writer 3 started writing. Active writers: 1
Writer 3 is WRITING
Now there are active readers/writers, writer must wait
Now there are active readers/writers, writer must wait
Writer 3 finished writing. Active writers: 0
Writer 3 finished writing
Writer 2 started writing. Active writers: 1
Writer 2 is WRITING
Now there are active readers/writers, writer must wait
Writer 4 wants to write
Now there are active readers/writers, writer must wait
Writer 2 finished writing. Active writers: 0
Writer 2 finished writing
Writer 1 started writing. Active writers: 1
Writer 1 is WRITING
Now there are active readers/writers, writer must wait
Writer 3 wants to write
Now there are active readers/writers, writer must wait
Writer 2 wants to write
Now there are active readers/writers, writer must wait
Writer 1 finished writing. Active writers: 0
Writer 1 finished writing
Writer 4 started writing. Active writers: 1
Writer 4 is WRITING
Now there are active readers/writers, writer must wait
Now there are active readers/writers, writer must wait
Writer 4 finished writing. Active writers: 0
Writer 4 finished writing
Writer 2 started writing. Active writers: 1
Writer 2 is WRITING
Now there are active readers/writers, writer must wait
Writer 2 finished writing. Active writers: 0
Writer 2 finished writing
Writer 3 started writing. Active writers: 1
Writer 3 is WRITING
Writer 3 finished writing. Active writers: 0
Writer 3 finished writing
!!!Simulation complete. All readers and writers have finished!!!
```
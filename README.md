# LEETCODE-Array-641
Let's go through a dry run of the `MyCircularDeque` class operations. The circular deque has a capacity of `k` and supports the following operations: inserting at the front, inserting at the rear, deleting from the front, deleting from the rear, and checking if it is full or empty. It also retrieves the front and rear values.

### Let's assume `k = 3` to test how the class works:

1. **Initialization**:
   - Call: `MyCircularDeque deque = new MyCircularDeque(3);`
   - Variables:
     - `k = 3`
     - `q = [0, 0, 0]` (array to hold elements)
     - `size = 0` (number of elements)
     - `front = 0` (initial front pointer)
     - `rear = 2` (initial rear pointer, set to `k - 1`)
   - Result: The deque is initialized but empty.

2. **Insert Front**:
   - Call: `deque.insertFront(10);`
   - Check: `isFull()` returns `false` since `size = 0`.
   - Operation:
     - Update `front`: `(front - 1 + k) % k = (-1 + 3) % 3 = 2`
     - Place the value in `q[front]`: `q[2] = 10`
     - Update `size`: `size = 1`
   - Result: The deque now contains `[0, 0, 10]`, with `front = 2`, `rear = 2`, and `size = 1`.

3. **Insert Last**:
   - Call: `deque.insertLast(20);`
   - Check: `isFull()` returns `false` since `size = 1`.
   - Operation:
     - Update `rear`: `(rear + 1) % k = (2 + 1) % 3 = 0`
     - Place the value in `q[rear]`: `q[0] = 20`
     - Update `size`: `size = 2`
   - Result: The deque now contains `[20, 0, 10]`, with `front = 2`, `rear = 0`, and `size = 2`.

4. **Insert Last**:
   - Call: `deque.insertLast(30);`
   - Check: `isFull()` returns `false` since `size = 2`.
   - Operation:
     - Update `rear`: `(rear + 1) % k = (0 + 1) % 3 = 1`
     - Place the value in `q[rear]`: `q[1] = 30`
     - Update `size`: `size = 3`
   - Result: The deque now contains `[20, 30, 10]`, with `front = 2`, `rear = 1`, and `size = 3`.

5. **Insert Front (Deque is Full)**:
   - Call: `deque.insertFront(40);`
   - Check: `isFull()` returns `true` since `size = 3` (which is equal to `k`).
   - Result: Operation fails, and the deque remains `[20, 30, 10]`.

6. **Get Front**:
   - Call: `deque.getFront();`
   - Check: `isEmpty()` returns `false` since `size = 3`.
   - Result: The front value is `q[2] = 10`.

7. **Get Rear**:
   - Call: `deque.getRear();`
   - Check: `isEmpty()` returns `false` since `size = 3`.
   - Result: The rear value is `q[1] = 30`.

8. **Delete Front**:
   - Call: `deque.deleteFront();`
   - Check: `isEmpty()` returns `false` since `size = 3`.
   - Operation:
     - Update `front`: `(front + 1) % k = (2 + 1) % 3 = 0`
     - Update `size`: `size = 2`
   - Result: The deque now contains `[20, 30, 10]` (though logically, `10` is removed), with `front = 0`, `rear = 1`, and `size = 2`.

9. **Delete Last**:
   - Call: `deque.deleteLast();`
   - Check: `isEmpty()` returns `false` since `size = 2`.
   - Operation:
     - Update `rear`: `(rear - 1 + k) % k = (1 - 1 + 3) % 3 = 0`
     - Update `size`: `size = 1`
   - Result: The deque now contains `[20, 30, 10]` (though logically, `30` is removed), with `front = 0`, `rear = 0`, and `size = 1`.

10. **Final State**:
    - `front = 0`
    - `rear = 0`
    - `size = 1`
    - Deque contents (logically): `[20]` at `q[0]`.

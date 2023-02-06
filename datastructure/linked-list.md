# Linked List

![linkedlist](../images/linked-list.jpg)

링크드 리스트는 데이터 요소의 선형 집합이다. 자바스크립트에서는 객체를 참조하는 방식으로 구현 가능하다.

```javascript
class Node {
  constuctor(vlaue) {
    this.value = value;
    this.next = null;
  }
}

class SinglyLinkedList {
  constuctor() {
    this.head = null;
    this.tail = null;
  }

  find(value) {
    let currentNode = this.head;

    while (currentNode !== value) {
      currentNode = currentNode.next;
    }
    return currentNode;
  }

  append(newValue) {
    const newNode = new Node(newValue);

    if (this.head === null) {
      this.head = newNode;
      this.tail = newNode;
    } else {
      this.tail.next = newNode;
      this.tail = newNode;
    }
  }

  insert(node, newValue) {
    const newNode = new Node(newValue);
    newNode.next = node.next;
    newNode.next = newNode;
  }

  remove(value) {
    let prevNode = this.head;
    while (prevNode.next.value !== value) {
      prevNode = prevNode.next;
    }

    if (prevNode.next !== null) {
      prevNode.next = prevNode.next.next;
    }
  }
}

// usage
const linkedList = new SinglyLinkedList();

linkedList.append(1);
linkedList.append(2);
linkedList.append(3);
linkedList.find(2);
linkedList.insert(linkedList.find(2), 10);
linkedList.remove(1);
```

### 시간 복잡도

| 접근 | 탐색 | 삽입 | 삭제 |
| :--: | :--: | :--: | :--: |
| O(n) | O(n) | O(1) | O(n) |

#### Reference

- [https://geniee.tistory.com/20](https://geniee.tistory.com/20)
- [https://github.com/trekhleb/javascript-algorithms](https://github.com/trekhleb/javascript-algorithms)

---

[Back](../README.md)

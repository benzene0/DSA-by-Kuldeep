
# Sort Linked list
Given the head of a linked list, return the list after sorting it in ascending order.

### Input: 
head = [4,2,1,3]

### Output: 
[1,2,3,4]
## code

```javascript
    ListNode* getMid(ListNode* head){
        ListNode *slow = head;
        ListNode *fast = head->next;  // ----> be care full here
        while(fast != nullptr && fast->next != nullptr){
            slow = slow->next;
            fast = fast->next->next;
        }
        return slow;
    }
    ListNode* merge(ListNode* left,ListNode* right)
    {
        ListNode* dummy = new ListNode();
        ListNode* tail = dummy;
        while(left != nullptr && right != nullptr){
            if(left->val <right->val){
                tail->next = left;
                left = left->next;
            }
            else{
                tail->next = right;
                right = right->next;
            }
            tail = tail->next;
        }
        if(left != nullptr) tail->next = left;
        if(right != nullptr) tail->next = right;
        tail = dummy->next;
        delete dummy;
        return tail;
    }
    ListNode* sortList(ListNode* head) {
        if(head== nullptr || head->next == nullptr) return head;
        
        ListNode* left = head;
        ListNode* right = getMid(head);
        ListNode* temp = right->next;
        right->next = nullptr;
        right = temp;
        
        left = sortList(left);
        right = sortList(right);
        
        return merge(left,right);
    }

```

  

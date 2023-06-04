# Leetcode

## 一、数组篇

==数组是存放在连续内存空间上的相同类型数据的集合==

我在刷数组篇的时候，给我的印象是双指针法，递归（爬楼梯），滑动窗口(其实也是双指针的一种)

我们来看看数组的结构特点

![image-20230228220356203](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230228220356203.png)

![image-20230228220332355](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230228220332355.png)

那么二维数组在内存的空间地址是连续的么？

C++的话

![image-20230228220602926](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230228220602926.png)

java的话

![image-20230228220620767](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230228220620767.png)

二分查找

> `class Solution{`
>
> `public:`
>
> `int search(vector<int> &nums,int target)`	 
>
> ​	`int left = 0;`		 
>
> `      			int right = nums.size() - 1;`//定义target在左闭右闭得区间里，[left,right]
>
> `while(left <= right){`//当left==right,区间[left,right]依然有效，所以<=
>
> `int middle = left + (right - left) / 2};`		
>
> `if(nums[middle] > target){`
>
> `right = middle - 1;}`//target 在左区间, 所以[left,middle - 1]
>
> `else if(nums[middle] < target){`
>
> `left = middle + 1}`//target 在右区间，所以[middle + 1,right]
>
> `else{`//nums[middle] == target
>
> `return middle;`
>
> `}`
>
> `return -1;`
>
> //未找到目标值
>
> `}`

2023/2/28 23：12

数组前移问题：

今天我的思路：把以为数组一维变成圆型（通过取余），但是好像不对哈哈

然后又做了一个是用一个变量temp去保存前序i的值，然后做交换

```c++
class Solution {
public:
    void rotate(vector<int>& nums, int k) {
    //我的思路是把数组一维变成园型
        int temp = 0;
        for(int j = 0 ; j < k ; j++){
           temp = nums[0];
           for(int i = 1; i < nums.size() ; i++){
               int temp1 = nums[i];
               nums[i] = temp;
               temp = temp1;
           }
           nums[0] = temp;
        }
    }
};
```

这个自己想的算法不过超时了呜呜w~w,看了看答案

其实还是很好懂的 其实就是取余的思想(分配一个新数组)

```c++
class Solution {
public:
    void rotate(vector<int>& nums, int k) {
    //我的思路是把数组一维变成园型
        int n = nums.size();
        vector<int> newArr(n);
        for(int i = 0 ; i < n;i++){
            newArr[(i + k) % n] = nums[i];
        }
        nums.assign(newArr.begin(),newArr.end());
    }
};
```

![image-20230312210810040](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230312210810040.png)

双指针法

```c++
class Solution {
    public:
    int maxArea(vector<int>& height) {
        int l = 0 , r = height.size() - 1;
        int maxarea = 0;
        while(l!=r){
            int area = (r - l) * min(height[l],height[r]);
            if(area >= maxarea) maxarea = area;
            if(height[l]>= height[r]) r--;
            else l++;
        }
        return maxarea;
    }
};
```

## 二、链表

链表和数组又不一样

链表是链式存储结构，不是一段连续分布的内存空间，而是在内存的不同位置通过逻辑关系（即指针）来连接

由两部分组成，第一部分数据域，第二部分指针域

![image-20230301192709104](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230301192709104.png)

![image-20230301192945949](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230301192945949.png)

![image-20230301193004498](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230301193004498.png)

删除链表中的某个节点：

> /**//链表结点结构
>  * Definition for singly-linked list.
>  * struct ListNode {
>  *     int val;
>  *     ListNode *next;
>  *     ListNode() : val(0), next(nullptr) {}
>  *     ListNode(int x) : val(x), next(nullptr) {}
>  *     ListNode(int x, ListNode *next) : val(x), next(next) {}
>  * };
>  */

> ​		ListNode* removeElememts(ListNode* head,int val){
>
> ​				ListNode* Head = new ListNode(0);//这里必须创个节点
>
>    			 Head ->next = head;//这里也有个细节就是这个题目给的head他是直接指向第一个结点，而不是头结点。
>						
>   			 ListNode* cur = Head;
>
> ​              while(cur->next!=nullptr){
>
> ​							if(cur->next-val == val){
>
> ​									cur->next = cur->next->next;
>
> ​							}else{
>
> ​							    	cur = cur->next;
>
> ​							}
>
> ​					}
>
> ​                 return head;
>
> }				

自己实现了一个链表类

> class MyLinkedList {
>
> public:
>
>   struct ListNode{
>
> ​    int val;
>
> ​    ListNode* next;
>
> ​    ListNode(int val):val(val),next(nullptr){}
>
>   };
>
>   MyLinkedList() {
>
> ​    this->Head = new ListNode(0);
>
> ​    this->size = 0;
>
>   }
>
>   
>
>   int get(int index) {
>
> ​    int i = 0;
>
> ​    ListNode* p = Head;
>
> ​    while(++i){
>
> ​      p = p->next;
>
> ​      if(i == index){
>
> ​        return p->val;
>
> ​      }
>
> ​    }
>
> ​    return -1;
>
>   }
>
>   
>
>   void addAtHead(int val) {
>
> ​    ListNode* p = new ListNode(val);
>
> ​    p->next = Head->next;
>
> ​    Head->next = p;
>
> ​    size++;
>
>   }
>
>   
>
>   void addAtTail(int val) {
>
> ​    ListNode* p = Head;
>
> ​    while(p->next!=nullptr){
>
> ​      p = p->next;
>
> ​    }
>
> ​    ListNode* t = new ListNode(val);
>
> ​    p->next = t;
>
> ​    size++;
>
>   }
>
>   
>
>   void addAtIndex(int index, int val) {
>
> ​    if(index > size) return;
>
> ​    else if(index < 0){
>
> ​      ListNode* node = new ListNode(val);
>
> ​      node->next = Head->next;
>
> ​      Head->next = node;
>
> ​      size++;
>
> ​    }else{
>
> ​      int l = index - 1;
>
> ​      ListNode* p = Head;
>
> ​      while(l--){
>
> ​        p = p->next;
>
> ​      }
>
> ​      ListNode* node = new ListNode(val);
>
> ​      node->next = p->next;
>
> ​      p->next = node;
>
> ​      size++;
>
> ​    }
>
>   }
>
>   
>
>   void deleteAtIndex(int index) {
>
> ​    if(index <0 || index > size) return;
>
> ​    else{
>
> ​      int l = index - 1;
>
> ​      ListNode *p = Head;
>
> ​      while(l--){
>
> ​        p = p->next;
>
> ​      }
>
> ​      p->next = p->next->next;
>
> ​      size--;
>
> ​    }
>
>   }
>
> private:
>
>   ListNode *Head;
>
>   int size;
>
> };

### 链表找环入口问题 142

- 双子指针法
- 首先一个环的入口我们是通过数学的方式去计算的
- 首先设置快指针fast，慢指针slow
- 然后我们让快指针的速度是slow的2倍
- 所以当他们相遇时，f = s + nb(s为s走的距离，b是环形个数)
- 2 * s = s + nb => s = nb 所以我们发现 发现入口a其实呢？
- 就在s的路上这时候我们只需要fast回到head，slow原地待命再走一次肯定会碰到
- 如果在路上碰到了那是入口了

```c++
class Solution {
    public:
    ListNode *detectCycle(ListNode *head) {
        ListNode* fast = head;
        ListNode* slow = head;
        while(fast!=NULL && fast->next!=NULL){
            slow = slow->next;
            fast = fast->next->next;
            if(slow==fast){
                fast = head;
                while(fast!=slow){
                    fast = fast->next;
                    slow = slow->next;
                }
                return slow;
            }
        }
        return NULL;
    }
};
```

![image-20230308212846965](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230308212846965.png)

}

两个链表合并

递归方式

```c++
class Solution {
    public:
    ListNode* mergeTwoLists(ListNode* list1, ListNode* list2) {
        if(list1 == NULL){
            return list2;
        }
        else if(list2 == NULL){
            return list1;
        }
        else if(list1->val < list2->val){
            list1->next = mergeTwoLists(list1->next,list2);
            return list1;
        }
        else{
            list2->next = mergeTwoLists(list1,list2->next);
            return list2;
        }
    }
};
```

![image-20230308231518294](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230308231518294.png)

## 三、字符串

![image-20230305000821862](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230305000821862.png)

字符串相加：

思路：![image-20230305001124459](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230305001124459.png)

```c++
class Solution {

public:

  string addStrings(string num1, string num2) {

​    int lengthA = num1.size() - 1;

​    int lengthB = num2.size() - 1;

​    string ans = "";

​    int add = 0;

​    while(lengthA >=0 || lengthB >=0 || add!=0){

​      int x = lengthA >=0 ? num1[lengthA] - '0' : 0;

​      int y = lengthB >=0 ? num2[lengthB] - '0' : 0;

​      int result = x + y + add;

​      ans.push_back('0' + result%10);

​      add = result/10;//进位

​      lengthA--;

​      lengthB--;

​    }

​    reverse(ans.begin(),ans.end());

​    return ans;

  }

};
```

四、动态规划

杨辉三角

public:

  vector<vector<int>> generate(int numRows) {

```c++
vector<vector<int>> res(numRows);

for(int i = 0 ;i < numRows ; i++){

  res[i].resize(i + 1);

  res[i][0] = res[i][i] = 1;

  for(int j = 1; j < i ; j++){

    res[i][j] = res[i-1][j-1] + res[i-1][j];

  }

}

return res;

//改进
用一个前序数组保存一个

class Solution {
public:
    vector<int> getRow(int rowIndex) {
        vector<int> pre, cur;
        for (int i = 0; i <= rowIndex; ++i) {
            cur.resize(i + 1);
            cur[0] = cur[i] = 1;
            for (int j = 1; j < i; ++j) {
                cur[j] = pre[j - 1] + pre[j];
            }
            pre = cur;
        }
        return pre;
    }
};

```

费波纳希数列

```wiki
F(0) = 0,   F(1) = 1
F(N) = F(N - 1) + F(N - 2), 其中 N > 1.
```

>  unordered_map<int,int> storemap;
>
> ​    int fib(int n){
>
> ​      if(n == 0){
>
> ​        storemap[0] = 0;
>
> ​        return 0;
>
> ​      }
>
> ​      else if(n==1||n==2){
>
> ​        storemap[n] = 1;
>
> ​        return 1;
>
> ​      }
>
> ​      else if(storemap.find(n)!=storemap.end()){
>
> ​        return storemap[n];
>
> ​      }
>
> ​      else{
>
> ​        storemap[n] = fib(n - 1) + fib(n - 2);
>
> ​        return storemap[n];
>
> ​      }
>
> ​    }



还有青蛙跳台问题

![image-20230310231313064](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230310231313064.png)

class Solution {
public:
    int numWays(int n) {
        unordered_map<int,int> store;
        if(n == 0){
            store[n] = 1;
            return 1;
        } 
        if(n == 1){
            store[n] = 1;
            return 1;
        } 
        if(store.find(n)!=store.end()) return store[n];
        else{
            int num = numWays(n - 1) + numWays(n - 2);
            store[n] = num;
            return num;
        }
    }
};







## 四、动态规划

回文子串个数

![image-20230312210336678](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230312210336678.png)

```cpp
class Solution {
public:
    int countSubstrings(string s) {
        vector<vector<bool>> dp(s.size(), vector<bool>(s.size(), false));
        int result = 0;
        for (int i = s.size() - 1; i >= 0; i--) {  // 注意遍历顺序
            for (int j = i; j < s.size(); j++) {
                if (s[i] == s[j]) {
                    if (j - i <= 1) { // 情况一 和 情况二
                        result++;
                        dp[i][j] = true;
                    } else if (dp[i + 1][j - 1]) { // 情况三
                        result++;
                        dp[i][j] = true;
                    }
                }
            }
        }
        return result;
    }
};
```

## 五、位运算

1. 交换律：a ^ b ^ c <=> a ^ c ^ b
2. 任何数于0异或为任何数 0 ^ n => n
3. 相同的数异或为0: n ^ n => 0
4. ![image-20230312221632180](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230312221632180.png)







## 六、哈希表

![image-20230315195832767](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230315195832767.png)

```c++
class Solution {
    public:
    vector<vector<string>> groupAnagrams(vector<string>& strs) {
        unordered_map<string,vector<string>> store;
        vector<vector<string>> res;
        for(auto it:strs){
            string cur = it;
            sort(cur.begin(),cur.end());
            if(store.find(cur)==store.end()){
                store[cur].push_back(it);
            }
            else if(store.find(cur)!=store.end()) store[cur].push_back(it);
        }
        for(auto it : store){
            vector<string> s;
            for(auto it1 : it.second){
                s.push_back(it1);
            }
            res.push_back(s);
        }
        return res;
    }
};
```

![image-20230315203358192](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230315203358192.png)

![image-20230315203416701](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230315203416701.png)

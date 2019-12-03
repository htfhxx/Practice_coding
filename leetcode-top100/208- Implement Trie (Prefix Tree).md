##### 题目描述
Implement a trie with insert, search, and startsWith methods.

Example:
```
Trie trie = new Trie();

trie.insert("apple");
trie.search("apple");   // returns true
trie.search("app");     // returns false
trie.startsWith("app"); // returns true
trie.insert("app");   
trie.search("app");     // returns true
```
Note:
```
You may assume that all inputs are consist of lowercase letters a-z.
All inputs are guaranteed to be non-empty strings.
```

##### 提交链接
https://leetcode.com/problems/implement-trie-prefix-tree/

##### 代码思路




##### 代码实现

```
class Node {
public:
    Node *node[26];
    bool end;
    Node(){
        memset(node,NULL,sizeof(node));
        end=false;
    }
};

class Trie {
public:
    Node *root;
    /** Initialize your data structure here. */
    Trie() {
        root=new Node();
    }
    /** Inserts a word into the trie. */
    void insert(string word) {
        Node *curr=root;
        for(int i=0;i<word.size();i++){
            if(curr->node[word[i]-'a']==NULL)
                curr->node[word[i]-'a']=new Node;
            curr=curr->node[word[i]-'a'];
        }
        curr->end=true;
        
    }
    
    /** Returns if the word is in the trie. */
    bool search(string word) {
        Node *curr=root;
        for(int i=0;i<word.size();i++){
            if(curr->node[word[i]-'a']==NULL)
                return false;
            curr=curr->node[word[i]-'a'];
        }
        if(curr->end==false)
            return false;
        return true;
    }
    
    /** Returns if there is any word in the trie that starts with the given prefix. */
    bool startsWith(string prefix) {
        Node *curr=root;
        for(int i=0;i<prefix.size();i++){
            if(curr->node[prefix[i]-'a']==NULL)
                return false;
            curr=curr->node[prefix[i]-'a'];
        }
        return true;
    }
};

/**
 * Your Trie object will be instantiated and called as such:
 * Trie* obj = new Trie();
 * obj->insert(word);
 * bool param_2 = obj->search(word);
 * bool param_3 = obj->startsWith(prefix);
 */


```

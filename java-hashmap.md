# Java HashMap 源码 阅读



```java
 final V putVal(int hash, K key, V value, boolean onlyIfAbsent,
                   boolean evict) {
        java.util.HashMap.Node<K,V>[] tab; java.util.HashMap.Node<K,V> p; int n, i;
        if ((tab = table) == null || (n = tab.length) == 0)
            n = (tab = resize()).length;
//        不存在冲突时，p 为链表中要插入的值 p 为第一个值
//         存在冲突时，p为冲突原值，e为插入的新值
//        key不存在，插入
        if ((p = tab[i = (n - 1) & hash]) == null)
            tab[i] = newNode(hash, key, value, null);
        else {
            java.util.HashMap.Node<K,V> e; K k;
//            key存在，更新value 联表结构
            if (p.hash == hash &&
                    ((k = p.key) == key || (key != null && key.equals(k))))
                e = p;
//            树结构
            else if (p instanceof java.util.HashMap.TreeNode)
                e = ((java.util.HashMap.TreeNode<K,V>)p).putTreeVal(this, tab, hash, key, value);
//            hash冲突
            else {
                for (int binCount = 0; ; ++binCount) {
//                    存放联表尾部
                    if ((e = p.next) == null) {
                        p.next = newNode(hash, key, value, null);
//                        长度大于树化阈值，转换树形结构
                        if (binCount >= TREEIFY_THRESHOLD - 1) // -1 for 1st
                            treeifyBin(tab, hash);
                        break;
                    }
//                    相同key是否存在
                    if (e.hash == hash &&
                            ((k = e.key) == key || (key != null && key.equals(k))))
                        break;
                    p = e;
                }
            }
            if (e != null) { // existing mapping for key
                V oldValue = e.value;
                if (!onlyIfAbsent || oldValue == null)
                    e.value = value;
                afterNodeAccess(e);
                return oldValue;
            }
        }
        ++modCount;
        if (++size > threshold)
            resize();
        afterNodeInsertion(evict);
        return null;
    }
```


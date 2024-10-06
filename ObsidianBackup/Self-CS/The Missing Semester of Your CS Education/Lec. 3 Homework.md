1. ![[Pasted image 20241006213611.png]]
2. （看了答案）原来正则可以使用多次，糊涂了，而且答案的匹配三次a是.\* ([\^a]\*a){3}，哦对的我一开始看成三个连续的a了，应该是三个任意数量的非 `a` 字符后跟一个 `a`。所以答案是：cat /usr/share/dict/words | tr '[:upper:]' '[:lower:]'  | grep -E "^([\^a]*a){3}.*" | grep -v "'s$" | sed -E "s/.\*([a-z]{2})/\1/" | sort | uniq -c | sort | tail -n 3 和 cat /usr/share/dict/words | tr '[:upper:]' '[:lower:]'  | grep -E "^([\^a]\*a){3}.*" | grep -v "'s\$" | sed -E "s/.*([a-z]{2})/\1/" | sort | uniq | wc -l
3. 

---
title: python_tips
date: 2019-07-23 10:36:46
tags:
---

1. #!/path/                  ---> add in the first line, to choose the interpreter
2. MUST use 4 4 4 4 spaces rather than 1 tab, have to keep consistent. Otherwise, you would get some trivial errors.
3. id2tag = dict((id_, tag) for tag, id_ in tag2id.items()) ----> transfer tag2id to id2tag with generator DICT. 
4. append vs expand   -----> a = [1,2,3], b= [4,5] , a.append(b) = [1,2,3,[4,5]]  vs  a.expand(b) = [1,2,3,4,5]


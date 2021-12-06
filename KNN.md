---
title: KNN
date: 2021-12-06 22:02:22
tags:
---

```python
from sklearn.model_selection import train_test_split
from sklearn.neighbors import KNeighborsClassifier
import csv

csvFile = open("D:\datacsv.csv", "r")
reader = csv.reader(csvFile)
iri_X=[]
iri_y=[]

for item in reader:
    # 忽略第一行
    if reader.line_num == 1:
        continue
    iri_X.append([float(item[0]),float(item[1])])
    iri_y.append(item[2])
    
X_train, X_test, y_train, y_test = train_test_split(iri_X, iri_y, test_size=0.3)
print(len(X_train))

#调用Knn算法
knn = KNeighborsClassifier(n_neighbors=3)
knn.fit(X_train, y_train)
y_predict = knn.predict(X_test)

count = 0
for i in range(len(y_predict)):
    if y_predict[i] == y_test[i]:
        count += 1
print('accuracy is %0.2f%%' % (100 * count / len(y_predict)))
```

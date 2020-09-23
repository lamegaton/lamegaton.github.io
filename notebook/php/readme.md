# PHP

### Update SQL  
https://stackoverflow.com/questions/14383503/on-duplicate-key-update-same-as-insert#answer-14383597
```
INSERT INTO table (id,a,b,c,d,e,f,g)
VALUES (1,2,3,4,5,6,7,8) 
ON DUPLICATE KEY
    UPDATE a=a, b=b, c=c, d=d, e=e, f=f, g=g;
```

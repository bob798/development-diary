

# mysql group by



- 标识列分组
- 减少文件排序

## 标识列分组

通过主键或索引分组

## 减少文件排序

若对分组后结果集顺序无要求，则可以使用order by null，让mysql不再进行文件排序。

```mysql
select user_source from user group by user_source order by null
```


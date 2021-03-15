# Mysql

### Join Update

- 형식

```sql
UPDATE [테이블명1] A 
 INNER JOIN [테이블명2] B
		ON A.[조인할 컬럼명] = B.[조인할 컬럼명]
	 SET [변경할 컬럼명] = 변경할 값
(WHERE 절)
```

- 예) 회원테이블과 후원테이블을 아이디로 INNER 조인을 건다음 회원등급이 9이면서, 후원금이 10000이상인 사람의 회원등급을 7로 변경해주는 쿼리의 예

```sql
UPDATE support_table A 
 INNER JOIN member_table B 
		ON A.sp_uid = B.user_id
	 SET B.level = 7
 WHERE B.level = 9 AND A.support_money > 10000
```

- 여러컬럼 수정시 UNION ALL 사용

```sql
UPDATE j2t_staff STF
	JOIN (
				SELECT 'juvis11' AS stf_id,  'I' AS stf_pfc_type FROM DUAL
				 UNION ALL 
				SELECT 'tjdn0621' AS stf_id,  'N' AS stf_pfc_type FROM DUAL                 
	) TOBE
		ON STF.stf_id = TOBE.stf_id
	 SET STF.stf_pfc_type = TOBE.stf_pfc_type
```

- Mybatis에서 foreach 사용해서 여러컬럼 수정시

```sql
UPDATE user A
	JOIN (
			 <foreach collection="list"  item="item"  separator="UNION ALL">
				 SELECT #{item.userId} AS user_id,  #{item.userType} AS user_type FROM DUAL
			 </foreach>
				) B
		ON A.user_id= B.user_id
	 SET A.user_type = B.user_type 
```
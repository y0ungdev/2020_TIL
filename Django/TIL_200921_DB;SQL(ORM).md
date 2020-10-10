## 09 / 21 DB : SQL(ORM)



### Relationship fields

> 모델 간 관계를 나타내는 필드

- Many to one(1:N / 일대다) : `ForeignKey()`

  ​	`Field()`라고 따로 명시되어 있지 않음.

  ​	**외래 키**라고도 함.

- Many to Many(M:N / 다대다) : `ManyToManyField()`

- One to One(1:1 / 일대일) : `OneToOneField()`

#### Foreign Key

> 외래 키는 *참조하는 테이블에서 1개의 키(속성 또는 속성의 집합*)에 해당하고, *참조하는 측의 관계 변수는 참조되는 측의 테이블의 키*를 의미함.

- 참조하는 테이블의 속성의 행 1개의 값은 참조되는 측 테이블의 행 값과 대응된다.
- <u>하나의 테이블이 여러 개의 외래 키를 포함할 수 있음.</u>

![image-20201010142148220](TIL_200921_DB;SQL(ORM).assets/image-20201010142148220.png)

> **참조 무결성의 원칙**
>
> 참조 무결성의 원칙을 어기지 않는 범위 내에서 참조할 수 있는 값에 제한되는 것은 없음(id, content, title 등 가능하지만 주로 겹치지 않을 수 있는 값을 선택)

#### ManyToOneField()


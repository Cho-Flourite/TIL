#### 코틀린 객체지향 프로그래밍
코틀린에서의 객체란? 

###### 주생성자  
Init 영역 - 주 생성자의 본문  
메인 함수에서 클래스의 객체를 생성할 때 init 영역에 작성한 코드가 자동으로 실행된다.
주 생성자의 매개변수는 init 영역안에서 지역변수로 활용하지만 Init 영역이 아닌 곳에서 함수를 만들어 매개변수를 쓸 수 없다.   
그래서 클래스 멤버 변수를 생성해서 대입 후 쓰여야 한다.   
그런데 매개변수 앞에 val, var로 선언 시 멤버 변수가 된다.
이것은 주 생성자의 매개변수만 가능하다.  

###### 보조생성자  
클래스의 본문에 constructor 키워드로 선언하는 함수 
주 생성자의 매개변수 사용하려면 this로 이어야한다.  
Constructor(name : String, count : Int): this(name)

#### 상속과생성자
클래스를 선언할 때 다른 클래스를 참조해서 선언하는 것을 상속이라고 한다.  
어떤 클래스에서 상속 받으려면 선언부에 콜론과 함께 상속받을 클래스 이름을 입력 해야한다.  
```kotlin
Open class Super {      // 상위 클래스 상속할 수 있게 open 키워드 사용
}
Class Sub: Super(){     //하위 클래스 
}
```
상위 클래스가 매개변수 있을 때 
```kotlin
open class Super(name: String) { 
}
class Sub(name: String): Super(name) { 
}
```
처럼 매개변수 구성에 맞게 인자를 전달해야 함  
● 하위 클래스에 보조 생성자만 있는 경우 상위 클래스의 생성자 호출  
```kotlin
Open class Super(name: String){ 
}
Class Sub: Super {
constructor(name: String): super(name) { 
}
}
```
##### 오버라이딩 - 재정의
##### 상속이 주는 최고의 이점은 상위 클래스에 정의된 멤버(변수, 함수)를 클래스에서 자신의 멤버처럼 사용할 수 있다는 것  
```kotlin
open class Super { 
     var superData = 10 
     fun superFun() {
         println(“i am superFun : $superData”) 
     }
}
class Sub: Super() 
fun main() {
     val obj = Sub() 
     obj.superData = 20 
     obj.superFun() 
}
```
상위 클래스의 멤버를 하위 클래스를 통해 이용할 수 있고 상위클래스 변수를 하위클래스 에서 재정의 할 수 있다.  
그 대신 상위에 오버라이드 할 함수나 변수 앞에 open 재정의 할 땐 override 키워드 써 줘야한다.  
데이터클래스1.equals(데이터클래스2) === 주 생성자의 멤버변수만 같으면 됨.  
toString()은 데이터 클래스가 아닌 일반클래스에서는 의미 있는 데이터가 아니다.  
하지만 데이터 클래스에서는 데이터 확인할 때 유용하게 사용할 수 있다.  
오브젝트 클래스는 상위 클래스를 그대로 쓸려고 가져오는 도구이다.  
```kotlin
Val apple = object() : 상위클래스(){ 
}
```
처럼 가져와서 변형하여 쓰는 거다 그런데 : 이거 뒤에 머 없으면 Any 취급 당하는데
이건 뭐 함수도 변수도 객체에 멤버가 없어서 사용 못한다. 
이 키워드로 익명 클래스를 만든다고 보면 됨
```kotlin
Companion object {
} // 를 클래스에서 설정하면 안에있는 멤버를 메인함수안에서 바로 사용 가능하다.
```





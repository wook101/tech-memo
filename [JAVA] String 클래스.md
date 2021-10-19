Java에서 String은 불변(Immutable)입니다. 그럼 불변이란 무엇일까요?   
   
 

불변은 말 그대로 아닐 불(不) 변할 변(變). 변하지 않는 것을 의미합니다.   
   
그럼 Java에서 String이 불변이라는 말에 의문이 들 수 있습니다. 아래와 같은 코드가 가능하기 때문이지요.   

String str = "first";   
str = "second";   
이처럼 Java에서 변수는 언제든 값을 바꿀 수 있는 가변입니다.   

만약 변수에 들어있는 값을 변경하지 못하게 하려면 아래와 같이 final 키워드를 붙여줘야만 합니다.   

final String str = "first";   
str = "second" // error!!   
 

그렇다면 Java의 String이 불변이라는 말은 무슨 말일까요?   

우리가 여기서 놓치면 안 되는 중요한 포인트는 String은 기본 타입(Primitive Type)이 아닌 참조 타입(Reference Type)이라는 것입니다. 즉, String은 클래스입니다.   

 

Java에서 String 객체는 특별히 String constant pool에서 따로 관리가 됩니다.   

(String constant pool과 관련된 자세한 내용은 다음 포스팅에서 다루겠습니다.)   

이 String constant pool은 Heap에 할당되어 있는데요. (Java 7 버전 이전에는 Perm 영역에서 관리 되었으나 7 버전 이후에 Heap 영역으로 옮겨졌습니다.)   

 

int num = 10;   
num = 20;   
 
String str = "abc";   
str = "def";   
 

Primitive Type인 int와 Reference Type인 String이 내부적으로 어떤 차이가 있는지 그림으로 살펴보겠습니다.   
   
![image](https://user-images.githubusercontent.com/45925158/137881242-b7260f66-7529-4810-b9cc-e539871c5032.png)   


보시다시피 int 변수 num은 변수에 할당된 스택 메모리에 값을 바로 저장하고 있기 때문에 10에서 20으로 값을 변경할 경우 변수가 갖고 있는 메모리에서 값을 변경해버립니다.    
10이라는 값이 할당되어있던 메모리 내에 값을 20으로 변경한 것이기 때문에 이는 가변이라고 할 수 있습니다.   

 

반면에 String 변수 str의 경우는 조금 다릅니다.    
그림에서 보시다시피 문자열 데이터는 스택 메모리에 직접 저장되는 것이 아니라 Heap 영역 중에서 String constant pool이라는 곳에 메모리를 할당받아 거기에 값을 저장하고, 
str은 바로 그 주소 값을 참조하게 됩니다.   

 

따라서, str = "abc" 후에 str = "def"가 실행되어 str이라는 변수가 갖는 참조 값이 0x11에서 0x22로 바뀐다 하더라도    
그건 str 변수가 갖는 참조값이 변경된 것이지 실제 "abc"가 저장되어 있는 0x11 주소의 데이터가 바뀌는 것이 아니라는 것이지요.    
Java에서 String은 이렇게 불변성을 띄게 됩니다.   

 

그러면 이제 본론으로 들어와서, Java에서 String은 왜 불변일까?에 대한 이야기를 해보겠습니다.   

 

자바가 String을 불변으로 처리하면서 얻는 이점에 대해 파악한다면, 왜 불변성을 갖게 하는지에 대해 이해할 수 있을 것 같습니다.   

앞서 언급한 바와 같이 Java는 String을 String constant pool에서 관리를 합니다. 그리고 이것이 가능한 이유가 바로 Java에서 String이 불변이기 때문입니다.    
String pool을 통해 String을 관리함으로써 Java는 Runtime에서 Heap 영역의 많은 메모리를 절약할 수 있습니다.    
왜냐면 같은 값을 갖는 String에 대해 같은 메모리를 참조하게 할 수 있기 때문입니다.    
만약 String이 불변이 아니었다면, 해당 메모리에 값이 언제 바뀔지 알 수 없기 때문에 String pool 형태로 관리할 수 없게 됩니다.   
예를 들어 a, b, c라는 String 변수가 모두 같은 메모리를 가리킬 때 a의 값을 바꿔버리면 b와 c의 값도 바뀌는 문제가 발생할 수 있습니다.   
String이 불변이 아니라면 보안상의 문제를 야기할 수 있습니다. 예를 들어, DB의 username과 password 라던가,    
소켓 통신에서 host와 port에 대한 정보가 String으로 다루어지기 때문에 String이 불변이라야 해커의 공격으로부터 값이 변경되는 것을 예방할 수 있습니다.   
String이 불변이기 때문에 멀티 쓰레딩 환경에서 안전(thread-safe)합니다. 값의 변경 가능성이 없기 때문에 멀티 쓰레딩 환경에서 동기화 문제를 걱정하지 않아도 됩니다.   
Java는 String의 hashcode를 생성 단계에서부터 캐싱합니다. 따라서 String의 hashcode는 쓰일 때마다 매번 계산되지 않습니다.    
이 특징은 특히 객체의 hashCode를 Key로 사용하는 HashMap의 경우에 효과를 발휘합니다.    
다른 객체는 키로 쓰일 때마다 hashCode를 계산하는데 비해 String은 캐싱을 하고 있기 때문에 다른 객체를 Key로 했을 때보다 String을 Key로 했을 때 더 빠른 속도로 사용할 수 있습니다.    
Java에서 String의 hashcode가 캐싱될 수 있는 이유가 바로 String이 불변이기 때문에 가능한 것입니다.   
이처럼 Java는 String을 불변으로 관리함으로써 많은 이점을 얻습니다. 그리고 이는 Java의 String이라는 클래스의 특별함이기도 한데요.    
결국엔 String도 하나의 클래스이기 때문에 우리는 우리가 정의한 커스텀 클래스를 불변 클래스로 만들 수도 있습니다.   
  

출처: https://readystory.tistory.com/139   

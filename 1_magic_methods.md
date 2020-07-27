# 특별 메서드

특별 메서드(magic methods)는 \_\_getitem__() 처럼 앞뒤에 이중 언더바를 갖고 있으며 특별 메서드는 아래와 같은 기본적인 언어 구조체를 구현하고 지원하고 사용할 수 있게 해준다. <br>
더블 언더바(double under)를 줄여서 던더(dunder)라고 부르며 특별 메서드를 던더 메서드라고도 한다.

* 반복
* 컬렉션
* 속성 접근
* 연산자 오버로딩
* 함수 및 메서드 호출
* 객체 생성 및 제거
* 문자열 표현 및 포맷
* 블록 등 콘텍스트 관리

호출 시에는 object.\_\_len__()으로 직접 호출하지 않고 len(object) 형태로 호출하는 것이 좋다.

예제
    
    from math import hypot
    
    class Vector:
    
      def __init__(self, x=0, y=0):
        self.x = x
        self.y = y
      
      def __repr__(self):
        return 'Vector(%r, %r)' % (self.x, self.y)
        
      def __abs__(self):
        return hypot(self.x, self.y)
        
      def __add__(self, other):
        x = self.x + other.x
        y = self.y + other.y
        return Vector(x, y)
      
      def __mul__(self, scalar):
        return Vector(self.x * scalar, self.y * scalar)
        
      
      if __name__ == '__main__':
        v1 = Vector(3, 4)
        v2 = Vector(2, 1)
        
        print(v1) # __str__
        print(v1 + v2) # __add__
        print(abs(v1)) #__abs__
        print(v1*3) # __mul__
        
파이썬 객체는 \_\_str__을 통해 객체를 문자열로 표현할 수 있게 한다. <br>
특별 메서드는 직접 호출하지 않고 이미 정의된 문법에 따라 파이썬 인터프리터가 호출한다.        

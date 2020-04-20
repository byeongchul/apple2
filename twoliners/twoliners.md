# 옛 감성의 두 줄 프로그램

 * Applesoft BASIC으로 작성되어 있습니다.

## matrix scene 1a


    3 text:home:dim p(15),d(15):def fn r(x)=int(x*RND(PEEK(78)+PEEK(79)*256))
    7 fori=0to14: p(i)=1+fn r(39): d(i)=(3 < fn r(10)): next: forj=1to24: fori=0to14: vtabj: htabp(i): ? chr$(32+d(i) * fn r(64));:next:next:goto 7


## matrix scene 1
    3 text:home:dim p(15),d(15)
    7 fori=0to14:p(i)=1+int(39*RND(PEEK(78)+PEEK(79)*256)):d(i)=(3 < int(10*RND(PEEK(78)+PEEK(79)*256))):next:forj=1to24:fori=0to14:vtabj:htabp(i):?chr$(32+d(i)*int(64*RND(PEEK(78)+PEEK(79)*256)));:next:next:goto 7

## 굴러가는 커서2

    3 text:home:b$="+\|/-":t=0:speed=200
    7 t=t+1:t=t*(t>=1 and t<=5)+(t>5):htab 19:? mid$(b$,t,1):goto 7

3행 : 텍스트 모두에 화면클리어 하고, b$에는 굴러가는 커서의 스프라이트가 될 캐릭터를 저장합니다.
캐릭터를 자르는 위치를 지정하 변수 t를 초기화합니다. 너무 빠르면 움직임이 보잊 않으니,
속도를 조금 늦쳐 줍니다.
if-then을 사용하기 어려운게 then 이후의 :은 모두 if 조건에 분기 되니 복잡한 논리식을사용합니다.

7행 : t를 증가시키고 논리식으로 t의 값을 1~5로 유지하고, 6이되면 0으로 초기화 합니다. 
b$에서 한 캐릭터식 잘라내어 출력하고  반복하여 굴러가는 커서로 표현합니다.

## 떨어지는 @를 패들로 조정함 (1,38 바운드 설정)
3 text:home: x=19: 
7 a=int(pdl(0)/10):s=sgn(a-13):x=x+s:x=(x<1)+x*(x>=1 and x<=37)+38*(x>37):htab x: ?"@"  : goto 7
run

## 굴러가는 커서

  3 b$="+\|/-":t=1: forj=0to100:fori=1to5:htab 10:vtab 10: ? mid$(b$,i,1):next:next

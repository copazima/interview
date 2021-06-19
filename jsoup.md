# jsoup
JAVA로 만들어진 HTML Parser이다. 

---
## jsoup으로 가능한 작업  
* URL, 파일, 문자열을 소스로 해서 HTML을 파싱할 수 있다.  
* DOM 구조를 추적하거나 익숙한 CSS 선택자를 사용해 데이터를 찾아 추출할 수 있다.  
* 문서 내의 HTML 요소, 속성, 텍스트를 조작할 수 있다.  
* 사용자가 입력한 데이터로부터 XSS(Cross-Site Script) 공격을 방지하기 위해서 안전한 화이트 리스트 방식으로 지정된 태그만 남기고 나머지는 제거할 수 있다.  
* 깔끔한 형태의 html을 출력할 수 있다.  


## jsoup의 사용법  
1. jar 파일 다운로드 받아 클래스 패스에 추가  
2. Maven에 의존성 추가  

## jsoup 예제  
1. 문서의 파싱: 문서는 URL, 파일, 문자열로부터 파싱 가능  
```
import org.jsoup.Jsoup; 
import org.jsoup.nodes.Document; 
... 
String html = "<title>First parse</title>" 
+ "<p>Parsed HTML into a doc.</p>"; 
Document doc = Jsoup.parse(html);

```
문서로부터 html tag를 모두 제거하고 순수 문자열만 얻고자 할 때는 String text = doc.text();를 사용한다.  

---
2. 문서의 body 일부분을 가지고 있는 문자열로부터 파싱  
```
import org.jsoup.Jsoup; 
import org.jsoup.nodes.Document; 
import org.jsoup.nodes.Element; 
... 
String html = "<div><p>Lorem ipsum.</p>";
Document doc = Jsoup.parseBodyFragment(html); 
Element body = doc.body();
```
doc.body() 메서드는 문서의 body 요소를 추출한다. doc.getElementByTag("body")와 동일하다.  
사용자가 웹페이지의 폼으로부터 입력한 html 태그를 포함한 입력 내용에서 cross-site scripting 공격을 피하기 위해서 화이트 리스트 기반의 tag 제거 기능을 사용할 수 있다.  

---

3. URL로부터 문서를 파싱하는 방법. GET 방식의 호출을 한다.  
```
Document doc = Jsoup.connect("http://example.com/").get(); 
String title = doc.title();
```
- POST 방식으로 사용할 수도 있다.  
```
Document doc = Jsoup.connect("http://example.com") 
.data("query", "Java") 
.userAgent("Mozilla") 
.cookie("auth", "token") 
.timeout(3000) .post();
```

---
4. 파일로부터 파싱하는 방법  
```
File input = new File("/tmp/input.html");
Document doc = Jsoup.parse(input, "UTF-8", "http://example.com/");
```
parse 메서드의 첫 번째 파라미터는 파싱할 파일의 File 객체이다.  
두 번째 파라미터는 파일의 캐릭터셋이다. 세 번째 파라미터는 파일내의 a, img 태그 등의 base url이다. base url이 없는 오버로드 된 메서드도 있다.(Jsoup.parse(input, "UTF-8");)

---

> 참고자료  
[https://offbyone.tistory.com/116]  
작성자: 다정  
작성일: 21.6.19
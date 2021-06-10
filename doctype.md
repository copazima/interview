# DOCTYPE  
> 문서 형식 선언(Document Type Declaration) 또는 DOCTYPE이란 어떤 SGML이나 XML 기반 문서 내에 그 문서가 특정 문서 형식 정의(DTD)를 따름을 지정하는 것이다. 본래 DTD에 기반한 SGML 도구를 이용해 문서 해석 가능성과 유효성을 검사하기 위한 목적으로 문서 내에 삽입되었다.  

> DOCTYPE 선언은 HTML 문서에서 \<html> 태그를 정의하기 전에 가장 먼저 선언되어야 한다.  
> DOCTYPE 선언은 HTML 태그는 아니지만 선언된 페이지의 HTML 버전이 무엇인지를 웹 브라우저에 알려주는 역할을 하는 선언문으로 대소문자를 구분하지 않는다.  
>HTML 4.01에서 DOCTYPE 선언은 SGML을 기반으로 하기 떄문에 DTD를 참조해야 한다. DTD는 브라우저가 컨텐츠를 정확하게 표현하도록 마크업 언어에 대한 규칙을 명시한다. HTML5는 SGML을 기반으로 하지 않기 때문에 DTD를 참조할 필요가 없다.  

* DTD  
이전 버전의 HTML(HTML2~HTML4)은 SGML(Standard Generalized Makrup Language)에 기반을 두어 만들어졌기 때문에 DTD 참조가 필요하며, 이 때문에 DOCTYPE 선언을 하려면 공개 식별자와 시스템 식별자가 포함된 긴 문자열을 작성해야 한다.  
HTML과 XTHML은 각 버전에서 사용 가능한 태그나 속성등을 DTD로 상세히 정의한다. DTD는 XML문서들의 클래스에 논리적인 구조를 강요하는 법칙이다. 

* HTML 4.01과 HTML5에서의 DOCTYPE 선언  
HTML 4.01에서는 DOCTYPE을 세 가지 방법으로 선언할 수 있었다.  


1. 이 DTD(Document Type Definition 문서형정의)는 모든 HTML요소와 속성들을 포함하고 있지만 더 이상 사용되지 않거나 아직 정식으로 포함되지 못한 요소들은 포함하고 있지 않다.  
```
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN" "http://www.w3.org/TR/html4/strict.dtd">
```  

2. 이 DTD는 모든 HTML 요소와 속성들뿐만 아니라 더 이상 사용되지 않거나 아직 정식으로 포함되지 못한 요소들까지도 포함하고 있다. 하지만 frameset 컨텐츠의 사용은 허용하지 않는다.  
```
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">
```  

3. 이 DTD는 모든 HTML 요소와 속성들, 더 이상 사용되지 않거나 아직 정식으로 포함되지 못한 요소들까지도 모두 포함하며, frameset 컨텐츠의 사용까지 허용한다.  
```
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Frameset//EN" "http://www.w3.org/TR/html4/frameset.dtd">
```

* HTML5에서는 단 한 가지 방법으로도 DOCTYPE을 선언할 수 있다.  
```
<!DOCTYPE html>
```

> 참고자료  
[http://tcpschool.com/html-tags/doctype]  
[https://webdir.tistory.com/40]  
[https://abcdqbbq.tistory.com/2]  
작성자: 다정  
작성일: 21.6.10
# BCF(Block Formatting Context)  
> BCF는 웹페이지를 렌더링하는 시각적 CSS의 일부로, 블록 박스의 레이아웃이 발생하는 지점과 플로팅 요소의 상호작용 범위를 결정하는 범위이다. BCF는 레이아웃에 영향을 주지만, 보통 위치 설정과 플로팅 해제를 위해 더 많이 사용한다.  

## BCF가 생성되는 경우  
* 문서의 루트 요소: \<html>  
* 플로팅 요소(float이 none이 아님)  
* 절대 위치를 지정한 요소(position이 absolute 또는 fixed)  
* 인라인 블록(display가 inline-block)  
* 표 칸(display가 table-cell, HTML 표 칸의 기본값)  
* 표 주석(display가 table-caption, HTML 표 주석의 기본값)  
* display가 table, table-row, table-row-group, table-header-group, table-footer-group(HTML 표에서 각각 표 전체, 행, 본문, 헤더, 푸터의 기본값) 또는 inline-table인 요소가 암시적으로 생성한 무명 칸  
* overflow가 visible이 아닌 블록 요소  
* display가 flow-root  
* contain이 layout, content, paint  
* 스스로 플렉스, 그리드, 테이블 컨테이너가 아닌 경우의 플렉스 항목(display가 flex 또는 inline-flex인 요소의 바로 아래 자식)  
* 스스로 플렉스, 그리드, 테이블 컨테이너가 아닌 경우의 그리드 항목(display가 grid 또는 inline-grid인 요소의 바로 아래 자식)  
* 다열 컨테이너(column-count) 또는 (column-width가 auto가 아닌 경우. column-count:1 포함)  
* column-span이 all인 경우, 해당하는 요소가 다열 컨테이너 안에 위치하지 않아도 항상 새로운 블록 서식 맥락을 생성해야 한다.  

### BCF의 특성 및 코드 참고  
[https://blueshw.github.io/2020/05/17/know-css-block-formatting-context/]

> 참고자료  
[https://developer.mozilla.org/ko/docs/Web/Guide/CSS/Block_formatting_context]  
[https://hceaan.tistory.com/101]
작성자: 다정  
작성일: 21.6.15
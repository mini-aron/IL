# Attribute.

- Atrribute란 요소의 성질,특징을 정의하는 명세이다.어트리 뷰트는 요소의 추가적인 정보를 제공한다.

---

## 글로벌 어트리뷰트(HTML Global Atrribute)

- 글로벌 어트리뷰트는 모든 HTML요소가 공통으로 사용가능한 어트리 뷰트다.몇몇 요소에는 효과가 적용되지 않을 수 있지만,대체로 모든 요소에 사용될 수 있다

| Atrribute |  |
| --- | --- |
| id | 유일한 식별자를 요소에 지정한다. 중복지정 불가능 |
| class | 스타일 시트에 정의된 class를 요소에 지정한다. 중복지정 가능 |
| hideen | css의hidden과는 다르게 의미상으로도 브라우저에 노출되지 않게 된다. |
| lang | 지정된 요소의 언어를 지정한다.검색엔진의 크롤링 시 웹페이지의 언어를 인식할 수 있게 한다. |
| style | 요소에 인라인 스타일을 지정한다. |
| tabindex | 사용자가 키보드로 페이지를 내비게이션 시 이동순서를 지정한다. |
| title | 요소에 관한 제목을 지정한다. |

## 시맨틱 웹(Semantic Web)

- 시맨틱 웹이란 웹에 존재하는 웹페이지들에 메타데이터를 부여하여, 기존의 잡다한 데이터 집합이었던 웹페이지를 의미와 관련성을 가지는 거대한 데이터베이스로 구축하고자 하는 발상이다.

| tag | Description |
| --- | --- |
| header | 헤더를 의미한다. |
| nav |  내비게이션을 의미한다. |
| aside | 사이드에 위치하는 공간을 의미한다. |
| section | 봄문의 여러내용(article)을 포함하는 공간을 의미한다. |
| article | 본문의 주내용이 들어가는 공간을 의미한다. |
| footer | 푸터를 의미한다. |

## 태그.

### 1.head 태그.

- head 요소는 메타데이터를 포함하기 위한 요소이며 웹페이지에 단 하나만 존재한다. 메타데이터는 html문서의 title,style,link,script에 대한 데이터로 화면에 표시되지 않는다. head요소에는 메타데이터 이외의 화면에 표시되는 일체의 요소를 포함시킬 수 없다.
- head 요소는 메타데이터를 포함하기 위한 요소이며 웹페이지에 단 하나만 존재한다. 메타데이터는 html문서의 title,style,link,script에 대한 데이터로 화면에 표시되지 않는다. head요소에는 메타데이터 이외의 화면에 표시되는 일체의 요소를 포함시킬 수 없다.

| tag | Description |
| --- | --- |
| title | 문서의 제목을 지정한다. |
| style | 문서를 위한 style을 지정한다. |
| link | 외부 리소스와의 연계 정보를 정의한다. 주로 CSS파일을 연계할 때 사용한다. |
| script | client-side,javascript를 정의한다.Src 어트리뷰트를 사용하여 외부 Java Script 파일을 로드할 수 있다. |
| meta | 메타데이터 정의에 사용된다. 메타데이터는 브라우저 검색엔진등에 사용된다.
<meta charset=”utf-8”>
브라우저가 사용하는 문자셋을 정의한다.
<meta http-equiv=”refresh” content=”30”>
웹 페이지를 30초 마다 refresh한다.
<meta name=”author” content=”leearon”>
웹페이지의 저자를 명시한다. |

### 2.텍스트 관련 태그.

|  |  |
| --- | --- |
| h1~h6 | 제목을 나타낼 떄 사용한다. hq이 가장 중요한 제목을 의미하며 글자 크기도 가장 크다. 시맨틱 웹의 의미를 살려서 제목 이외에는 사용하지 않는 것이 좋다. |
| b | bold체를 지정한다. 시맨틱 중요성의 의미는 없다. |
| strong | bold체를 지정한다. 시맨틱 중요성의 의미를 갖는다. 외양은 b 태그와 동일하지만 웹 표준을 준수하고자 한다면 strong을 사용하는 것이 바람직하다. |
| i | italic체를 지정한다. 시맨틱 중요성의 의미는 없다. |
| em | emphasized(강조,중요한)텍스트를 지정한다. i  태그와 동일하게 italic체로 표현된다.
시맨틱 중요성의 의미를 갖는다. |
| small | 작은 텍스트를 지정한다. |
| mark | highlighted text를 지정한다. |
| del | deleted text를 지정한다. |
| ins | inserted text를 지정한다. 밑줄이 쳐진 글씨 |
| sub/sup | sub태그는 subscrinted text, sup태그는 superscripted text를 지정한다. |
| p | 단락을 지정한다. |
| br | 강제 개행을 지정한다. 빈 요소로 종료태그가 없다. |
| pre | 형식화된 텍스트를 지정한다. pre태그 내의 content는 작성된 그대로 브라우저에 표시된다. |
| hr | 수평줄을 삽입한다. |
| q | 짧은 인용문을 지정한다. 브라우저는 인용부호(큰따옴표)로 q요소를 감싼다. |
| blockquote | 김 인용문 블록을 지정한다 CSS를 이용하여 다양한 style을 적용할 수 있다. |

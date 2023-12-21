# HTML Practice Note

## 개요
HTML에 대해 학습 및 실습한 내용을 적습니다. MDN 사이트의 HTML 튜토리얼을 참고했습니다.
- https://developer.mozilla.org/ko/

<br />

## HTML ?
HTML(Hypertext Markup Language)은 웹 페이지가 어떻게 구조화되어 있는지 브라우저에게 알려주기 위해 사용하는 마크업 언어입니다. 특정 컨텐츠를 생성 또는 수정하거나 또다른 페이지를 하이퍼링크로 연결하여 이동할 수 있습니다.

### 요소(Element)
웹 페이지 구조는 일련의 요소로 이루어져 있으며 태그(tag)로 감싸 나타냅니다. 

![element](https://developer.mozilla.org/ko/docs/Learn/Getting_started_with_the_web/HTML_basics/grumpy-cat-small.png)

어떤 요소는 속성(attribute)을 가질 수 있습니다.

![attr](https://developer.mozilla.org/ko/docs/Learn/Getting_started_with_the_web/HTML_basics/grumpy-cat-attribute-small.png)

속성은 실제 컨텐츠로 표시되지 않고 요소에 대한 추가적인 정보를 담고 있습니다. '속성명="값"'으로 나타내며 어떤 속성은 값을 가지지 않기도 합니다(ex. `required`).

속성이 항상 가져야 하는 것은 다음과 같습니다.

1. 요소 이름과 속성 사이에는 공백이 있어야 합니다. 속성이 여러개라면 속성과 속성 사이에도 공백이 있어야 합니다.

2. 속성 이름 뒤에는 등호(=)가 와야 합니다.

3. 속성 값의 앞뒤에 열고 닫는 인용부호(" 또는 ')가 있어야 합니다.

### 요소 중첩(Nesting)
요소를 다른 요소의 안에 놓을 수 있습니다.

```html
<p>My cat is <strong>very</strong> grumpy.</p>
```

### 블록(Block) 요소 vs 인라인(Inline) 요소
HTML에는 두 가지 종류의 요소가 있습니다. 바로 블록 레벨 요소와 인라인 요소입니다.

- 블록 레벨 요소는 한 줄(line)을 전부 차지하는 블록을 만들며 일반적으로 웹페이지의 구조적 요소를 나타낼 때 사용됩니다. 단락(paragraphs), 목록(lists), 네비게이션 메뉴(navigation menus), 꼬리말(footer) 등을 표현할 수 있습니다. 서로 다른 블록 요소끼리는 중첩될 수 있지만, 인라인 요소에는 중첩될 수 없습니다.

- 인라인 요소는 새로운 줄을 만들지 않으며 항상 블록 레벨 요소에 포함되어 있습니다. 문장, 단어 같은 작은 부분에 대해 사용됩니다(ex. 하이퍼링크, 텍스트).

### 빈(Empty) 요소
어떤 요소들은 내용을 갖지 않습니다.

```html
<img src="" />
<link />
<meta />
```

닫힌 태그가 따로 존재하지 않고 단일(single) 태그만으로 작성합니다.

다만, 태그의 뒷쪽에 슬래시(/)를 붙여 닫힘을 표시합니다. 대부분의 경우 슬래시를 작성하지 않아도 문제 없이 동작하지만(브라우저가 HTML을 해석할 때 자동으로 슬래시를 붙여 동작), 브라우저의 해석이 언제나 올바른 것만은 아닙니다. 따라서 예기치 않은 오류를 피하기 위해 슬래시를 명시적으로 작성하는 것을 권장합니다.

### HTML5 기본 템플릿
에밋(emmet)으로 작성되는 HTML5의 기본 템플릿은 다음과 같습니다.

```html
<!DOCTYPE html>
<html lang="ko">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width" />
  <title>Document</title>
</head>
<body>
  
</body>
</html>
```

- `<!DOCTYPE html>` : HTML 문서의 가장 첫 줄로 명시해야 하는 내용입니다. HTML 버전을 나타냅니다.

- `<html></html>` : HTML 문서의 전체 범위를 나타냅니다. 이 요소는 페이지 전체의 컨텐츠를 감싸며, 루트(root) 요소라고도 합니다. 문서의 고유 언어를 설정하는 `lang` 속성을 포함합니다.

- `<head></head>` : 사용자에게 보여지는 컨텐츠가 아닌 문서 자체의 정보를 나타냅니다. 페이지의 제목, 설명, 참조할 파일들(CSS/JS) 등을 포함합니다.

- `<meta charset="utf-8" />` : 문서가 사용할 문자 집합을 나타냅니다. 웹 초창기의 문자 코드는 'ASCII'의 로마자 위주 코드였고, 1byte 남짓의 작은 공간에 자국 문자를 할당했었습니다. 이런 상황에서 다른 국가에 이메일을 보냈더니 글자 깨짐 현상이 나타났고, 그 대책으로 4byte(32bit, 약 42억 자)의 넉넉한 공간에 세상의 모든 문자를 할당하는 방법이 제시됐습니다. 이를 유니코드(Unicode), 전 세계의 모든 문자를 다루도록 설계된 표준 문자 전산 처리 방식이라 합니다. 이로 인해 각 언어와 문자 체계에 따른 충돌 문제가 해결됐고 한글, 한자, 아랍 문자 등을 통일된 환경에서 사용할 수 있습니다. `utf`는 유니코드의 인코딩 방식 중 하나이며 현재 호환성이 가장 좋은 인코딩은 `utf-8`입니다.

- `<meta name="viewport" content="width=device-width" />` : 뷰포트의 너비에서 페이지가 렌더링하도록 하며, 모바일 브라우저가 뷰포트보다 넓은 페이지를 렌더링한 후 축소하는 것을 방지합니다.

- `<title></title>` : 브라우저의 탭에 나타나는 페이지 제목을 설정합니다.

- `<body></body>` : 사용자에게 보여지길 원하는 모든 컨텐츠를 포함합니다.

<br />

## 메타데이터(Metadata)
### `<head>` 요소
head 태그는 브라우저에 내용이 표시되지 않는 대신 페이지에 대한 메타데이터를 포함합니다.

### `<title>` 요소
head 태그에 포함되는 요소인 `<title>`은 body 태그의 최상위 부분에 들어가는 `<h1>`과 헷갈릴 수 있습니다.

- `<h1>`은 일반적으로 페이지당 한 번씩 사용되는데, 페이지 내용물의 제목이나 뉴스의 헤드라인을 표시하기 위해 표시됩니다.

- `<title>`은 문서의 컨텐츠가 아니라 HTML 문서 전체의 제목을 표현하기 위한 메타데이터입니다.

### `<meta>` 요소
HTML 문서에 메타데이터를 적용하는데에 사용합니다.

1. 문서의 문자(character) 인코딩 지정
- `<meta charset="utf-8" />`

- 위의 설명처럼, 웹 페이지에서 어떤 문자라도 취급할 수 있다는 것을 의미합니다.

- 크롬과 같은 어떤 브라우저는 자동으로 잘못된 인코딩을 고치기 때문에, 문자 깨짐 현상을 겪지 않을 수도 있습니다. 그래도 다른 브라우저에서 있을 잠재적인 문제를 피하기 위해 인코딩을 `utf-8`로 설정해야 합니다.

2. 저자와 설명 추가
```html
<meta name="author" content="my-name" />
<meta name="description" content="some-description" />
```

- 많은 `<meta>` 요소가 `name`과 `content` 속성을 가집니다. `name`은 정보의 형태, `content`는 실제 메타데이터의 컨텐츠입니다.

- 저자를 지정하는 것은 컨텐츠 작성자에 대한 정보를 볼 수 있게 해줍니다. 일부 컨텐츠 관리 시스템에는 페이지 작성자 정보를 자동으로 추출해서 사용할 수 있는 기능이 있습니다.

- 페이지 컨텐츠 관련 키워드를 포함시키는 것은 검색 엔진에서 이 페이지가 더 많이 표시될 가능성을 높여줍니다. 이러한 활동을 SEO(Search Engine Optimization)라고 합니다.

- 참고: 이외에도 많은 `<meta>` 기능들이 있지만 현재에는 더이상 사용되지 않습니다. 대표적으로 다른 검색 용어에 대해 해당 페이지의 관련성을 부여하기 위해 검색 엔진에 키워드를 제공하던 `<meta name="keywords" content="fill, in, your, keywords, here" />` 구문이 있습니다. 그러나 스팸 발송자들이 키워드 목록에 수백 개의 키워드를 채워버리는 악용 사례가 생겨버렸기 때문에 해당 기능은 검색 엔진들이 아예 무시를 해버리게 되었습니다.

3. 다른 종류의 메타데이터 삽입
```html
<meta property="og:image" content="my-og-image.png" />
<meta property="og:description" content="my-og-description" />
<meta property="og:title" content="my-og-title" />
<meta name="twitter:title" content="my-twitter-title" />
```
여러 메타데이터 중 어떤 것들은 특정 사이트(ex. SNS 사이트)에 사용할 수 있는 특정 정보를 제공하도록 설계되었습니다.

- Open Graph Data는 Facebook이 웹 사이트에 더 풍부한 메타데이터를 제공하기 위해 발명한 프로토콜입니다. 이는 사용자에게 보다 나은 정보를 보여줄 수 있습니다.

- Twitter에서도 유사한 형태의 독점 메타데이터를 가지고 있습니다.

### 커스텀 아이콘
커스텀 아이콘을 메타데이터에 추가하고 특정 컨텐츠에서 보여지게 할 수 있습니다. 이를 파비콘(favicon, favorite icon)이라 하며 16x16 픽셀의 크기를 갖습니다. 페이지의 탭이나 북마크 패널에서 볼 수 있습니다.

사이트에 파비콘을 추가하는 방법은 다음과 같습니다.

1. `index.html` 파일이 있는 디렉토리에 `.ico` 포멧의 파일을 저장합니다. 대부분의 브라우저는 `.gif` 또는 `.png`와 같은 보다 일반적인 형식의 파비콘을 지원하지만 ICO 포멧을 사용하면 IE6까지 작동합니다.

2. `<head>`에 다음 구문을 추가합니다.
```html
<link rel="shortcut icon" href="favicon.ico" type="image/x-icon" />
```

### HTML에 CSS, JS 적용하기
웹 페이지에 디자인을 더할 CSS, 사용자와 상호작용 기능을 위한 JS 파일을 적용하는 방법은 다음과 같습니다.

```html
<link rel="stylesheet" href="my-css-file.css" />
```

- `<link>`는 항상 문서의 `<head>` 부분에 위치합니다.
- `rel="stylesheet"`는 스타일 시트임을 나타냄과 동시에 해당 파일의 경로를 뜻하는 `href`를 포함합니다.

```html
<script src="my-js-file.js"></script>
```

- `<script>`는 반드시 `<head>`에 들어갈 필요는 없습니다. 주로 `</body>`의 바로 앞, 문서 본문의 맨 끝에 넣는 것이 좋으며 JS를 적용하기 전에 모든 HTML 내용을 브라우저가 읽도록 하는 것이 좋습니다. 그렇지 않을 경우 JS에서 참조하려는 HTML 요소가 아직 존재하지 않는 것으로 판단하여 에러가 날 수 있습니다.

### 문서의 기본 언어 설정
`<html>`에 페이지의 기본 언어를 설정할 수 있습니다.

```html
<html lang="ko"></html>
```

HTML 문서는 언어가 설정되어 있으면 검색 엔진에 의해 보다 효과적으로 색인화(언어별 결과에 올바르게 표시)되며 화면 판독기를 사용하는 시각장애가 있는 사용자에게 유용합니다.

또한 문서의 하위 섹션을 다른 언어로 인식하도록 설정할 수도 있습니다. 다음 구문은 일본어로 인식됩니다.

```html
<p>
  Japanese example:
  <span lang="jp">ご飯が熱い</span>
</p>
```
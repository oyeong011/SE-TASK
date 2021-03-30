# 1) Tables (extension)

## 1. table
행과 열이 있는 테이터 배열

## 구성

#### -1 " | "
각 행은 **"|"** 로 구분되는 인라인구문 분석된 임의텍스트가 포함된 셀로 구성됩니다.

#### -2. "-:"
디리미터 행은 유일한 함량이 하이픈 및 선택적으로 선행 또는 후행 결장() 또는 둘 다인 셀로 구성되어 각각 왼쪽, 오른쪽 또는 중앙 정렬을 나타냅니다.

### Ex 1
#### CODE
```txt
| foo | bar |
| --- | --- |
| baz | bim |

<table>
  <thead>
    <tr>
      <th>foo</th>
      <th>bar</th>
    </tr>
  </thead>
   <tbody>
    <tr>
      <td>baz</td>
      <td>bim</td>
    </tr>
   </tbody>
</table>
```

| foo | bar |
| --- | --- |
| baz | bim |

### Ex 2
한 열의 셀은 길이를 일치할 필요는 없지만, 이 열의 경우 읽기가 더 쉽습니다. 마찬가지로 선도 및 후행 파이프의 사용이 일치하지 않을 수 있습니다.
#### CODE
```txt
| abc | defghi |
:-: | -----------:
bar | baz

<table>
  <thead>
    <tr>
      <th align="center">abc</th>
      <th align="right">defghi</th>
    </tr>
   </thead>
  <tbody>
    <tr>
      <td align="center">bar</td>
      <td align="right">baz</td>
    </tr>
  </tbody>
</table>
```
| abc | defghi |
:-: | -----------:
bar | baz

### Ex 3
다른 인라인 범위 내부를 포함하여 셀의 내용내용에 파이프를 포함합니다.
#### CODE
```txt
| f\|oo  |
| ------ |
| b `\|` az |
| b **\|** im |

<table>
  <thead>
    <tr>
      <th>f|oo</th>
    </tr>
   </thead>
  <tbody>
    <tr>
      <td>b <code>|</code> az</td>
    </tr>
    <tr>
      <td>b <strong>|</strong> im</td>
    </tr>
  </tbody>
</table>
```
| f\|oo  |
| ------ |
| b `\|` az |
| b **\|** im |

### Ex 4
테이블이 첫 번째 빈 줄에서 깨지거나 다른 블록 수준 구조의 시작 부분에서 끊어졌습니다.
#### CODE
```txt
| abc | def |
| --- | --- |
| bar | baz |
> bar
 
<table>
  <thead>
    <tr>
      <th>abc</th>
      <th>def</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>bar</td>
      <td>baz</td>
    </tr>
  </tbody>
</table>
<blockquote>
<p>bar</p>
</blockquote>
```
| abc | def |
| --- | --- |
| bar | baz |
> bar

### Ex 5
#### CODE
```txt
| abc | def |
| --- | --- |
| bar | baz |
bar

bar

<table>
  <thead>
    <tr>
      <th>abc</th>
      <th>def</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>bar</td>
      <td>baz</td>
    </tr>
    <tr>
      <td>bar</td>
      <td></td>
    </tr>
  </tbody>
</table>
<p>bar</p>
```
| abc | def |
| --- | --- |
| bar | baz |
bar

bar

### Ex 6 
#### CODE
헤더 행은 셀 수의 데리미터 행과 일치해야 합니다. 그렇지 않은 경우 테이블은 인식되지 않습니다.
```txt 
| abc | def |
| --- |
| bar |

<p>| abc | def |
| --- |
| bar |</p>
```
| abc | def |
| --- |
| bar |

### Ex 7
테이블행의 나머지 행은 셀 수에 따라 다를 수 있습니다. 헤더 행의 셀 수보다 적은 셀이 여러 개 있는 경우 빈 셀이 삽입됩니다. 더 큰 경우 초과는 무시됩니다.
#### CODE
```txt
| abc | def |
| --- | --- |
| bar |
| bar | baz | boo |

<table>
  <thead>
    <tr>
      <th>abc</th>
      <th>def</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>bar</td>
      <td></td>
    </tr>
    <tr>
      <td>bar</td>
      <td>baz</td>
    </tr>
  </tbody>
</table>
```
| abc | def |
| --- | --- |
| bar |
| bar | baz | boo |

### Ex 8
본문에 행이 없는 경우 HTML 출력에서 생성되지 않습니다. <tbody>

#### CODE
```txt
| abc | def |
| --- | --- |
 
<table>
  <thead>
    <tr>
      <th>abc</th>
      <th>def</th>
    </tr>
  </thead>
</table>
```
| abc | def |
| --- | --- |

# 5.3 작업 목록 항목(확장)
## 1. tasklist
GFM을 사용하면 목록 항목에서 추가 처리 단계 수행을 사용할 수 있습니다.

#### * 작업 목록 항목 
```txt
  첫 번째 블록이 다른 콘텐츠 앞에 작업 목록 항목 마커와 하나 이상의 공백 문자로 시작하는 단락인 목록 항목입니다.
```
#### * 작업 목록 항목 마커
##### [x]
```txt
선택적 공간 수, 왼쪽 브래킷, 화이트스페이스 문자 또는 소문자 또는 대문자의 문자, 그리고 오른쪽 브래킷으로 구성됩니다.
 
괄호 사이의 문자가 공백 문자인 경우 확인란을 선택하지 않습니다. 그렇지 않으면 확인란을 선택합니다.
```
### Ex 1
#### CODE
```txt
- [ ] foo
- [x] bar

<ul>
<li><input disabled="" type="checkbox"> foo</li>
<li><input checked="" disabled="" type="checkbox"> bar</li>
</ul>
```
- [ ] foo
- [x] bar

### EX 2
작업 목록은 임의로 중첩될 수 있습니다.
#### CODE
```txt
- [x] foo
  - [ ] bar
  - [x] baz
- [ ] bim
 
<ul>
<li><input checked="" disabled="" type="checkbox"> foo
<ul>
<li><input disabled="" type="checkbox"> bar</li>
<li><input checked="" disabled="" type="checkbox"> baz</li>
</ul>
</li>
<li><input disabled="" type="checkbox"> bim</li>
```
- [x] foo
  - [ ] bar
  - [x] baz
- [ ] bim
  
  
# 6.5 스트라이크스루
* ~

GFM을 사용하면 추가 강조 유형을 사용할 수 있는 확장을 사용할 수 있습니다.

스트라이크스루 텍스트는 두 개의 ~로 래핑된 텍스트입니다.


### EX 1
#### CODE
```txt
~~Hi~~ Hello, world!
 
<p><del>Hi</del> Hello, world!</p>
```
~~Hi~~ Hello, world!
### EX 2
정기적인 강조 구분과 마찬가지로 새 단락으로 인해 스트라이크스루 구문 분석이 중단됩니다.
#### CODE
```txt
This ~~has a

new paragraph~~.
 
<p>This ~~has a</p>
<p>new paragraph~~.</p>
</ul>
```

This ~~has a

new paragraph~~.








# 6.9 AUTOLINK

Autolinks는 더 작은 상황에서 인식되지만 사용을 요구하지 않고 이를 구분할 수 있습니다.

> 줄의 시작 부분, 공백 후 또는 구분문자,  . < > * _ ~ ( 

* 텍스트가 발견된 다음 유효한 도메인이 있을 떄 링크가 인식 
* 유효한 도메인은 유수 문자 세그먼트, 밑줄 및 하이픈()이 기간()으로 구분된 세그먼트로 구성. 
* 하나 이상의 기간이 있어야 하며 도메인의 마지막 두 세그먼트에는 밑줄이 없을 수 있다.

> www._-.

### EX 1
#### CODE
```txt
www.commonmark.org
 
<p><a href="http://www.commonmark.org">www.commonmark.org</a></p>
```
www.commonmark.org

### EX 2
유효한 도메인이후에 공백이 없는 문자가 0개 이상 따를 수 있습니다.<
#### CODE
```txt
Visit www.commonmark.org/help for more information.
 
<p>Visit <a href="http://www.commonmark.org/help">www.commonmark.org/help</a> for more information.</p>
```
Visit www.commonmark.org/help for more information.
### EX 3
자동 링크 경로 유효성 검사를 다음과 같이 적용합니다.

후행 문장 부호 (특히,,, , , , , , 및) 그들은 링크의 내부에 포함 될 수 있지만, 자동 링크의 일부로 간주되지 않는다.

> ?!.,:*_~

#### CODE
```txt
Visit www.commonmark.org.

Visit www.commonmark.org/a.b.
 
<p>Visit <a href="http://www.commonmark.org">www.commonmark.org</a>.</p>
<p>Visit <a href="http://www.commonmark.org/a.b">www.commonmark.org/a.b</a>.</p>
```
Visit www.commonmark.org.

Visit www.commonmark.org/a.b.

### EX 4
자동 링크가 끝나면 전체 자동 링크를 검사하여 총 괄호 수를 검사합니다. 닫는 괄호가 개괄호를 여는 것보다 많은 수의 경우 괄호 안에 자동 링크를 포함하기 위해 자동 링크의 괄호 부분을 고려하지 않습니다.
> )
#### CODE
```txt
www.google.com/search?q=Markup+(business)

www.google.com/search?q=Markup+(business)))

(www.google.com/search?q=Markup+(business))

(www.google.com/search?q=Markup+(business)
 
<p><a href="http://www.google.com/search?q=Markup+(business)">www.google.com/search?q=Markup+(business)</a></p>
<p><a href="http://www.google.com/search?q=Markup+(business)">www.google.com/search?q=Markup+(business)</a>))</p>
<p>(<a href="http://www.google.com/search?q=Markup+(business)">www.google.com/search?q=Markup+(business)</a>)</p>
<p>(<a href="http://www.google.com/search?q=Markup+(business)">www.google.com/search?q=Markup+(business)</a></p>
이 검사는 링크가 닫는 괄호에서 끝날 때만 수행되므로 자동 링크 내부에 만 괄호가 있는 경우 특별한 규칙이 적용되지 않습니다.)
```
www.google.com/search?q=Markup+(business)

www.google.com/search?q=Markup+(business)))

(www.google.com/search?q=Markup+(business))

(www.google.com/search?q=Markup+(business)
### EX 5
이 검사는 링크가 닫는 괄호에서 끝날 때만 수행되므로 자동 링크 내부에 만 괄호가 있는 경우 특별한 규칙이 적용되지 않습니다.)
#### CODE
```txt
www.google.com/search?q=(business))+ok
 
<p><a href="http://www.google.com/search?q=(business))+ok">www.google.com/search?q=(business))+ok</a></p>
```
www.google.com/search?q=(business))+ok

### EX 6
자동 링크가 세미콜론(세미콜론)에서 끝나는 경우 엔터티 참조와유사한 것으로 보이는지 확인합니다. 앞의 텍스트 다음에 하나 이상의 대숫자 문자가 있습니다. 그렇다면 자동 링크에서 제외됩니다.;&
#### CODE
```txt
www.google.com/search?q=commonmark&hl=en

www.google.com/search?q=commonmark&hl;
 
<p><a href="http://www.google.com/search?q=commonmark&amp;hl=en">www.google.com/search?q=commonmark&amp;hl=en</a></p>
<p><a href="http://www.google.com/search?q=commonmark">www.google.com/search?q=commonmark</a>&amp;hl;</p>
```
www.google.com/search?q=commonmark&hl=en

www.google.com/search?q=commonmark&hl;

### EX 7
> < 
자동 링크가 즉시 종료됩니다.
#### CODE
```txt
www.commonmark.org/he<lp
 
<p><a href="http://www.commonmark.org/he">www.commonmark.org/he</a>&lt;lp</p>
```
www.commonmark.org/he<lp

### EX 8
확장된 URL 자동 링크는 스키마 중 하나 또는 유효한 도메인다음에 확장된 자동 링크 경로 유효성 검사에따라 0 개 이상의 비 공간 비 문자가 있을 때 인식됩니다.

> http://https://<

#### CODE
```txt
http://commonmark.org

(Visit https://encrypted.google.com/search?q=Markup+(business))
 
<p><a href="http://commonmark.org">http://commonmark.org</a></p>
<p>(Visit <a href="https://encrypted.google.com/search?q=Markup+(business)">https://encrypted.google.com/search?q=Markup+(business)</a>)</p>
```
http://commonmark.org

(Visit https://encrypted.google.com/search?q=Markup+(business))

### EX 9
모든 텍스트 노드 내에서 전자 메일 주소를 인식할 때 확장된 전자 메일 자동 링크가 인식됩니다. 이메일 주소는 다음 규칙에 따라 인식됩니다.

>> 한 광석은 거형, 또는 , 또는 ..-_+
>> 기호입니다.@
>> 한 개 이상의 문자는 유수또는 마침표로 구분 마지막 문자는 하나이거나 .-_.-_
>> 구성표가 생성된 링크에 자동으로 추가됩니다.mailto:
#### CODE
```txt
foo@bar.baz
 
<p><a href="mailto:foo@bar.baz">foo@bar.baz</a></p>
```
foo@bar.baz
### EX 10
> **+** 그 전에 는 발생할 수 있지만 그 후에는 발생하지 않는다.**@**

#### CODE
```txt
hello@mail+xyz.example isn't valid, but hello+xyz@mail.example is.
 
<p>hello@mail+xyz.example isn't valid, but <a href="mailto:hello+xyz@mail.example">hello+xyz@mail.example</a> is.</p>
```

hello@mail+xyz.example isn't valid, but hello+xyz@mail.example is.
### EX 11
., , 그리고 의 양쪽에서 발생할 수 있지만, 이메일 주소의 끝에서만 발생할 수 있습니다, 이 경우 주소의 일부로 간주되지 않습니다 :-_@.

#### CODE
```txt
a.b-c_d@a.b

a.b-c_d@a.b.

a.b-c_d@a.b-

a.b-c_d@a.b_
 
<p><a href="mailto:a.b-c_d@a.b">a.b-c_d@a.b</a></p>
<p><a href="mailto:a.b-c_d@a.b">a.b-c_d@a.b</a>.</p>
<p>a.b-c_d@a.b-</p>
<p>a.b-c_d@a.b_</p>
```
a.b-c_d@a.b

a.b-c_d@a.b.

a.b-c_d@a.b-

a.b-c_d@a.b_








# 6.11 허용되지 않는 원시 HTML
GFM을 사용하면 HTML 출력을 렌더링할 때 다음 HTML 태그가 필터링되는 확장을 사용할 수 있습니다.

* <title>
* <textarea>
* <style>
* <xmp>
* <iframe>
* <noembed>
* <noframes>
* <script>
* <plaintext>

필터링은 선행을 엔터티로 대체하여 수행됩니다. 이러한 태그는 특히 HTML이 고유 한 방식으로 해석되는 방식을 변경할 때 선택되며 (즉 중첩 된 HTML은 다르게 해석됨) 일반적으로 렌더링 된 다른 Markdown 콘텐츠의 컨텍스트에서 신뢰할 수 없습니다.<&lt;

다른 모든 HTML 태그는 그대로 유지됩니다.
### EX 1
#### CODE
```txt
<strong> <title> <style> <em>

<blockquote>
  <xmp> is disallowed.  <XMP> is also disallowed.
</blockquote>
 
<p><strong> &lt;title> &lt;style> <em></p>
<blockquote>
  &lt;xmp> is disallowed.  &lt;XMP> is also disallowed.
</blockquote>
```
<strong> <title> <style> <em>

<blockquote>
  <xmp> is disallowed.  <XMP> is also disallowed.
</blockquote>

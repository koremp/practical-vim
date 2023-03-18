# 4장 비주얼 모드

## Tip.20 비주얼 모드의 내부 들여다보기

일반 모드의 대다수의 명령은 비주얼 모드에서도 동일하게 작동. 비주얼 모드에서 커서가 이동할 때마다 본문에서의 선택 영역은 계속 변경된다.

* 검색 반복 - **;**
* 역방향 검색 반복 - **,**
* 패턴 일치하는 곳으로 이동하는 검색 - **n/N**

몇 가지 명령은 약간 다른 구석이 있지만 일반 모드와 거의 동일하게 동작

* **c* 명령
  * 일반 모드: c 먼저 입력하고 모션을 사용해 범위를 지정
  * 비주얼 모드: 영역 우선 선택한 다음에 바꾸기 명령을 실행

비주얼 모드에서 오퍼레이터 명령은 일반적으로 제어가 역전된(inversion of control) 방식으로 사용할 수 있다.

"March" -\> "April" 으로 변경하는 예제

* **viw**, **April**
* **viwc**, **April**

고르기 모드

* **:h Select-mode**
* **\<C-g\>* 로 비주얼-고르기 모드 전환 가능


## Tip.21 비주얼 영역 선택 정의하기

비주얼 모드는 다른 종류의 본문을 다루기 위한 세 가지 서브 모드가 있다

* 문자 단위(charater-wise) 비주얼 모드
  * 단일 문자 기준 한 행 이상에 걸쳐 영역을 지정 가능
  * 개별적인 단어나 구문 단위로 작업할 때 적합
* 행 단위(line-wise) 비주얼 모드
  * 각 행 전체를 기준으로 영역을 선택할 때 적합
* 블록 단위(block-wise) 비주얼 모드
  * 문서에서 열을 기준으로 선택해서 작업할 때 적합

### 비주얼 모드 활성화하기

* v: 문자 단위 비주얼 모드 활성화하기
* V: 행 단위 비주얼 모드 활성화하기
* \<C-v\>: 블록 단위 비주얼 모드 활성화하기
* gv: 비주얼 모드에서 마지막으로 선택했던 영역 다시 선택하기

### 비주얼 모드 간 전환하기

* \<Esc\> / \<C-\[\>: 일반 모드로 전환하기
* v / V / \<C-v\>: 일반 모드로 전환하기 (각각 문자, 행, 블록 단위 비주얼 모드일 때)
* v: 문자 단위 비주얼 모드로 전환하기
* V: 행 단위 비주얼 모드로 전환하기
* \<C-v\>: 블록 단위 비주얼 모드로 전환하기
* o: 선택 영역 중 반대쪽 끝으로 이동하기

### 선택 영역의 끝 전환하기

**o**: 선택 영역의 반대 방향의 끝을 조종할 수 있도록 커서 전환

## Tip.22 행 범위 비주얼 모드 반복하기

`visual-mode/fibonacci-malformed.py`

### 준비

`:set shiftwidth=4 softtabstop=4 expandtab`

### 들여쓰기 한 번, 그리고 반복

* **Vj**, **\>.**
  * **Vj**, **2\>**

비주얼 모드 명령을 반복하기 위해 점 명령을 사용하면 가장 마지막으로 선택했던 범위만큼 본문을 선택한 후 동작

## Tip.23 가능하면 비주얼 명령 대신 오퍼레이터 명령 사용하기

`visual-mode/list-of-links.html`

**vit** 명령

* 태그 안의 내용을 선택할 수 있다
* 태그 내에 있는 내용을 선택하라의 약어
  * visually select inside the tag

**it** 명령: 택스트 객체(text object)라고 하는 특별한 종류의 모션을 의미

### 비주얼 오퍼페이터 사용하기

* **U* 명령: 선택한 문자를 대문자로 전환
  * **:h v_U**

**vit**, **U**, **.**

**:h visual-repeat**

### 일반 오퍼레이터 명령 사용하기

**U** 명령 - gU{모션}

* **gUit**, **j.**, **j.**

### 토론

**vitU**, **gUit* 명령의 차이점

* **vitU**
  * **vit**: 선택
  * **U**: 선택 영역 조작
* **gUit**
  * **gU**: 오퍼레이터를 포함한 명령
  * **it**: 모션

비주얼 모드에서 반복 작업을 위한 변경점을 만드는 과정보다 동일한 기능의 오퍼레이터 명령을 사용해서 반복 작업을 처리하는 것이 더 편리하며 훨씬 일반적인 접근 방식이다.

변경이 일회성이라면 비주얼 모드에서 편집하는 것이 더 적절하다.

## Tip.24 탭으로 된 데이터를 비주얼 블록 모드로 편집하기

`visual-mode/chapter-table.txt`

두 열 사이에 파이프(|) 문자로 세로선을 그리려고 한다.

* **\<C-v\>3j**: 비주얼 블록 모드로 진입, 커서를 아래로 이동해서 열을 기준으로 여러 행을 선택
* **x...**: **x**를 눌러 선택한 열을 제거하고 점 명령을 반복적으로 눌러서 같은 범위의 문서를 여러 번 제거한다. 두 열의 간격이 적당해질 때까지 반복
  * 점 명령을 사용하는 대신에 열을 선택한 커서를 우측으로 두세 칸 이동하는 방법으로 넓은 범위를 한번에 선택할 수 있다.
  * 한 열씩 제거하면 제거할 때마다 시각적으로 바로 확인할 수 있으므로 한 열씩 제거하는 방법이 낫다.
* **gv**: 마지막으로 선택했던 범위를 **gv* 명령으로 다시 선택한다.
* **r|**: 각각의 선택 영역으로 지정한 범위를 모두 파이프 문자로 대체한다.
* **yyp**: 행 단위 복사, 붙여넣기로 최상단의 행을 복제한다.
* **Vr-**: 복제한 행에서 모든 문자를 대시(-) 문자로 치환한다.

## Tip.25 문서의 열 변경하기

`visual-mode/sprite.css`

비주얼 블록 모드를 사용하면 동시에 여러 행에 내용을 추가하는 것도 가능하다.

images 텍스트를 components로 변경하기

* **\<C-v\>jje**: 범위 선택, 비주얼 모드
* **c**: 모든 영역의 본문이 제거되고 끼워넣기 모드로 전환
* **components**: components 입력, 가장 상단의 행에서만 입력한 내용이 나타난다.
* **\<Esc\>**: 일반 모드로 돌아간다. 나머지 두 행에 입력한 내용이 추가된다.

## Tip.26 비주얼 블록을 쪼개서 본문에 붙여넣기

비주얼 블록 모드는 행과 열이 뒤범벅된, 사각의 코드 영역을 조작해야 하는 상황에서 강력한 힘을 발휘한다. 물론 그 외의 경우에서도 충분히 활용할 수 있다.

`the-vim-way/2_foo_bar.js`

* **\<C-v\>jj\$**
  * **\<C-v\>**: 비주얼 블록 모드로 진입
  * **\$**:, 선택 영역을 행의 마지막까지 늘린다. 각 행의 선택 영역을 본문 오른쪽 끝까지, 행의 길이에 맞춰 확장한다.
* **A;**: 영역을 선택한 상황에서 행의 마지막에 글자 ; 를 추가
* **\<Esc\>**: 일반 모드

> *i와 a 명령 사용방법
> i, a 명령은 Vim에서 일반 모드와 끼워넣기 모드를 전환하는 여러 가지 방법 중 하나이다.
> i는 커서의 앞에서부터, a는 커서의 뒤에서부터 내용을 추가할 수 있는 기능.
> I와 A 명령은 i, a와 비슷하게 시작하지만 커서의 시작 위치는 행의 처음 또는 마지막으로 이동한다.
>
> 비주얼 블록 모드에서 끼워넣기 모드로 전환하는 경우에도 I, A 명령은 비슷한 방식으로 동작한다.
>
> i와 a 명령은 비주얼 모드와 동작 대기 모드에서 텍스트 객체를 시작할 때 사용하는 명령이다.
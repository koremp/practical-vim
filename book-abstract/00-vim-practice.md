# Vim을 시작하기 위한 준비운동

## Vim 내장 문서 사용하기

`:h vimtutor`
`:h`
`:help`

## Vim을 책에서 표현하기 위한 표기법

### 선율 연주하기

### 화음 연주하기

### 플레이스 홀더

### 특수키 표시하기

### 중간 명령(midcommand)로 모드 전환하기

### 명령행 모드 사용하기

grep 명령어 실행

`$ grep -n Waldo *`

Vim 내장 :grep 사용

`:grep Waldo *`

### 버퍼에서 커서의 위치 보이기

### 검색에 일치하는 본문 강조하기

### 비주얼 모드에서 본문 선택하기

## 예제 다운로드하기

## Vim을 출하 설정(Factory Settings)으로 사용하기

`$ vim -u None -N`

*-u NONE* 플래그를 사용하면 Vim이 *vimrc* 파일을 사용하지 않고 실행된다.

*-N* 플래그는 nocompatible 설정을 활성화 하는 기능으로 vi 호환모드로 전환되지 않도록 방지한다.

[[essential.vim]] 파일은 Vim 내장 플러그인을 활성화하는 최소 설정만 적용한 파일로, Vim에 내장된 일부 기능은 Vim 스크립트로 구현되어 있는데, 이 기능은 플러그인이 활성화되어 있을 때만 동작하기 때문에 작성했다.

*vimrc* 대신 *essential.vim* 파일을 사용하여 Vim을 구동하려면 다음과 같이 실행하면 된다.

`$ vim -u essential.vim`

### Vim 스크립트의 역할

## Vim 버전

### Vim 8의 새로운 점

### 선택 기능

### GUI를 사용하는 Vim, 터미널에서 사용하는 Vim? 선택은 자유!


# VSCode Git 세팅

> 설정 / Terminal > Integrated > Default Profile: Windows → Git Bash

# Local 실습

```
# 새로운 Git 저장소 초기화
git init
# 파일을 Staging Area에 추가
git add 파일명
# 모든 변경사항 추가
# git add *
# git add .
# 현재 작업 상태 확인
git status
# 파일 추적에서 제외
git rm --cached 파일명
# Staging Area에서 파일 제거
# git reset
git status
# 커밋 생성 시 편집기로 메시지 작성
git commit

# 사용자 정보 설정
# 전역 사용자 이메일 설정
git config --global user.email "메일주소"

# 전역 사용자 이름 설정
git config --global user.name "유저네임"

# 현재 설정 확인
git config --global -l
```

## VI 편집기

> 명령 기반의 텍스트 편집기로 입력 모드와 명령 모드로 구성됨

- ESC: 명령 모드로 전환
- i: 입력 모드로 전환
- :wq: 저장 후 종료 (! 강제 옵션)

```
# 커밋 메시지와 함께 커밋
# 메시지를 인라인으로 작성
git commit -m "커밋 메시지"

# 커밋 로그 확인
# 상세한 커밋 로그 보기
git log

# 간략한 커밋 로그 보기
git log --oneline
```

## Remote 실습

- New Repository > Public > Create Repository
- New Repository > Public > Create Repository

```
#원격 저장소 추가
git remote add origin 원격_저장소_주소
# 원격 저장소 확인
git remote -v
# 원격 저장소 삭제
# git remote remove origin
# 로컬 변경 사항 원격 저장소에 푸시
git push origin master
```

## github.dev

- 브라우저에서 GitHub 레포지토리의 코드를 편집할 수 있는 Visual Studio Code 기반의 편집 환경
- GitHub에서 , 키를 눌러 VSCode 환경에 진입하여 편리하게 편집 가능

```
# 원격 저장소에서 변경 사항 가져오기
git pull origin master
# 원격 저장소 복제
git clone 원격_저장소_주소
```

## .gitignore

[gitignore사이트](https://www.toptal.com/developers/gitignore)

- Git이 무시할 파일을 지정
  - 각 라인은 무시할 파일이나 디렉터리(폴더)를 나타냄
  - \*를 사용하여 와일드카드 매칭 가능
  - 제외 처리는 !를 사용

```
# 예시

*.log
!important.log
*.tmp
```

## 일괄로 하위 git 제거

```
# ls -a 폴더경로 # 특정 경로 아래에 숨긴 파일/폴더 보기
rm -rf */.git
```

# 버전 관리

## 브랜치

### 브랜치(branch)란?

> - 브랜치는 나뭇가지처럼 작업 공간을 독립적으로 나눌 수 있도록 도와주는 Git의 도구

- 각 브랜치는 원본 코드(master 또는 main)와는 별개로 작업을 진행할 수 있으며, 필요에 따라 병합하여 작업 결과를 통합할 수 있음
- 독립적인 작업 공간을 제공하여 안전한 코드 변경이 가능
- 실험적인 작업을 별도로 진행할 수 있음
- 브랜치 간 변경 사항을 손쉽게 병합 가능

## 브랜치 목록 확인

```
$ git branch
```

## 새로운 브랜치 생성

```
$ git branch <브랜치 이름>
```

## 브랜치 이동

```
$ git switch <브랜치 이름>
```

## 브랜치 생성 및 이동

```
$ git switch -c <브랜치 이름>
```

## 브랜치 삭제

```
$ git branch -d <브랜치 이름>
```

## Merge

## 병합(Merge) 종류

### Fast-Forward

- 브랜치 병합 시 단순히 포인터를 최신 커밋으로 이동
- 변경 기록이 간단하지만, 병합 이력이 남지 않음

### 3-Way Merge

- 공통 조상을 기준으로 두 브랜치의 변경 사항을 병합
- 병합 커밋이 생성되며, 명확한 병합 이력을 제공

### Merge Conflict

- 동일한 파일의 동일한 부분을 수정한 경우 충돌 발생
- 수동으로 충돌 해결 후 병합

## 브랜치 병합

```
$ git merge <브랜치 이름>
```

## 병합 충돌 해결 후 커밋

```
$ git add .
$ git commit
```

## Rebase

- Rebase는 한 브랜치의 변경 사항을 다른 브랜치의 기반 위로 옮기는 작업
- 병합과 달리 이력을 깔끔하게 유지할 수 있는 장점이 있음

## Rebase 시작

```
$ git rebase <브랜치 이름>
```

## Rebase 충돌 해결 후 진행

```
$ git add .
$ git rebase --continue
```

## Reset

- Reset은 특정 커밋으로 되돌아가는 작업으로, 이후의 변경 사항은 삭제
- Reset 옵션
  - soft: 변경 사항을 Staging Area에 유지
  - mixed (기본값): 변경 사항을 Working Directory로 이동
  - hard: 변경 사항을 완전히 삭제

## 특정 커밋으로 되돌리기

```
$ git reset --soft <커밋 ID>
$ git reset --mixed <커밋 ID>
$ git reset --hard <커밋 ID>
```

## Revert

- Revert는 특정 커밋을 취소한 내용을 새로운 커밋으로 생성
- 협업 환경에서 안전하게 되돌릴 수 있음

## 특정 커밋 되돌리기

```
$ git revert <커밋 ID>
```

## 유용한 기능들

## Stash

- Stash는 현재 작업 중인 변경 사항을 임시로 저장해 두는 기능

## 변경 사항 저장

```
$ git stash
```

## 저장된 변경 사항 확인

```
$ git stash list
```

## 저장된 변경 사항 복원

```
$ git stash apply
```

## 저장된 변경 사항 삭제

```
$ git stash drop
```

## Cherry-Pick

- Cherry-Pick은 특정 커밋만 선택하여 현재 브랜치에 적용하는 기능

## 특정 커밋 적용

```
$ git cherry-pick <커밋 ID>
```

## Amend

- Amend는 가장 최근 커밋을 수정할 때 사용
- 커밋 메시지 변경이나 누락된 파일 추가에 유용

## 최근 커밋 수정

```
$ git commit --amend
```

---

# 협업

# Feature Branch Workflow

> Git 저장소에서 독립적인 작업 공간을 만들고 병합하는 방식으로, 협업 시 자주 사용

## **과정**

- 원격 저장소를 로컬에 복제

  ```bash
  $ git clone <저장소 URL>
  ```

- 새로운 기능 구현을 위해 독립적인 브랜치를 생성

  ```
  $ git branch <브랜치 이름>
  $ git switch <브랜치 이름>
  ```

- 브랜치에서 기능을 구현하고 커밋

  ```bash
  $ git add .
  $ git commit -m "<커밋 메시지>"
  ```

- 구현된 브랜치를 원격 저장소에 반영

  ```bash
  $ git push origin <브랜치 이름>
  ```

- GitHub에서 Pull Request를 생성하여 팀원들과 코드 리뷰를 진행
- 리뷰 후 병합 완료된 브랜치를 삭제

  ```bash
  $ git branch -d <브랜치 이름>
  ```

- **장점**
  - 팀원 모두가 능숙하고 프로젝트를 빠르게 진행해야 할 때 적합
  - 독립적인 작업 공간 제공
  - 코드 충돌 방지
  - 명확한 병합 이력 유지

# Forking Workflow

원본 저장소에 대한 접근 권한이 없는 외부 기여자들이 주로 사용하는 협업 방식

## **과정**

- 원본 저장소를 개인 GitHub 계정으로 Fork
- Fork된 저장소를 로컬로 복제

  ```bash
  $ git clone <Fork된 저장소 URL>
  ```

- 원본 저장소를 upstream으로 추가

  ```bash
  $ git remote add upstream <원본 저장소 URL>
  ```

- 브랜치를 생성하여 기능을 구현

  ```bash
  $ git branch <브랜치 이름>
  $ git switch <브랜치 이름>
  $ git add .
  $ git commit -m "<커밋 메시지>"
  ```

- 브랜치를 Fork된 원격 저장소에 반영

  ```bash
  $ git push origin <브랜치 이름>
  ```

- 원본 저장소에 Pull Request를 생성하여 코드 리뷰를 요청
- 원본 저장소의 변경 사항을 Fork된 저장소로 가져옴

  ```bash
  $ git pull upstream master
  ```

## **장점**

- 초심자가 포함된 팀에서 원본 저장소를 보호하면서 협업할 때 적합
- 외부 기여자와의 협업 용이
- 원본 저장소 보호

# Feature Branch Workflow vs Forking Workflow

- **Feature Branch Workflow**
  - 팀원 모두가 능숙하고 프로젝트를 빠르게 진행해야 할 때 적합
  - 모든 팀원이 같은 원격 저장소에 접근 권한이 있음
  - 빠르고 간단한 협업 방식
  - Pull Request와 코드 리뷰가 용이
- **Forking Workflow**
  - 초심자가 포함된 팀에서 원본 저장소를 보호해야 하는 경우 적합
  - 외부 기여자나 오픈소스 프로젝트에 적합
  - 원본 저장소에 접근 권한이 없는 경우 사용
  - 개인 계정에서 작업 후 원본 저장소로 Pull Request
  - 기여 내용이 원본 저장소와 명확히 분리
- **선택 기준**
  - 팀 프로젝트로 능숙한 팀원들과 빠른 작업 필요: Feature Branch Workflow
  - 초심자가 포함되거나 원본 저장소 보호가 중요: Forking Workflow
  - 저장소 접근 권한 여부에 따라 선택
  - 협업 규모와 기여자 수에 따라 적합한 워크플로우를 사용

# Commit Convention

- 일관된 커밋 메시지 작성은 협업 효율성을 높이고 변경 이력을 명확히 파악하는 데 필수적.

## **형식**

`<타입>(<영역>): <제목>`

`<본문>`

`<Footer>`

## **타입 예시**

- **feat**: 새로운 기능 추가
- **fix**: 버그 수정
- **docs**: 문서 수정
- **style**: 코드 스타일 변경 (공백, 세미콜론 등)
- **refactor**: 코드 리팩토링
- **test**: 테스트 추가
- **chore**: 기타 변경 사항

```
예시

feat(login): 사용자 로그인 기능 추가

- JWT 토큰을 이용한 인증 구현
- 로그인 실패 시 에러 메시지 표시

Closes #42
```

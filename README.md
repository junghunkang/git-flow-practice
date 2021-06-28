# git-flow-practice

<hr>

## Git

* 분산형 버전 관리 시스템, 여러 클라이언트는 각자 로컬 저장소에 중앙 서버의 사본을 가지고 작업
* 소스코드를 주고받을 일 없이 같은 파일을 여러 명이 동시에 작업하는 병렬 개발이 가능



## Git 협업 방법

* 협업의 규모가 커지면 개인 스타일대로 git을 사용하는 것이 아닌 서로 규칙을 정해 사용해야 한다.

* Centralized Workflow

	> master branch하나로 모든 개발이 이루어진다.
	>
	> 단순하지만 충돌이 일어날 확률이 높고 여러 버전을 구별하지 않는다.
	>
	> 서비스 배포 이후 관리가 어려우며 master 브랜치가 더러워진다는 단점이 있다.

* Feature Branch Workflow

	> feature branch를 만들어 개발하고 master에 합치는 방식
	>
	> 서비스 배포 이후 관리가 어려우며 기능을 잘 나누지 못하면 사람 1명당 1개의 브랜치를 만들게 될 확률이 높다.

* Forking Workflow

	>대표 중앙 저장소를 fork하여 자신의 원격 저장소를 만든다.
	>
	>작업은 자신이 만든 원격 저장소에서 진행되고 Pull Request를 통해 merge 요청을 한다.

* Gitflow Workflow

	> 개발자는 develop 브랜치에서 구현하고자 하는 기능에 따라 새로운 feature를 생성하여 기능을 구현한후 develop 브랜치로 pull request
	>
	> release 브랜치에서 수정하고자 하는 버그에 따라 새로운 hotfix를 생성하여 수정후 release 브랜치로 pull request



## Git Flow 브랜치 전략

* 5가지 종류의 브랜치가 존재한다.
* 항상 유지되는 메인 브랜치: master, developer
* 일정 기간 동안만 유지되는 보조 브랜치: feature, release, hotfix
* master: 제품으로 출시될 수 있는 브랜치
* develop: 다음 출시 버전을 개발하는 브랜치
* feature: 다음 출시 버전을 위한 새로운 기능을 개발하는 브랜치, 개발자의 저장소에만 존재
* release: 새로운 버전 출시 버전을 준비하는 브랜치, 출시를 위한 사소한 버그 수정이나 메타 데이터 준비를 허용
* hotfix: 출시 버전에서 발생한 버그를 즉각 대응해야 하는 상황에서 필요



## Git-Flow 전략 흐름

1. 처음에는 master와 develop 브랜치가 존재
2. develop 브랜치에서는 상시로 버그를 수정한 커밋들이 추가된다.
3. 새로운 기능 추가작업이 있는 경우 develop 브랜치에서 feature 브랜치를 생성, feature 브랜치는 언제나 develop 브랜치에서 부터 시작하게 된다.
4. 기능 추가작업이 완료되면 feature 브랜치는 develop 브랜치로 merge
5. develop에 이번 버전에 포함되는 모든 기능이 merge 되었다면 QA를 하기 위해 develop 브랜치에서부터 release 브랜치를 생성
6. QA를 진행하면서 발생한 버그들은 release 브랜치에 수정된다.
7. QA를 통과했다면 release 브랜치를 master와 develop 브랜치로 merge, release를 마무리하면 develop과 master가 같은 상태가 된다.
8. master 브랜치에서 버전 태그를 추가



## Git Confilct

* 서로 다른 브랜치를 머지할 때 같은 파일을 각각 다르게 수정할 경우 충돌이 발생한다
* 충돌은 발생하지 않는 것이 제일 좋다.
* 코드를 기능별로 세분화 한다면 같은 파일을 수정하지 않는 방법이 있다.
* 충돌은 깃만의 문제가 아닌 프로젝트 구조를 재 구성해야 할지 생각해보아야 한다.



## Pull-Request

* Merge되기 전에 코드 리뷰를 할 수 있다.




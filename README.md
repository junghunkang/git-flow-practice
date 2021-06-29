# git-flow-practice

<hr>

## Git

* 분산형 버전 관리 시스템, 여러 클라이언트는 각자 로컬 저장소에 중앙 서버의 사본을 가지고 작업
* 소스코드를 주고받을 일 없이 같은 파일을 여러 명이 동시에 작업하는 병렬 개발이 가능



## 브랜치 전략

* 협업의 규모가 커지면 개인 스타일대로 git을 사용하는 것이 아닌 서로 규칙을 정해 사용해야 한다.

* 브랜치 전략이 없다면 동료들이 만든 커밋이나 브랜치에 대해서는 알기가 어렵다

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



## GitHub Flow

* master 브랜치와 Pull Request를 활용한 단순한 브랜치 전략

* 제품이 릴리즈되는 최신 버전인 master 브랜치 하나만 존재한다.

	

## GitHub-Flow 프로세스

1. 기능 개발, 버그 픽스 등의 코드 개발이 필요할 경우 브랜치를 생성한다.

	git-flow처럼 브랜치의 체계적인 분류가 없기 때문에 브랜치 이름에 의도를 잘 드러내야한다.

2. 개발 과정중 커밋 메세지도 상세하게 적어준다.

3. 개발이 완료되면 Pull Request를 생성한다.

4. Pull Request에 대한 충분한 리뷰와 토의를 거친다.

5.  리뷰가 끝나면 실제 서버에 배포한다.



## GitHub-Flow 장점

* 브랜치 전략이 단순하여 git을 처음 접하는 사람에게도 유용하다.
* CI(지속적인 통합), CD(지속적인 배포)가 자연스럽게 이루어진다.



## Git Flow

* 5가지 종류의 브랜치를 이용해 운영하는 전략

* 메인 브랜치: 프로젝트 진행동안 항상 유지되는 

	* master: 제품으로 출시될 수 있는 브랜치

	* developer:  다음 출시 버전을 개발하는 브랜치

* 보조 브랜치: merge되면 사라지는 브랜치

* feature: 다음 출시 버전을 위한 새로운 기능을 개발하는 브랜치, 개발자의 저장소에만 존재

* release: 새로운 버전 출시 버전을 준비하는 브랜치, 출시를 위한 사소한 버그 수정이나 메타 데이터 준비를 허용

* hotfix: 출시 버전에서 발생한 버그를 즉각 대응해야 하는 상황에서 필요



## Git-Flow 개발 프로세스

1. 처음에는 master와 develop 브랜치가 존재, develop 브랜치는 master 브랜치에서 생성되었다.

2. 개발자는 develop 브랜치로부터 본인이 개발할 기능을 위한 feature 브랜치를 만든다.

3. feature 브랜치에서 기능을 만들다가 기능이 완성되면 develop 브랜치에 merge

4. 이번 배포 버전의 기능을 develop 브랜치에 모두 merge 되었다면 QA를 위해 release 브랜치를 생성

5. release 브랜치에서 QA 도중 오류가 발생하면 release 브랜치 내에서 수정을 한다.

	QA가 끝났다면 master와 develop 브랜치에 merge

6. master에서 버그가 발생하면 hotfix 브랜치를 만든다.

	hotfix 브랜치에서 버그 픽스가 끝났다면 develop과 master 브랜치에 각각 merge한다.



## Git-Flow 장점

* master 브랜치에서 버전에 따라 관리할 수 있기 때문에 주기적으로 배포하는 서비스에 적합
* 가장 유명한 전략인 만큼 많은 IDE가 지원한다.



## Git-Flow vs Git-Hub Flow

1. 한달이상의 긴 호흡으로 개발하여 주기적 배포, QA 및 hotfix를 수행할 수 있는 팀이면 git-flow가 적합
2. 항상 릴리즈되어야 할 필요가 있는 서비스와 지속적으로 테스트하고 배포하는 팀이면 github-flow와 같은 간단한 work-flow가 적합



## Git Confilct

* 서로 다른 브랜치를 머지할 때 같은 파일을 각각 다르게 수정할 경우 충돌이 발생한다
* 충돌은 발생하지 않는 것이 제일 좋다.
* 코드를 기능별로 세분화 한다면 같은 파일을 수정하지 않는 방법이 있다.
* 충돌은 깃만의 문제가 아닌 프로젝트 구조를 재 구성해야 할지 생각해보아야 한다.



## Pull-Request

* Merge되기 전에 코드 리뷰를 할 수 있다.




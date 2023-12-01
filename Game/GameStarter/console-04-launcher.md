## Game > GameStarter > 콘솔 사용 가이드 > 런처

[시작하기](./console-01-getting-started)에서 설명하였듯이 런처를 사용하려면 인스톨러와 게임을 준비가 완료되어야 합니다.
아직 인스톨러와 게임 설정 및 바이너리를 준비하지 않았으면 먼저 진행해주세요.

## Launcher

런처 설정 방법과 런처를 배포하는 방법에 대해서 설명합니다.

### 1. 런처 설정 목록
![launcher_list](https://static.toastoven.net/prod_gamestarter/console/gamestarter_launcher_list_202311.png)

런처 목록에서는 등록된 런처 설정들을 조회할 수 있습니다.
또한 새로운 런처를 등록하거나 삭제할 수 있으며, 기존의 런처 설정을 복사할 수도 있습니다.

런처 목록의 조회 결과에는 아래와 같은 필드를 가지고 있습니다.

#### 1) 런처 설정 이름
런처 설정 등록할 때 입력한 이름이 표시됩니다.

#### 2) 등록 일시
런처 설정을 등록하거나 마지막으로 수정한 날짜가 표시됩니다.

#### 3) 등록자
런처 설정을 최초 등록하거나 마지막으로 수정한 사용자의 마스킹 된 이메일 주소가 표시됩니다.

#### 4) 메모
런처 설정을 등록할 때 사용자가 구분하기 위해서 입력한 메모가 표시됩니다.

#### 5) 삭제
등록된 런처 설정을 삭제할 수 있습니다.
런처 설정을 삭제하더라도 이미 배포된 런처 설정이 삭제되지 않습니다.


### 2. 런처 설정 등록
새로운 런처 설정 등록은 왼쪽 위의 [+등록]으로 등록할 수 있습니다.

#### 2-1. 기본 정보
![launcher_register_01](https://static.toastoven.net/prod_gamestarter/console/gamestarter_launcher_register_01_202311.png)

##### 1) 런처 설정 이름
런처 설정 이름은 다른 런처 설정과 구분하기 위해서 사용합니다.
따라서 런처 설정 이름은 중복으로 등록할 수 없습니다.
또한 한글, 영문 대소문자, 숫자, 띄어쓰기를 포함하여 2 ~ 20자까지 입력 가능합니다.

##### 2) 메모
메모는 런처 설정의 내용을 참고하기 위해서 입력하는 정보입니다.

모든 설정을 완료하였으면 하단의 [다음] 버튼으로 다음 페이지로 이동합니다.

#### 2-2. 런처 UI
![launcher_register_02](https://static.toastoven.net/prod_gamestarter/console/gamestarter_launcher_register_02_202311.png)

런처 UI에서는 런처 상단 메뉴에 표시되는 브랜드 아이콘과 게임 순서를 지정할 수 있습니다.

##### 1) 브랜드 아이콘
브랜드 아이콘으로 사용할 이미지를 업로드합니다.
브랜드 아이콘 영역의 왼쪽 위의 [수정] 아이콘으로 이미지를 업로드할 수 있습니다.

![launcher_register_02_brandicon](https://static.toastoven.net/prod_gamestarter/console/gamestarter_launcher_register_02_brandicon_202311.png)

###### 1-1) 이미지 업로드
새로운 브랜드 아이콘 이미지를 업로드합니다.
브랜드 아이콘 이미지 파일은 JPG, JPEG, PNG 확장자만 업로드할 수 있습니다.
브랜드 아이콘 이미지의 권장 크기는 256x256입니다.

이미지 업로드가 완료되고 [확인]을 누르면 런처 UI에 반영된 모습을 확인할 수 있습니다.

###### 1-2) 삭제
이미 등록된 브랜드 아이콘을 삭제하고 싶을 때는 [삭제] 버튼으로 삭제할 수 있습니다.

##### 2) 게임
새로운 게임을 등록하려면 게임 추가 영역의 [추가] 아이콘으로 추가할 수 있습니다.

![launcher_register_02_games](https://static.toastoven.net/prod_gamestarter/console/gamestarter_launcher_register_02_games_202311.png)

게임 등록 팝업에서 등록된 게임의 목록이 표시됩니다.
선택하는 게임 순서대로 런처에 게임이 표시되는 것을 확인할 수 있습니다.
아래의 예시는 `Game1`, `Game2`, `Game3`을 순서대로 추가하였습니다.

![launcher_register_02_complete](https://static.toastoven.net/prod_gamestarter/console/gamestarter_launcher_register_02_complete_202311.png)

등록한 게임을 삭제하려면 게임 영역의 왼쪽 아래의 [삭제] 아이콘을 통해서 삭제할 수 있습니다.

모든 런처 UI를 설정하였으면 하단의 [다음] 버튼으로 다음 페이지로 이동합니다.

##### 3) 자동 실행
![launcher_register_03](https://static.toastoven.net/prod_gamestarter/console/gamestarter_launcher_register_03_202311.png)

자동 실행은 런처 UI에 등록한 게임이 1개일 경우에만 사용 가능한 설정입니다.
앞선 예시에서 게임을 3개 선택했기 때문에 선택할 수 없는 상태입니다.
만약에 게임 1개만 사용하시면 자동 실행의 기능을 사용할 수 있습니다.

###### 3-1) 자동 시작
자동 시작은 런처가 실행되면 자동으로 게임까지 실행할 수 있습니다.

###### 3-2) 자동 업데이트
자동 업데이트는 런처가 실행되면 업데이트할 게임이 있으면 바로 업데이트를 실행할 수 있습니다.

모든 자동 실행 설정을 완료하였으면 [등록] 버튼으로 런처 설정을 등록할 수 있습니다.

### 3. 런처 설정 상세보기
![launcher_detail](https://static.toastoven.net/prod_gamestarter/console/gamestarter_launcher_detail_202311.png)

런처 설정 상세정보를 보려면 빨간색 영역의 런처를 클릭하면 상세보기 페이지로 이동합니다.

![launcher_modify_01](https://static.toastoven.net/prod_gamestarter/console/gamestarter_launcher_modify_01_202311.png)

런처 설정 상세보기에서 런처 설정을 수정하거나 복사할 수 있습니다.
왼쪽 위의 [수정] 버튼으로 수정할 수 있습니다.
왼쪽 위의 [복사] 버튼으로 복사할 수 있습니다.

#### 1) 런처 설정 수정
![launcher_modify_02](https://static.toastoven.net/prod_gamestarter/console/gamestarter_launcher_modify_02_202311.png)

[수정] 버튼을 누르면 런처 설정 수정 페이지로 변경됩니다.
런처 설정 수정이 완료되었으면 마지막 단계에서 [저장]을 통해서 수정사항을 반영할 수 있습니다.

##### 2) 런처 설정 복사
![launcher_copy](https://static.toastoven.net/prod_gamestarter/console/gamestarter_launcher_copy_202311.png)

[복사] 버튼을 누르면 복사 팝업창이 등장합니다.
런처 설정 복사는 런처 설정 이름과 메모를 제외한 다른 설정을 복사합니다.

###### 2-1) 런처 설정 이름
복사할 런처 설정의 런처 설정 이름을 입력해주세요.
런처 설정 등록과 동일하게 중복된 이름을 사용할 수 없습니다.

###### 2-2) 메모
복사할 런처 설정을 구분할 수 있는 내용을 메모에 작성해주세요.

### 4. 런처 배포
![launcher_deploy_01_list](https://static.toastoven.net/prod_gamestarter/console/gamestarter_launcher_deploy_01_list_202311.png)
런처 배포 페이지에는 배포존별로 배포를 할 수 있도록 구분되어 있습니다.
기본적으로 제공되는 배포존은 SERVICE, DEVELOP, TEST 배포존이 있습니다.
배포존별로 각각 런처 설정을 배포할 수 있습니다.

초기에는 런처 설정이 등록되어 있지 않아서 배포 실행의 [배포] 버튼이 비활성화되어 있습니다.

런처 실행의 필드는 아래와 같이 구성되어 있습니다.
#### 1) 런처 설정 이름
현재 배포된 런처 설정의 이름이 표시됩니다.

#### 2) 게임 목록
헌재 배포된 런처 설정의 게임 목록이 순서대로 표시됩니다.

#### 3) 배포 일시
마지막으로 배포된 배포 날짜가 표시됩니다.

#### 4) 배포자
마지막으로 배포된 배포자의 마스킹 된 이메일 주소가 표시됩니다.

#### 5) 배포 상태
조회할 당시의 배포 상태를 표시합니다.

> [참고] 배포 상태 종류
>
> - `배포 중`: 배포를 진행 중인 상태를 나타냅니다.
> - `배포 완료`: 배포가 완료된 상태를 나타냅니다.
> - `배포 예약`: 배포 예약이 등록된 상태를 나타냅니다.
> - `배포 예약 취소`: 예약된 배포가 취소된 상태를 나타냅니다.
> - `배포 실패`: 배포 과정에 문제가 발생하여 실패한 상태를 나타냅니다.

#### 6) 배포 실행
예시로 TEST 배포존에 등록된 런처 설정을 배포해보도록 하겠습니다.

TEST 배포존의 [배포] 버튼을 누르면 아래와 같은 배포 팝업창이 등장합니다.

![launcher_deploy_02](https://static.toastoven.net/prod_gamestarter/console/gamestarter_launcher_deploy_02_202311.png)

런처를 배포하는 방식에는 2가지가 있습니다.
- 예약 배포
- 즉시 배포

##### 6-1) 런처 설정
배포하려는 런처 설정을 선택합니다.
런처 설정을 선택하면 아래의 화면에 등록했던 브랜드 아이콘과 게임들이 순서대로 표시됩니다.

##### 6-2) 예약 배포
런처 설정을 특정 시간에 배포하려면 [예약 배포] 버튼으로 예약할 수 있습니다.

![launcher_deploy_02_reserve](https://static.toastoven.net/prod_gamestarter/console/gamestarter_launcher_deploy_02_reserve_202311.png)

배포 예약을 하려는 기준 시간과 배포 시간을 선택하고 [확인]을 클릭하면 배포 예약 시간을 등록할 수 있습니다.
마지막 단계인 [6-4] 단계에서 모든 확인을 한 후에 [배포] 버튼을 누르면 배포 예약이 등록됩니다.

##### 6-3) 즉시 배포
런처를 즉시 배포를 진행합니다.
즉시 배포에는 별도로 설정할 필요가 없으므로 마지막 단계인 [6-4] 단계로 이동합니다.

##### 6-4) 배포 비교
즉시 배포나 예약 배포의 설정이 완료되면 마지막 단계로 마지막에 배포한 정보와 비교하는 팝업창이 등장합니다.

###### 6-4-1) 배표 비교: 런처 설정
![launcher_deploy_02_diff_config](https://static.toastoven.net/prod_gamestarter/console/gamestarter_launcher_deploy_02_diff_config_202311.png)

###### 6-4-2) 배표 비교: 런처 UI
![launcher_deploy_02_diff_ui](https://static.toastoven.net/prod_gamestarter/console/gamestarter_launcher_deploy_02_diff_ui_202311.png)

새롭게 배포하려는 런처 설정이 맞는지 모두 확인되면 [배포] 버튼을 통해서 즉시 배포나 예약 배포를 실행할 수 있습니다.

[배포] 버튼으로 배포 팝업창이 닫히면서 배포존에 배포 상태에 변경된 것을 확인할 수 있습니다.
![launcher_deploy_03](https://static.toastoven.net/prod_gamestarter/console/gamestarter_launcher_deploy_03_202311.png)

#### 7) 실행 템플릿
실행 템플릿은 웹 브라우저에서 런처를 실행하거나 인스톨러를 다운로드할 수 있는 자바스크립트를 제공합니다.
해당 배포존에 런처가 이미 설치되어 있으면 런처를 실행하게 됩니다.
만약 런처가 설치가 되어 있지 않으면 인스톨러 다운로드를 실행하게 됩니다.

[복사] 버튼을 통해서 자바스크립트 코드를 복사할 수 있습니다.

#### 8) 런처 실행
배포존에 런처가 배포가 완료되면 런처를 실행할 수 있게 됩니다.

[런처 실행] 버튼을 통해서 배포존의 런처를 실행할 수 있습니다.
위의 동작은 사용자 PC에 런처 설치 여부에 따라서 2가지로 수행됩니다.

##### 8-1) 런처를 이미 설치한 경우
![launcher_execute_urlscheme](https://static.toastoven.net/prod_gamestarter/console/gamestarter_launcher_execute_urlscheme_202311.png)
런처를 설치한 경우 브라우저에서 실행 팝업창이 등장합니다.
여기서 [GameStarter 열기] 버튼을 통해서 런처를 실행할 수 있습니다.

##### 8-2) 런처를 설치하지 않은 경우
![launcher_execute_download](https://static.toastoven.net/prod_gamestarter/console/gamestarter_launcher_execute_download_202311.png)
런처를 설치하지 않은 경우 브라우저에서 인스톨러 다운로드 팝업창이 등장합니다.
[확인] 버튼을 통해서 인스톨러를 다운로드 받을 수 있습니다.

##### 8-3) 런처가 실행된 화면
인스톨러를 통해 런처를 설치한 이후에 런처를 실행하면 아래와 같이 런처가 실행된 모습을 확인할 수 있습니다.

![launcher_final](https://static.toastoven.net/prod_gamestarter/console/gamestarter_launcher_final_202311.png)



### 5. 배포 이력
![launcher_history_01](https://static.toastoven.net/prod_gamestarter/console/gamestarter_launcher_history_01_202311.png)

런처가 배포된 이력을 배포 이력 페이지에서 조회할 수 있습니다.

배포 이력 조회 순서는 다음과 같습니다.
1. 조회하고자 하는 배포존을 선택합니다.
2. 검색 조건을 설정하여 필터링합니다. 검색 조건에는 총 3가지 있습니다.
    1) `런처 설정 이름`: 런처 설정 이름으로 필터링할 수 있습니다.
    2) `런처 배포 일시`: 특정 기간으로 필터링할 수 있습니다.
    3) `배포 상태`: 배포 상태로 필터링할 수 있습니다.


![launcher_history_02](https://static.toastoven.net/prod_gamestarter/console/gamestarter_launcher_history_02_202311.png)

배포 이력 조회의 결과에서는 다음과 같은 필드가 있습니다.

1. `런처 설정 이름`: 배포된 런처의 설정 이름을 나타냅니다.
2. `게임 목록`: 배포된 런처에 설정되었던 게임을 나타냅니다.
3. `배포 상태`: 배포된 런처의 배포 상태를 나타냅니다.
    - 배포 중
    - 배포 완료
    - 배포 예약
    - 배포 예약 취소
    - 배포 실패
4. `배포 일시`: 런처가 배포된 날짜를 나타냅니다.
5. `배포자`: 런처를 배포한 사용자의 마스킹 된 이메일 주소를 나타냅니다.
6. `메모`: 배포된 런처의 메모를 나타냅니다.

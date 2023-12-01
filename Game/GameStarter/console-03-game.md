## Game > GameStarter > 콘솔 사용 가이드 > 게임

## Game

게임을 등록하고 게임의 설정과 바이너리를 배포하는 방법에 대해서 설명합니다.

### 1. 게임 목록
![game_list](https://static.toastoven.net/prod_gamestarter/console/gamestarter_game_list_202311.png)

게임 목록에서는 새로운 게임을 등록하거나 등록된 게임들을 조회할 수 있습니다.
또한 게임 이름이나 게임 사용 여부를 통해서 필터링할 수 있습니다.

게임 목록의 조회 결과에는 아래와 같은 필드를 가지고 있습니다.

#### 1) 게임 이름
등록된 게임의 고유한 이름을 나타냅니다.

#### 2) 등록 일시
게임을 등록한 날짜를 나타냅니다.

#### 3) 등록자
게임을 등록한 사용자의 마스킹 된 이메일 주소를 나타냅니다.

#### 4) 게임 사용 여부
게임의 사용 여부(사용 혹은 사용 안 함)를 나타냅니다.

#### 5) 상세보기
[상세] 버튼을 통해서 등록된 게임의 상세한 정보를 확인할 수 있습니다.


### 2. 게임 등록

게임 목록의 왼쪽 위의 [+등록]을 통하여 새로운 게임을 등록할 수 있습니다.

![game_register](https://static.toastoven.net/prod_gamestarter/console/gamestarter_game_register_202311.png)

#### 1) 게임 이름
게임 이름은 다른 게임과 구분할 수 있도록 중복되지 않는 고유한 명칭을 가져야 합니다.
게임 이름은 한글, 영문 대소문자, 숫자로 2~15자까지 입력할 수 있습니다.

게임 이름 입력을 완료하였으면 [등록] 버튼을 통해서 게임을 등록할 수 있습니다.

### 3. 게임 상세보기

게임 목록에서 [상세] 버튼을 눌러서 게임의 상세보기 페이지로 이동하게 됩니다.

![game_detail](https://static.toastoven.net/prod_gamestarter/console/gamestarter_game_detail_202311.png)

### 4. 게임 수정

게임 상세보기 페이지의 상단의 [수정] 버튼으로 수정 상태로 진입할 수 있습니다.

![game_modify](https://static.toastoven.net/prod_gamestarter/console/gamestarter_game_modify_202311.png)

#### 1) 게임 사용 여부
게임을 사용하지 않는 경우 사용 안 함으로 변경할 수 있습니다.


### 5. 게임 진입

![game_enter](https://static.toastoven.net/prod_gamestarter/console/gamestarter_game_enter_202311.png)

게임을 등록 완료하면 게임 목록에 게임들이 조회됩니다.
상단의 빨간색 영역을 클릭하면 게임으로 진입할 수 있습니다.

게임을 진입하면 게임 설정과 게임 바이너리 배포를 할 수 있습니다.

#### 5-1. 게임 설정 목록

게임을 진입하면 다음과 같이 상단에 게임 이름이 표시되고 하단에 선택한 게임의 메뉴들이 표시됩니다.

![game_config_list](https://static.toastoven.net/prod_gamestarter/console/gamestarter_game_config_list_202311.png)

게임 설정은 게임을 설치할 때 필요한 여러 설정을 등록할 수 있습니다.

게임 설정 조회 결과 페이지에는 다음과 같은 필드가 있습니다.
1. `게임 설정 이름`: 등록된 게임 설정의 이름을 나타냅니다.
2. `수정 일시`: 등록된 게임 설정이 마지막으로 수정된 날짜를 나타냅니다.
3. `등록자`: 등록된 게임 설정을 마지막 수정한 등록자의 마스킹 된 이메일 주소를 나타냅니다.
4. `메모`: 등록된 게임의 메모를 나타냅니다.
5. `삭제`: 등록된 게임을 삭제합니다.


#### 5-2. 게임 설정 등록

새로운 게임 설정 등록은 게임 설정 목록의 우측의 [+등록] 버튼을 통해서 등록할 수 있습니다.


##### 5-2-1. 기본 설정
![game_config_register_01](https://static.toastoven.net/prod_gamestarter/console/gamestarter_game_config_register_01_202311.png)

###### 1) 게임 설정 이름
게임 설정의 이름은 다른 게임 설정과 구분하기 위해서 입력합니다.
선택한 게임 안에서 중복된 게임 이름은 사용할 수 없습니다.
게임 설정의 이름은 한글, 영문 대소문자, 숫자로 2 ~ 15자까지 입력 가능합니다.

###### 2) 메모
메모는 게임 설정의 내용을 참고하기 위해서 입력하는 정보입니다.

###### 3) 관리자 권한 획득
해당 게임을 설치할 때 Windows의 관리자 권한 획득 여부에 대해서 선택합니다.
이 기능을 활성화하면 사용자가 게임을 설치하는 과정에서 UAC(User Access Control)가 등장할 수도 있습니다.

###### 4) 기본 설치 경로
게임을 설치할 때 기본으로 설치할 경로를 지정합니다.
기본 경로는 Windows는 `<SystemDrive>/ProgramData/<GameName>`입니다.
다른 경로로 설정하려면 [사용자 지정 경로]를 선택하고 원하는 경로를 입력해주시면 됩니다.

###### 5) 설정된 기본 설치 경로
기본 설치 경로에 따라서 기본 설치 경로를 예시로 보여줍니다.
Windows는 `<SystemDrive>`를 `C 드라이브`를 예시로 기본 설치 경로를 표시합니다.


모든 설정을 완료하였으면 하단의 [다음] 버튼으로 다음 페이지로 이동합니다.

##### 5-2-2. 게임 바로 가기 아이콘
![game_config_register_02](https://static.toastoven.net/prod_gamestarter/console/gamestarter_game_config_register_02_202311.png)

게임 설치를 하면서 바탕화면에 바로 가기 아이콘을 설치할 수 있습니다.
이때에 필요한 게임 아이콘 이미지와 이름이 필요합니다.

###### 1) 바로 가기 아이콘 이미지
바탕화면에 설치될 때 사용할 게임의 바로 가기 아이콘 이미지를 등록합니다.
아이콘 이미지의 권장 크기는 256x256입니다.

###### 2) 바로 가기 아이콘 이름
바탕화면에 설치될 게임 바로 가기 아이콘의 이름을 입력합니다.
게임 바로 가기 아이콘의 이름은 2 ~ 50자까지 입력 가능합니다.
또한 첫 번째와 마지막 문자에 `공백`, `/`, `/`는 입력할 수 없습니다.


모든 설정을 완료하였으면 하단의 [다음] 버튼으로 다음 페이지로 이동합니다.

##### 5-2-3. 게임 UI
![game_config_register_03](https://static.toastoven.net/prod_gamestarter/console/gamestarter_game_config_register_03_202311.png)

게임 UI는 런처에서 게임별로 보이는 게임 UI를 구성할 수 있습니다.
게임의 아이콘, 배경 이미지, 하단 부분에 이용 약관이나 고객센터 URL 등을 추가하거나 삭제할 수 있습니다.

> [참고] 게임 UI 편집기 사용방법
>
> 각각의 영역에 이동, 크기조절, 편집, 삭제 아이콘을 통해서 위치 이동이나 속성을 수정할 수 있습니다.
> ![game_config_register_03_usage](https://static.toastoven.net/prod_gamestarter/console/gamestarter_game_config_register_03_usage.gif)

###### 1) 게임 아이콘
![game_config_register_03-1](https://static.toastoven.net/prod_gamestarter/console/gamestarter_game_config_register_03-1_202311.png)

게임 아이콘 영역의 [편집] 아이콘으로 새로운 게임 아이콘을 등록하거나 삭제할 수 있습니다.
게임 아이콘 이미지의 권장 크기는 256x256입니다.

###### 2) 배경 이미지
![game_config_register_03-2](https://static.toastoven.net/prod_gamestarter/console/gamestarter_game_config_register_03-2_202311.png)

배경 이미지 영역의 [편집] 아이콘으로 새로운 배경 이미지를 등록할 수 있습니다.
배경 이미지의 최소 크기는 992x584입니다.

###### 3) 이용약관
![game_config_register_03-3](https://static.toastoven.net/prod_gamestarter/console/gamestarter_game_config_register_03-3_202311.png)

게임 UI의 Footer 영역의 이용약관이나 고객센터를 추가하거나 제거할 수 있습니다.

위의 예시 이미지에는 이용약관의 [편집] 아이콘을 통해서 이용약관을 클릭했을 때 연결되는 URL을 입력하는 화면입니다.
또한 이용약관의 이름을 다른 이름으로도 변경할 수 있습니다.


##### 5-2-4. 미리 보기

###### 1) UI 미리 보기
우측의 [UI 미리 보기] 버튼을 통해서 실제 런처에서 보이는 게임 UI를 확인할 수 있습니다.

![game_config_register_04](https://static.toastoven.net/prod_gamestarter/console/gamestarter_game_config_register_04_202311.png)

모든 게임 설정을 완료하였으면 하단의 [저장] 버튼으로 게임 설정을 등록할 수 있습니다.

#### 5-3. 게임 설정 상세보기
![game_config_register_complete](https://static.toastoven.net/prod_gamestarter/console/gamestarter_game_config_register_complete_202311.png)

게임 설정 목록에서 빨간색 영역을 클릭하면 게임 설정 상세보기 페이지로 이동하게 됩니다.

![game_config_detail](https://static.toastoven.net/prod_gamestarter/console/gamestarter_game_config_detail_202311.png)

게임 설정 상세보기 페이지는 게임 설정 등록 페이지와 같지만 입력헐 수 없다는 차이점이 있습니다.
왼쪽 위의 [수정]과 [복사] 버튼을 통해서 수정하거나 복사를 할 수 있습니다.

##### 1) 게임 설정 수정

게임 설정 목록의 왼쪽 위의 [수정] 버튼을 통해서 게임 설정 수정을 할 수 있습니다.

![game_config_modify](https://static.toastoven.net/prod_gamestarter/console/gamestarter_game_config_modify_202311.png)

수정하고자 하는 설정을 수정하고 게임 설정 마지막 페이지의 [저장] 버튼을 통해서 수정할 수 있습니다.

##### 2) 게임 설정 복사

게임 설정 목록의 왼쪽 위의 [복사] 버튼을 통해서 게임 설정 복사를 할 수 있습니다.

![game_config_copy](https://static.toastoven.net/prod_gamestarter/console/gamestarter_game_config_copy_202311.png)

게임 설정 복사 팝업창이 등장하며 게임 설정 이름과 메모를 입력한 후에 복사할 수 있습니다.


지금까지 게임 설정 등록/상세보기/수정/복사에 대해서 설명하였습니다.
단순히 게임 설정을 등록만 하였기 때문에 실제로 런처에는 반영이 되지 않았습니다.
게임 바이너리 업로드에 대해서 먼저 설명한 후에 게임 배포에 대해서 설명을 이어가도록 하겠습니다.


#### 5-4. 게임 바이너리
![game_binary_list](https://static.toastoven.net/prod_gamestarter/console/gamestarter_game_binary_list_202311.png)

게임 바이너리는 게임 실행에 필요한 바이너리 파일들의 집합을 의미합니다.
게임 바이너리 업로드를 하려면 우선 CDN 연동을 진행해야 합니다.

##### 1) CDN 연동
CDN 연동을 하려면 [연동] 버튼을 통해서 진행할 수 있습니다.
먼저 연동하고자 하는 배포존에 CDN 연동을 선택합니다.

예시에서는 TEST 배포존에 CDN 연동을 진행합니다.

CDN 연동 방식은 2가지가 제공됩니다.
###### 1-1) GameStarter CDN
![game_binary_cdn_default](https://static.toastoven.net/prod_gamestarter/console/gamestarter_game_binary_cdn_default_202311.png)

GameStarter에서 제공하는 CDN을 사용합니다.
GameStarter CDN은 자동으로 CDN 생성 작업을 진행하기 때문에 특별하게 설정해야 할 정보가 없습니다.
이 과정에서는 CDN을 새롭게 생성하기 때문에 작업 완료까지 다소 시간이 많이 소요됩니다.

###### 1-2) 고객사 CDN
![game_binary_cdn_customer](https://static.toastoven.net/prod_gamestarter/console/gamestarter_game_binary_cdn_customer_202311.png)

GameStarter에서 제공하는 CDN을 사용하지 않고 고객사 자체 CDN 주소로 연동합니다.
이 과정에서는 2단계의 설정 작업이 필요합니다.

1. GameStarter 파일 스토리지 주소를 고객사 자체 CDN의 원본 서버 URL로 등록합니다.
2. 고객사 자체 CDN의 주소를 입력합니다.

##### 2) CDN 상태
CDN 연동을 진행하면 다소 시간이 소요됩니다.
CDN 연동 작업이 완료되면 다음과 같이 [정상]으로 상태가 변경됩니다.

![game_binary_cdn_complete](https://static.toastoven.net/prod_gamestarter/console/gamestarter_game_binary_cdn_complete_202311.png)

CDN 상태가 [정상]이 되면 게임 바이너리를 업로드를 진행할 수 있습니다.
CDN 상태가 [정상]이 아니라면 작업이 완료될 때까지 대기해주시기 바랍니다.

#### 5-5. 게임 바이너리 상세보기
![game_binary_cdn_enter](https://static.toastoven.net/prod_gamestarter/console/gamestarter_game_binary_cdn_enter_202311.png)

게임 바이너리의 상세보기는 빨간색 영역을 클릭하면 상세보기 페이지로 이동합니다.

![game_binary_cdn_detail](https://static.toastoven.net/prod_gamestarter/console/gamestarter_game_binary_cdn_detail_202311.png)

게임 바이너리 상세보기에는 다음과 같은 필드가 있습니다.

##### 1) 배포존
게임 바이너리가 속한 배포존 이름이 나타납니다.

##### 2) CDN 서버
게임 바이너리의 CDN 연동 정보가 표시됩니다.
CDN 연동을 GameStarter CDN으로 진행했으면 `GameStarter CDN`이 표시되며,
CDN 연동을 고객사 자체 CDN으로 진행했으면 `고객사 CDN`으로 표시됩니다.

##### 3) CDN 상태
CDN 연동의 진행 상태를 표시합니다.

> [참고] CDN 상태
>
> - `정상`: 정상적으로 CDN 연동이 완료되었을 나타냅니다.
> - `작업 중`: CDN 연동이 진행 중임을 나타냅니다.
> - `생성 실패`: CDN 연동이 실패하였음을 나타냅니다.

##### 4) 배포 상태
현재 게임 바이너리가 CDN까지 정상적으로 배포되었는지를 나타냅니다.

##### 5) 게임 바이너리 업로드 정보
업로드한 게임 바이너리의 정보를 표시합니다.
게임 바이너리 정보에는 파일의 개수와 파일 크기가 제공됩니다.

##### 6) 게임 바이너리 업로드 일시
업로드한 게임 바이너리의 날짜를 나타냅니다.

##### 7) 업로드 상태
게임 바이너리의 업로드 진행 상황을 나타냅니다.

> [참고] 업로드 상태
>
> - `업로드 대기`: 게임 바이너리의 필요한 메타파일 생성 등의 준비 작업을 진행 중임을 나타냅니다.
> - `업로드 중`: 게임 바이너리 업로드가 진행 중인 상태임을 나타냅니다.
> - `업로드 성공`: 게임 바이너리 업로드 절차가 모두 완료하였음을 나타냅니다.
> - `업로드 실패`: 게임 바이너리 업로드 중 오류가 발생하였음을 나타냅니다.

##### 8) 게임 실행파일 이름
업로드한 게임 바이너리 파일 중 게임 실행 파일의 이름을 나타냅니다.


#### 5-6. 게임 바이너리 업로드

CDN 연동이 완료된 이후에 게임 바이너리 파일들을 업로드할 수 있습니다.
게임 바이너리 파일을 업로드를 완료하였다고 해서 실제 런처로 즉시 반영되지 않습니다.
업로드가 완료된 게임 바이너리를 반영하려면 게임 설정과 마찬가지로 게임 배포의 게임 바이너리 배포를 통해서 적용할 수 있습니다.

먼저 실습으로 TEST 배포존에서 게임 바이너리 업로드를 진행합니다.

![game_binary_upload_01](https://static.toastoven.net/prod_gamestarter/console/gamestarter_game_binary_upload_01_202311.png)
TEST 배포존의 업로드 실행의 [바이너리 업로드] 버튼을 통해서 파일 업로드를 진행합니다.

![game_binary_upload_02](https://static.toastoven.net/prod_gamestarter/console/gamestarter_game_binary_upload_02_202311.png)

업로드하고자 하는 게임 바이너리의 폴더를 선택해주세요.

![game_binary_upload_03](https://static.toastoven.net/prod_gamestarter/console/gamestarter_game_binary_upload_03_202311.png)

파일 업로드가 진행됩니다.

![game_binary_upload_04](https://static.toastoven.net/prod_gamestarter/console/gamestarter_game_binary_upload_04_202311.png)

파일 업로드가 완료되면 게임 실행 파일 정보를 선택해야 합니다.
입력창에는 업로드한 바이너리의 파일들이 리스트로 표시됩니다.
이 중에 게임을 실행하는 파일을 선택해주시면 됩니다.

![game_binary_upload_05](https://static.toastoven.net/prod_gamestarter/console/gamestarter_game_binary_upload_05_202311.png)

게임 실행 파일을 선택하고 나면 업로드 된 정보가 표시됩니다.
여기에는 업로드한 파일 개수와 파일 크기가 표시됩니다.

![game_binary_upload_06](https://static.toastoven.net/prod_gamestarter/console/gamestarter_game_binary_upload_06_202311.png)

파일 업로드 전송이 완료되었지만, 실제 CDN까지의 반영까지 다소 시간이 소요됩니다.
빨간색 영역의 업로드 상태가 [업로드 완료]가 될 때까지 대기해주세요.


![game_binary_upload_complete](https://static.toastoven.net/prod_gamestarter/console/gamestarter_game_binary_upload_complete_202311.png)

업로드가 완료되면 [업로드 완료]로 상태가 변경됩니다.
이제부터 게임 배포를 통해서 게임 바이너리를 배포할 수 있습니다.

지금까지 게임 바이너리 업로드까지의 과정을 설명했습니다.
게임 설정과 마찬가지로 런처에 배포하지 않았기 때문에 아직 실제로 반영이 되지 않았습니다.

다음 섹션에서 게임 설정과 게임 바이너리의 배포에 대해서 설명하도록 하겠습니다.


#### 5-7. 게임 배포
![game_deploy_list](https://static.toastoven.net/prod_gamestarter/console/gamestarter_game_deploy_list_202311.png)

게임 배포는 배포존별로 게임 설정과 게임 바이너리를 배포할 수 있습니다.
빨간색 영역이 하나의 배포존을 의미합니다.
주황색 영역은 배포존의 게임 설정을 새롭게 배포하거나 배포된 정보를 확인할 수 있습니다.
초록색 영역은 배포존의 게임 바이너리를 새롭게 배포하거나 배포된 정보를 확인할 수 있습니다.

만약에 등록된 게임 설정이 없거나 게임 바이너리가 업로드 완료가 되지 않았다면 [배포] 버튼은 비활성화됩니다.

그러면 TEST 배포존에서 등록했던 게임 설정과 게임 바이너리를 배포해보겠습니다.

##### 5-7-1. 게임 설정 배포
![game_deploy_config_01](https://static.toastoven.net/prod_gamestarter/console/gamestarter_game_deploy_config_01_202311.png)

TEST 배포존에서 게임 설정의 [배포] 버튼을 클릭하면 게임 설정 배포 팝업창이 등장합니다.

게임 설정 배포에는 [예약 배포]와 [즉시 배포] 2가지 방법으로 진행할 수 있습니다.

###### 1) 게임 설정 선택
등록된 게임 설정들이 표시됩니다.
이 중에 배포하고자 하는 게임 설정을 선택합니다.

###### 2) 예약 배포
![game_deploy_config_01-reserve](https://static.toastoven.net/prod_gamestarter/console/gamestarter_game_deploy_config_01-reserve_202311.png)

예약하려는 기준 시간과 배포 시간을 설정한 후에 [확인] 버튼을 클릭하면 마지막 단계인 [배포 비교] 단계로 이동합니다.

###### 3) 즉시 배포

즉시 배포에는 별도로 설정해야 내용이 없습니다.
바로 마지막 단계인 [배포 비교] 단계로 이동합니다.

###### 4) 배포 비교
![game_deploy_config_02](https://static.toastoven.net/prod_gamestarter/console/gamestarter_game_deploy_config_02_202311.png)

최근에 배포한 게임 설정과 비교하는 팝업창이 등장합니다.

새롭게 배포하려는 게임 설정이 맞는지 모두 확인되면 [배포] 버튼을 통해서 즉시 배포나 예약 배포를 실행할 수 있습니다.
틀리지 않게 설정한 부분이 확인 한 후 [배포] 버튼을 클릭하면 배포가 됩니다.

[배포] 버튼을 클릭하면 배포 팝업창이 닫히면서 해당 배포존에 게임 설정 배포 상태에 변경된 것을 확인할 수 있습니다.
![game_deploy_config_complete](https://static.toastoven.net/prod_gamestarter/console/gamestarter_game_deploy_config_complete_202311.png)


##### 5-7-2. 게임 바이너리 배포
게임 바이너리 배포는 게임 바이너리 업로드가 완료된 게임 바이너리를 적용하는 단계입니다.

![game_deploy_binary_01](https://static.toastoven.net/prod_gamestarter/console/gamestarter_game_deploy_binary_01_202311.png)
TEST 배포존에서 게임 바이너리의 [배포] 버튼을 클릭하면 배포창이 등장합니다.

![game_binary_deploy_02](https://static.toastoven.net/prod_gamestarter/console/gamestarter_game_binary_deploy_02_202311.png)
게임 바이너리 배포도 [예약 배포]와 [즉시 배포] 2가지 방법으로 진행할 수 있습니다.

###### 1) 예약 배포
![game_deploy_binary_02-reserve](https://static.toastoven.net/prod_gamestarter/console/gamestarter_game_deploy_binary_02-reserve_202311.png)

예약하려는 기준 시간과 배포 시간을 설정한 후에 [확인] 버튼을 클릭하면 게임 바이너리 배포가 예약됩니다.

###### 2) 즉시 배포
[즉시 배포]를 실행하면 업로드된 게임 바이너리로 즉시 배포가 진행됩니다.


[예약 배포]나 [즉시 배포] 버튼을 클릭하면 팝업창이 닫히면서 해당 배포존에 게임 바이너리 배포 상태가 변경된 것을 확인할 수 있습니다.
![game_deploy_binary_complete](https://static.toastoven.net/prod_gamestarter/console/gamestarter_game_deploy_binary_complete_202311.png)
배포가 완료된 경우 위의 그림처럼 배포 완료가 표시됩니다.

#### 5-8 배포 이력

##### 5-8-1. 게임 설정 배포 이력
![game_history_config_01](https://static.toastoven.net/prod_gamestarter/console/gamestarter_game_history_config_01_202311.png)

게임 설정 배포 이력은 배포한 게임 설정들에 대한 이력을 조회할 수 있습니다.
우측의 검색 조건을 통해서 조회 결과를 필터링할 수 있습니다.

###### 1) 게임 설정 이름
배포된 게임 설정 이름으로 배포 이력을 필터링할 수 있습니다.

###### 2) 배포 일시
지정한 기간에 배포된 배포 이력을 필터링할 수 있습니다.

###### 3) 배포 상태
특정 배포 상태로 배포 이력을 필터링할 수 있습니다.

배포 이력 조회 결과에는 다음과 같은 필드가 있습니다.
![game_history_config_02](https://static.toastoven.net/prod_gamestarter/console/gamestarter_game_history_config_02_202311.png)

###### 1) 게임 설정 이름
배포된 게임 설정의 이름을 나타냅니다.

###### 2) 배포존
게임 설정이 배포된 배포존을 나타냅니다.

###### 3) 배포 일시
게임 설정이 배포된 날짜를 나타냅니다.

###### 4) 배포자
게임 설정을 배포한 사용자의 마스킹 된 이메일 주소가 나타냅니다.

###### 5) 배포 상태
게임 설정이 배포된 상태를 나타냅니다.

> [참고] 배포 상태
>
> - `배포 중`: 게임 설정 배포가 진행 중임을 나타냅니다.
> - `배포 완료`: 게임 설정 배포가 완료되었음을 나타냅니다.
> - `배포 실패`: 게임 설정 배포 중 오류가 발생하였음을 나타냅니다.
> - `배포 예약`: 게임 설정 배포 예약이 등록되었음을 나타냅니다.
> - `배포 예약 취소`: 게임 설정 배포 예약이 취소되었음을 나타냅니다.

###### 6) 메모
배포된 게임 설정의 메모를 나타냅니다.


##### 5-8-2. 게임 바이너리 배포 이력
![game_history_binary_01](https://static.toastoven.net/prod_gamestarter/console/gamestarter_game_history_binary_01_202311.png)

게임 바이너리 배포 이력은 배포한 게임 바이너리의 배포 이력을 조회할 수 있습니다.
우측의 검색 조건을 통해서 조회 결과를 필터링할 수 있습니다.

###### 1) 배포 일시
지정한 기간에 배포된 배포 이력을 필터링할 수 있습니다.

###### 2) 배포 상태
특정 배포 상태로 배포 이력을 필터링할 수 있습니다.

배포 이력 조회 결과에는 다음과 같은 필드가 있습니다.
![game_history_binary_02](https://static.toastoven.net/prod_gamestarter/console/gamestarter_game_history_binary_02_202311.png)

###### 1) 배포존
게임 바이너리가 배포된 배포존을 나타냅니다.

###### 2) 게임 바이너리
배포된 게임 바이너리의 정보가 표시됩니다.
게임 바이너리 정보는 파일의 개수와 파일의 크기로 구성되어 있습니다.

###### 3) 배포 일시
게임 바이너리가 배포된 날짜를 나타냅니다.

###### 4) 배포자
게임 바이너리를 배포한 사용자의 마스킹 된 이메일 주소가 나타냅니다.

###### 5) 배포 상태
게임 바이너리를 배포된 상태를 나타냅니다.

> [참고] 배포 상태
>
> - `배포 중`: 게임 바이너리 배포가 진행 중임을 나타냅니다.
> - `배포 완료`: 게임 바이너리 배포가 완료되었음을 나타냅니다.
> - `배포 실패`: 게임 바이너리 배포 중 오류가 발생하였음을 나타냅니다.
> - `배포 예약`: 게임 바이너리 배포 예약이 등록되었음을 나타냅니다.
> - `배포 예약 취소`: 게임 바이너리 배포 예약이 취소되었음을 나타냅니다.

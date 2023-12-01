## Game > GameStarter > 콘솔 사용 가이드 > 인스톨러

## Installer
인스톨러를 생성하려면 필요한 설정이 있습니다.
이 설정들에 대해서 설명합니다.

### 1. URL scheme 설정
![installer_urlscheme](https://static.toastoven.net/prod_gamestarter/console/gamestarter_installer_urlscheme_202311.png)

#### 1) URL scheme

URL Scheme은 사용자가 정의한 프로토콜로 앱과 통신을 할 수 있도록 해줍니다.
GameStarter는 사용자가 등록한 URL Scheme으로 런처를 실행할 수 있도록 해줍니다.

> <font color="red">[주의]</font><br/>
>
> URL Scheme는 한 번 설정한 이후에는 변경하기 어렵습니다.
> 다른 프로그램에서 사용하는 URL Scheme로 설정하면 GameStarter가 정상적으로 실행되지 않을 수 있습니다.


> [참고] URL Scheme 이름 규칙
>
> - 첫 글자는 영문 소문자로 시작해야 합니다.
> - 영문 소문자 및 숫자만 가능하며, 최대 20자까지 가능합니다.

> [참고] 배포존
> URL Scheme는 한 번만 입력받지만 배포존은 여러 개가 존재합니다.
> GameStarter에서는 이를 구분하기 위해서 SERVICE 배포존을 제외한 존에서는 `-<zone>` 형태로 마지막 부분에 자동으로 추가합니다.
>
> 예) SERVICE
> - URL Scheme: example
>
> 예) DEVELOP
> - URL Scheme: example-develop

### 2. 공통 이름 설정
![installer_names](https://static.toastoven.net/prod_gamestarter/console/gamestarter_installer_names_202311.png)

#### 1) 공통 이름
공통 이름은 런처 설치 프로그램과 삭제 프로그램 이름으로 사용되며, 설치 폴더와 경로에도 사용됩니다.

> <font color="red">[주의]</font><br/>
>
> 공통 이름은 한 번 등록한 이후에는 변경하기 어렵습니다.

> [참고] 공통 이름 규칙
>
> - 공통 이름은 20자 이내의 영문 대소문자, 숫자만 입력 가능합니다.

> [참고] 배포존
> 공통 이름은 한 번만 입력받지만 배포존은 여러 개가 존재합니다.
> GameStarter에서는 이를 구분하기 위해서 SERVICE 배포존을 제외한 존에서는 `_<ZONE>` 형태로 마지막 부분에 자동으로 추가합니다.
>
> 예) SERVICE
> - 런처 Installler 이름: `<공통이름>Insatller`
> - 런처 Uninstaller 이름: `<공통이름>Uninstaller`
> - 런처 설치 폴더 이름: `<공통이름>`
> - 런처 설치 경로: `C:\Users\<UserName>\AppData\Roaming\<공통이름>`
>
> 예) DEVELOP
> - 런처 Installler 이름: `<공통이름>Insatller_DEVELOP`
> - 런처 Uninstaller 이름: `<공통이름>Uninstaller_DEVELOP`
> - 런처 설치 폴더 이름: `<공통이름>_DEVELOP`
> - 런처 설치 경로: `C:\Users\<UserName>\AppData\Roaming\<공통이름>_DEVELOP

### 3. 런처 설정
![installer_icons](https://static.toastoven.net/prod_gamestarter/console/gamestarter_installer_icons_202311.png)

GameStarter 런처가 설치되고 난 이후 바탕화면에 자동으로 런처 바로 가기를 생성할 수 있습니다.
이 바로 가기를 생성하는 데 필요한 설정 정보가 필요합니다.

#### 1) 바로 가기 아이콘
바로가기 아이콘 이미지를 등록합니다.

#### 2) 바로 가기 아이콘 이름


### 4. 인스톨러 설정 확인
![installer_confirm](https://static.toastoven.net/prod_gamestarter/console/gamestarter_installer_confirm_202311.png)

인스톨러에 필요한 설정을 모두 마치면 최종적으로 확인하는 팝업창이 표시됩니다.
입력한 내용이 올바른지 확인이 끝나면 [확인] 버튼을 클릭합니다.

### 5. 인스톨러 배포
![installer_build](https://static.toastoven.net/prod_gamestarter/console/gamestarter_installer_build_202311.png)

이제 인스톨러 생성이 시작되었습니다.
이 작업은 몇 분에서 수십 분이 소요될 수 있습니다.

#### 1) 인스톨러 배포 일시
배포 일시는 배포 상태에 따라서 변경됩니다.
예를 들어 배포 상태가 `생성 중`이라면 생성 일시, `생성 완료`라면 업로드 완료 일시로 변경됩니다.

#### 2) 인스톨러 배포 상태
배포 상태는 총 3가지의 상태를 가집니다.

1. 생성 중
2. 실패
3. 생성 완료

> [참고]
>
> 빌드 상태가 `실패`면 고객센터로 문의를 하시기 바랍니다.


![installer_deploy](https://static.toastoven.net/prod_gamestarter/console/gamestarter_installer_deploy_202311.png)

인스톨러 생성 작업이 완료되면 배포 상태가 `생성 완료`로 변경됩니다.

### Ubuntu 설정

1.  **원격 데스크톱 활성화 및 주소 확인**
    * `설정` > `공유(Sharing)` 메뉴로 이동합니다.
    * `원격 데스크톱(Remote Desktop)`을 활성화합니다.
    * `원격 제어(Remote Control)`를 활성화합니다.
    * **인증(Authentication)** 섹션에서 연결에 사용할 **사용자 이름(User Name)**과 **비밀번호(Password)**를 설정합니다.
    * 표시되는 **원격 데스크톱 주소(Remote Desktop Address)**를 기록해 둡니다. (예: `ms-rd://smartcps-3.local`)

2.  **GNOME 원격 데스크톱 서비스 재시작 및 상태 확인**
    * 아래 명령어를 터미널에 입력하여 서비스를 재시작합니다.
        ```bash
        systemctl --user restart gnome-remote-desktop.service
        ```
    * 서비스가 정상적으로 실행되는지 확인합니다.
        ```bash
        systemctl --user status gnome-remote-desktop.service
        ```
    * 만약 RDP 서버가 실행되지 않으면, `xrdp` 패키지와의 충돌일 수 있으므로 아래 명령어로 `xrdp`를 삭제한 후 다시 시도합니다.
        ```bash
        sudo apt remove xrdp
        ```

3.  **부팅 시 서비스 자동 실행 설정**
    * 시스템 부팅 시 원격 데스크톱 서비스가 자동으로 시작되도록 설정합니다.
        ```bash
        systemctl --user enable gnome-remote-desktop.service
        ```
    * 설정이 잘 적용되었는지 확인합니다.
        ```bash
        systemctl --user is-enabled gnome-remote-desktop.service
        ```

4.  **키링(Keyring) 비밀번호 설정 해제**
    * `seahorse` (Passwords and Keys) 애플리케이션을 실행합니다.
    * 좌측 메뉴에서 `Default Keyring`을 찾아 마우스 우클릭 후 `Change Password`를 선택합니다.
    * 현재 설정된 비밀번호를 입력합니다.
    * 새로 설정할 비밀번호는 **아무것도 입력하지 않고** `Continue`를 클릭하여 비워둡니다. 이는 원격 접속 시 비밀번호 관련 팝업이 뜨는 것을 방지합니다.

---

### Windows 설정

1.  **원격 데스크톱 연결 실행**
    * Windows 검색 창에 '원격 데스크톱 연결'을 검색하여 실행합니다.

2.  **연결 정보 입력**
    * **컴퓨터(C)** 입력 창에 Ubuntu 설정에서 기록해 둔 주소를 입력합니다. 이때 주소의 맨 앞 `ms-rd://` 부분은 제외하고 입력합니다. (예: `smartcps-3.local`)
    * `연결`을 클릭한 후, Ubuntu 원격 데스크톱 설정 시 지정했던 **사용자 이름**과 **비밀번호**를 입력하여 접속합니다.
      
*.  **바로가기 만들기**
    * 위 연결 정보 입력시 좌측 하단에 표시 버튼을 누른 후, 다른 이름으로 저장을 누르면 바로가기가 생성됨.
---

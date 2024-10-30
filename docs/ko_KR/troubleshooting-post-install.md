# Troubleshooting (Post-Install)

This page offers troubleshooting advice for commonly encountered issues after custom firmware is installed. 만약 이 페이지의 해결책만으로 문제를 해결할 수 없다면, [Nintendo Homebrew Discord 서버](https://discord.gg/MWxPgEp)에 들어가서 당신의 문제와 시도한 해결책을 설명해 주세요.

## Boot issues

::: info

여기서 안내하는 설명은 일반적으로 최신 커스텀 펌웨어 설정(boot9strap + Luma3DS 8.0 이상)에 적용됩니다. 만약 콘솔이 이전 설정(arm9loaderhax 또는 menuhax 기반 등)으로 구동되고 있다면, 이 설명을 따르기 전에 설정을 업데이트해야 합니다.

:::

### 전원/알림 LED

:::details 콘솔을 켜도 켜지지 않거나, 혹은 부팅 시 알림 LED가 색상을 표시합니다

`boot.firm` 파일에 문제가 있습니다. [boot9strap 1.4](https://github.com/SciresM/boot9strap/releases/tag/1.4)를 실행하고 있다면, 3DS 알림 LED가 특정 색상으로 깜빡일 겁니다. 이 색상은 SD 카드 혹은 내부 메모리에 있는 `boot.firm`의 오류를 분석하기 위해 이용됩니다. 구 버전의 boot9strap에서는 콘솔을 켜려 할 때 파란 LED가 켜졌다가 즉시 꺼질 것입니다.

알림 LED가 깜빡인다면:

- **하얀색**: SD 카드 혹은 내부 메모리에서 `boot.firm`을 찾지 못했습니다.
- **다홍색**: SD 카드에서 `boot.firm`을 찾지 못했습니다. 내부 메모리에 있는 `boot.firm`을 확인했으나, 파일이 손상되었습니다.
- **빨간색**: `boot.firm` 파일을 찾았지만, SD 카드와 내부 메모리에 있는 파일 모두가 손상되었습니다.

[Luma3DS의 최신 버전](https://github.com/LumaTeam/Luma3DS/releases/latest)을 다운받아 압축을 해제해, 새 `boot.firm` 파일을 SD 카드의 루트 디렉토리에 넣어주세요. (파일이 이미 있다면 덮어씌워주세요.) `boot.firm` 파일이 계속 문제가 있는 것으로 인식된다면, SD 카드에 문제가 있는지 확인해야 할 수 있습니다: ([Windows](h2testw-\(windows\)), [Linux](f3-\(linux\)), or [macOS](f3xswift-\(mac\))) 또, WinRAR로 압축 해제한 파일은 3DS에서 문제를 자주 일으키는 것으로 알려져 있습니다.

순간적르로 백라이트가 켜졌다 꺼지면서 "퍽 소리"가 들린다면, 콘솔의 하드웨어 문제인 것입니다. (백라이트 케이블이 연결이 끊기는 등) 이 경우 특정 각도로 콘솔을 들면 부팅될 수도 있습니다.

:::

:::details 파란 전원 LED가 켜진 상태로 콘솔이 검은 화면에서 작동하지 않습니다

다음 단계는 순서 없이 진행 가능하나, 시간 소모가 적은 것부터 긴 순서로 정렬되어 있습니다.

1. 콘솔의 전원을 종료하고, SD 카드를 분리한 뒤, 다시 장착하고 전원을 켜 보세요.
2. 전원을 끄고 게임 카트리지가 장착되어 있다면 분리한 다음, 10분 정도 기다려 주세요. 10분 후에 정상적으로 부팅된다면, 문제는 해결된 것이며 재발 가능성이 낮습니다
3. SD 카드의 `Nintendo 3DS` 폴더를 다른 이름(예: `NIntendo 3DS_BACKUP`)으로 변경 후 부팅해보세요. 콘솔이 정상적으로 부팅된다면, `Nintendo 3DS` 폴더 내부에 문제가 있는 것입니다. 홈 메뉴의 추가 데이터를 정리해주세요:
   - SD 카드에 있는 `/Nintendo 3DS/<ID0>/<ID1>/extdata/00000000/` 폴더로 이동해 주세요
   - 콘솔 지역에 해당되는 폴더를 삭제해 주세요:
     - **EUR 지역**: `00000098`
     - **JPN 지역**: `00000082`
     - **USA 지역**: `0000008f`
     - **CHN 지역**: `000000A1`
     - **KOR 지역**: `000000A9`
     - **TWN 지역**: `000000B1`
4. 복구 모드로 부팅하여 본체를 업데이트해 보세요:
   - 콘솔의 전원을 꺼 주세요
   - (L 버튼) + (R 버튼) + (D패드 상) + (A) 버튼을 길게 눌러주세요
   - 콘솔의 전원을 켜 주세요
   - 성공적일 경우엔 콘솔이 "본체 업데이트"로 부팅됩니다
5. [CTRTransfer](ctrtransfer) 설명서를 따라 주세요
6. 지원이 필요하면 [Nintendo Homebrew Discord 서버](https://discord.gg/MWxPgEp)에 (영어로) 지원을 요청해 주세요

:::

### 부팅 중에 에러 메시지가 표시됩니다

:::details "An error has occurred: Failed to apply 1 FIRM patch(es)" 또는 "An exception has occurred -- Current process: pm"

Your Luma3DS version is outdated. 최신 버전의 [Luma3DS](https://github.com/LumaTeam/Luma3DS/releases/latest)을 다시 내려받고 `boot.firm` 파일을 SD 카드의 최상위 디렉토리에 복사해주세요. 이미 파일이 있으면 덮어씌워 주세요. ZIP 파일을 압축 해제할 때, 3DS 관련 파일에서 문제가 있다고 알려져 있은 WinRAR를 제외한 프로그램으로 압축 해제해 주세요.

:::

:::details "Unable to mount CTRNAND or load the CTRNAND FIRM. Please use an external one."

이러한 문제가 발생하는 경우의 수는 여러 가지가 있습니다. 어느 경우가 됐던, 일반적으로 [CTRTransfer](ctrtransfer) 가이드를 통해 고칠 수 있습니다.

:::

:::details "에러가 발생했습니다. 본체의 전원 버튼을 길게 눌러 전원을 끈 후..."

ARM11 오류 핸들러가 꺼져있거나, 커스텀 펌웨어가 정상적으로 설치되지 않았습니다. ARM11 오류 핸들러를 활성화해보세요:

- 콘솔의 전원을 꺼 주세요
- (Select) 버튼을 길게 눌러 주세요
- (Select) 버튼을 계속 눌러 있는 상태에서 콘솔의 전원을 켜 주세요
- "Disable ARM11 exception handlers" 박스가 체크되어 있다면, 체크를 해제해 주세요

:::

:::details HOME 메뉴에 설치한 앱이 없어졌습니다

여러 이유가 있을 수 있지만, 대부분 시스템이 SD 카드를 읽지 못해 발생합니다.
SD 카드가 읽혔는지 확인하려면 SELECT를 누른 채 부팅해 아래 화면의 노란색 문구를 확인하세요: "Booted from CTRNAND via B9S"가 표시된다면 SD 카드가 읽히지 않아 내부 메모리에서 부팅되었음을 의미합니다.
그렇다면, 다음 단계를 따라주세요. 쉬운 것부터 어려운 순으로 나열되어 있습니다:

1. 콘솔의 전원을 종료하고, SD 카드를 분리한 뒤, 다시 장착하고 전원을 켜 보세요
2. 콘솔의 전원을 종료하고, SD 카드를 분리한 뒤, PC에 장착하세요. 최신 버전의 [Luma3DS](https://github.com/LumaTeam/Luma3DS/releases/latest)를 다운받아 `Luma3DS.zip`에서 `boot.firm` 파일을 복사해 SD 카드의 루트에 넣어주세요. 이미 있다면 덮어씌워주세요
3. 콘솔의 전원을 끄고, SD 카드를 분리한 뒤, PC에 장착해 운영 체제에 따른 방식으로 포멧해 주세요: [Windows](formatting-sd-\(windows\)), [macOS](formatting-sd-\(mac\)), [Linux](formatting-sd-\(linux\)). _(이 과정은 SD 카드의 데이터를 모두 삭제합니다)_
4. 컴퓨터의 운영 체제에 따라 SD 카드에 오류가 있는지를 확인해주세요: [Windows](h2testw-\(windows\)), [Linux](f3-\(linux\)), [macOS](f3xswift-\(mac\)). SD 카드에 오류가 있다고 표시되면, SD 카드를 교체해야 합니다
5. SD 카드 슬롯이 파손되었을 수 있습니다. [Nintendo Homebrew Discord 서버](https://discord.gg.MWxPgEp)에 오셔서 도움을 요청하세요

:::

:::details Blue "BOOTROM ERROR" screen

이 콘솔은 벽돌 상태입니다. ntrboot 플래시카트를 구매한 후 이를 이용해 boot9strap를 설치하여 콘솔을 복구해야 합니다. 이 문제는 또 콘솔의 하드웨어 문제가 있다는 뜻일수도 있습니다. 어떠한 경우가 됐든, [Nintendo Homebrew Discord 서버](https://discord.gg.MWxPgEp)에 오셔서 도움을 요청하세요.

- It is also possible that someone has set a boot-time splash screen that just looks like a brick. Try leaving your console powered on, waiting on the blue screen, for five minutes.

:::

:::details Some other error

Please take a photo of the error and join [Nintendo Homebrew on Discord](https://discord.gg/MWxPgEp) for assistance.

:::

## Software issues on consoles with custom firmware

:::details DSi / DS functionality is broken or has been replaced with Flipnote Studio

1. Download the latest release of [TWLFix-CFW](https://github.com/MechanicalDragon0687/TWLFix-CFW/releases/latest) (the `.3dsx` file)
2. 콘솔의 전원을 꺼 주세요
3. SD 카드의 루트에 `3ds` 폴더가 없을 경우 폴더를 만들어 주세요
4. Copy `TWLFix-CFW.3dsx` to the `/3ds/` folder on your SD card
5. SD 카드를 콘솔에 다시 삽입해 주세요
6. Open the Homebrew Launcher
7. Launch TWLFix-CFW from the list of homebrew
8. Press (A) to uninstall the broken TWL titles
9. Press (Start) to reboot the console
10. 본체 설정의 "기타 설정"에서 가장 오른쪽에 있는 "본체 업데이트"를 선택해 콘솔을 업데이트해 주세요
    - The update will see that the essential TWL titles have been uninstalled, and will redownload and reinstall them
11. Once the update is complete, tap "OK" to reboot the console

:::

:::details GBA Virtual Console and/or Safe Mode functionality is broken

Your console is running Luma3DS 6.6 or older, likely via arm9loaderhax. You should follow [A9LH to B9S](a9lh-to-b9s) to update your console to a modern custom firmware environment.

:::

:::details Extended memory mode games (Pokemon Sun/Moon, Smash, etc.) don't work

This can occur after a CTRTransfer or region change on Old 3DS / 2DS. Follow the instructions [here](region-changing#section-vi---fixing-locale-related-issues) to fix this issue (skipping steps 3, 4, 5, and 6).

:::

:::details Exception screen when booting/loading an application

Look for your exception screen in [this page](https://wiki.hacks.guide/wiki/3DS:Error_screens/Luma3DS_exception_screen).
If you weren't able to find your error or the instructions didn't work, join [Nintendo Homebrew on Discord](https://discord.gg/MWxPgEp) for further assistance.

:::

:::details Opening the HOME Menu settings crashes the console or loads the Homebrew Launcher

Your console likely still has menuhax67 installed. To uninstall menuhax67, download the latest release of [menuhax67](https://github.com/zoogie/menuhax67/releases/latest) (the menuhax `.zip`), then follow the ["Uninstall menuhax67" section](https://wiki.hacks.guide/wiki/3DS:Alternate_Exploits/menuhax67#Uninstall_menuhax67) here.

:::

:::details Something else

Join [Nintendo Homebrew on Discord](https://discord.gg/MWxPgEp) for assistance, and describe the issue that you see.

:::

## Other troubleshooting

:::details Clear HOME Menu extdata

1. 콘솔의 전원을 꺼 주세요
2. SD 카드를 컴퓨터에 삽입해 주세요
3. Navigate to the `/Nintendo 3DS/<ID0>/<ID1>/extdata/00000000/` folder on your SD card
4. 콘솔 지역에 해당되는 폴더를 삭제해 주세요:
   - **EUR 지역**: `00000098`
   - **JPN 지역**: `00000082`
   - **USA 지역**: `0000008f`
   - **CHN 지역**: `000000A1`
   - **KOR 지역**: `000000A9`
   - **TWN 지역**: `000000B1`
5. SD 카드를 콘솔에 다시 삽입해 주세요

:::

:::details Clear HOME Menu theme data

1. 콘솔의 전원을 꺼 주세요
2. SD 카드를 컴퓨터에 삽입해 주세요
3. Navigate to the `/Nintendo 3DS/<ID0>/<ID1>/extdata/00000000/` folder on your SD card
4. 콘솔 지역에 해당되는 폴더를 삭제해 주세요:
   - **EUR Region**: `000002ce`
   - **JPN Region**: `000002cc`
   - **USA Region**: `000002cd`
   - **KOR Region**: `000002cf`
5. SD 카드를 콘솔에 다시 삽입해 주세요

:::

:::details Manually entering Homebrew Launcher

If you are missing the Homebrew Launcher application from your HOME Menu, you can follow these instructions to manually enter the Homebrew Launcher. (You will need [boot.3dsx and boot.firm](https://github.com/LumaTeam/Luma3DS/releases/latest) on the root of your SD card.)

<!--@include: ./_include/launch-hbl-dlp.md -->

:::

:::details Turning off Parental Controls

You can disable the Parental Controls feature by going to System Settings -> Parental Controls and inserting the PIN, then pressing "Clear Settings", then "Delete" to remove it.
However, if you do not know the PIN and therefore cannot access the console's settings, you will need to disable it. In order to do this, you need to obtain your console's master key (mkey):

1. Go to [this website](https://mkey.eiphax.tech/)
2. Fill the following boxes with the information:
   - Device Type: Select "3DS" (the same applies if you are using a 2DS, New 3DS (XL/LL) or New 2DS (XL/LL))
   - System Date: The day and month your console's clock is set to
   - Inquiry Number: Can be obtained by pressing "Forgot PIN" then "I Forgot" in the Parental Controls screen
3. After you have obtained your mkey, press OK on the screen you have obtained your Inquiry Number, then input the master key
4. Press "Clear Settings", then "Delete" to remove all Parental Controls data

:::

---

<!--@include: ./_include/troubleshooting-return.md -->
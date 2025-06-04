# Microsoft Network Monitor

네트워크 패킷 단에서 분석하기 위해서 위 도구를 사용하여 캡쳐하고 분석합니다.  
seq&ack 확인을 통한 패킷 누락 및 Payloadlen 값 확인 후, 패킷 단편화 분석 등등...

다운로드 링크: [https://www.microsoft.com/en-us/download/details.aspx?id=4865](https://www.microsoft.com/en-us/download/details.aspx?id=4865)

## 1. 넷몬 설치
[Korean]  
![](./MD_Images/netmon_01001.jpg)
* 관리자 권한으로 실행합니다.

![](./MD_Images/netmon_01002.jpg)
* Network Monitor 설치에 동의합니다.

![](./MD_Images/netmon_01003.jpg)
* 다음으로 넘어갑니다.

![](./MD_Images/netmon_01004.jpg)
* 라이센스에 동의합니다.

![](./MD_Images/netmon_01005.jpg)
* 자동 업데이트를 비활성화합니다.

![](./MD_Images/netmon_01006.jpg)
* 모든 옵션을 설치합니다.

![](./MD_Images/netmon_01007.jpg)
* Network Monitor를 설치합니다.

[English]  
![](./MD_Images/netmon_01001.jpg)
* Run with administrator privileges.

![](./MD_Images/netmon_01002.jpg)
* Agree to install Network Monitor.

![](./MD_Images/netmon_01003.jpg)
* Move Next Course

![](./MD_Images/netmon_01004.jpg)
* Agree with the license.

![](./MD_Images/netmon_01005.jpg)
* Disable automatic updates.

![](./MD_Images/netmon_01006.jpg)
* Install all options.

![](./MD_Images/netmon_01007.jpg)
* Install Network Monitor.

## 2. 네트워크 캡쳐(로컬 분석)
_용량을 한정하여 캡쳐하고 싶다면 GUI가 아닌 CMD로 수집합니다._
  
![](./MD_Images/netmon_02001.jpg)
* 관리자 권한으로 실행합니다.

![](./MD_Images/netmon_02002.jpg)
* `Tools` -> `Option`으로 이동합니다.

![](./MD_Images/netmon_02003.jpg)
* `Parser Profiles` -> `Windows` -> `Set As Active`을 순서대로 클릭합니다.
* 위 설정으로 Netmon에서 Windows Parser Profile을 활성화합니다.

![](./MD_Images/netmon_02004.jpg)
* 패킷 수집을 위한 새로운 캡쳐를 생성합니다.

![](./MD_Images/netmon_02005.jpg)
* `Start`를 클릭하여 패킷 수집을 시작합니다.

![](./MD_Images/netmon_02006.jpg)
* 수집이 종료된 후, `Stop`을 클릭합니다.
* 데이터 수집 후, `File` -> `Save AS`로 이동합니다.

![](./MD_Images/netmon_02007.jpg)
* 수집된 데이터를 원하는 경로에 저장합니다.

<br>

## 3. 네크워크 캡쳐(덤프 수집)

[Korean]  
Netmon 수집 시, 해당 서버에서 발생하는 모든 네트워크 패킷이 캡처되므로 초기에는 1분간만 수집하여 1분 동안의 데이터 적재량을 모니터링해 주시기 바랍니다. 문제가 없다고 판단될 경우, 장애 재현 시점 또는 10분간 수집하여 전달해 주시기 바랍니다.

수집 시에 디스크 용량을 확인 부탁드리며, 용량이 부족할시에 즉시 CMD창에서 `Ctrl + C`를 입력하여 수집을 종료합니다.

![](./MD_Images/netmon_03001.jpg)
* 실행창에서 cmd를 관리자 권한으로 실행합니다.
* `cmd` 입력 후, `Ctrl + Shift + Enter`를 동시 입력하여 관리자 권한으로 실행됩니다.

![](./MD_Images/netmon_03002.jpg)
```
nmcap.exe /network * /capture /file c:\temp\Capture.chn:100M /CaptureProcesses
```
위 명령어를 실행하여 네트워크 패킷을 수집합니다.
* c:\temp 경로에 Capture 이름을 한 cap파일들을 100Mbyte 단위로 수집합니다.


![](./MD_Images/netmon_03003.jpg)
* 수집이 완료된 후, `Ctrl + C`를 입력하여 수집을 종료합니다.

![](./MD_Images/netmon_03004.jpg)
* 수집된 데이터를 전달합니다.

<br>

[English]  
When collecting Netmon, all network packets from that server are captured, so initially collect only one minute and monitor the data load for one minute. If you think there is no problem, collect and deliver it at the time of failure or for 10 minutes.

Please check the disk capacity when collecting, and if the capacity is insufficient, immediately enter 'Ctrl + C' in the CMD window to end the collection.

![](./MD_Images/netmon_03001.jpg)
* In the Run window, run cmd with administrator privileges.
* After entering 'cmd', enter 'Ctrl + Shift + Enter' at the same time and run with administrator authority.

![](./MD_Images/netmon_03002.jpg)
```
nmcap.exe /network * /capture /file c:\temp\Capture.chn:100M /CaptureProcesses
```
Run the above command to collect network packets.
* Collect cap files named Capture in the c:\temp path repeatedly in units of 100 Mbytes.

![](./MD_Images/netmon_03003.jpg)
* After the collection is complete, type 'Ctrl + C' to end the collection.

![](./MD_Images/netmon_03004.jpg)
* Deliver the collected data.
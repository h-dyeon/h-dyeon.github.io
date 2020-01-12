---
layout: post
title:  "[Linux] Window10에서 Ubuntu 듀얼부팅 실패기"
subtitle:   "듀얼부팅 실패"
categories: Dev
tags: Linux
comments: true
date:  2019-12-02 22:00:00
---



설마 했지만 역시나 였다.

왜 남들은 볼까 말까 하는 에러를 나는 이렇게 많이 마주치는지... ㅂㄷㅂㄷ



# 환경

- Lenovo Yoga 720
- 삼성 970 Evo Plus (NVME M.2)
- Window10

![내 노트북의 시스템 정보](https://h-dyeon.github.io/assets/img/Dev/Linux/191202-Linux-bualbootfail/systemInfo.png)








# 시도한 방법

1. 처음엔 Ubuntu 16.04버전을 시도했다. [http://releases.ubuntu.com/xenial/](http://releases.ubuntu.com/xenial/?fbclid=IwAR1ojoRopNWytuybsrxe5Wij8vzu1rJ3Dc44xWtZZ59kFKxOrJQik38EOSA)  에서  64-bit PC(AMD64) desktop image 를 다운받는다. ( https://ubuntu.com/download/desktop 에서 ubuntu 18.04.3 LTS도 해봤지만 역시나 안된다.)

2. rufus 프로그램을 이용하여 16기가 짜리 USB Flash Drive에 GPT(파티션 방식), FAT32(파일시스템)으로 iso파일을 담았다. 일반 USB로 했을때도 역시나 불가능이었다. 그리고 디스크가 GPT 혹은 MBR을 사용하는지 확인하는 방법은 아래 사진처럼 cmd에서 확인 가능하다.

    ![GPT or MBR](https://h-dyeon.github.io/assets/img/Dev/Linux/191202-Linux-bualbootfail/gptcheck.png)

3. 디스크를 파티션을 분할한다.

4. 노트북을 다시 시작하기를 해서 lenovo로고가 보일 때 <code>Fn+F2</code>버튼을 연타를 해서 bios모드에 진입한다. Fast boot를 disabled한다. (사실 이건 별 의미 없었다.)

5.   <code>Fn+F12</code>로 usb부팅을 선택해서 우분투 화면이 뜨길 기다린다. 







# 문제 상황

![노트북이 ssd인식을 못함](https://h-dyeon.github.io/assets/img/Dev/Linux/191202-Linux-bualbootfail/nothingpng.png)

![usb만 인식하는 상황](https://h-dyeon.github.io/assets/img/Dev/Linux/191202-Linux-bualbootfail/nothing2png.png)

사진처럼 아무것도 뜨지 않는다. ubuntu를 설치할 디스크를 골라서 선택해야 하는데 usb만 인식하고 내 노트북의 ssd를 인식을 하지 못했다.







# 또다시 구글 검색...

- 구글에 **"ubuntu installer can't see windows partitions"**라고 검색했더니 SATA Controller Mode 를 기존엔 **RAID**이던것을 **AHCI**로 변경해서 재부팅하라고 했다. 결과는 기존에 잘되던 윈도우도 부팅이 안되서 하마터면 서비스 센터에 갈뻔했음............

- 페북 생활코딩에 도움을 요청했더니 NVME type SSD에 관해 언급이 있었다. SSD 타입이 관련 있을 거라고는 생각도 못했는데... 또다시 구글에 검색했다.

- **"nvme ubuntu"**로 검색했더니 드디어 나와 같은 증상을 호소하는 사람들이 보였다. ubuntu가 disk를 인식못한다는 질문글들이 가득했지만 해결방법이라고 comment달린 것들은 모두 이미 해본것... 특히 RAID에서 AHCI로 변경하라는 말이 제일 많았는데 역시나 그 밑에 comment로 "그러면 window10이 작동이 안되요!"가 달려있었다.

  >  [Problem installing Ubuntu 18.04 on NVMe](https://ubuntuforums.org/showthread.php?t=2390475&page=2)

  >  [M.2 Samsung SM951 NVME SSD Not Recognized On Linux](https://superuser.com/questions/1022849/m-2-samsung-sm951-nvme-ssd-not-recognized-on-linux)







# 최후의 방법

검색을 하다보니 최후의 방법들이 있었다. 결론부터 말하자면 1번은 실패했고 2번은 시도조차 하지 않았다.

### linux boot option수정

 [PCIe M2 드라이브를 사용하여 시스템에서 Ubuntu 로드]( https://www.dell.com/support/article/kr/ko/krbsd1/sln299303/loading-ubuntu-on-systems-using-pcie-m2-drives?lang=en ) 

위 사이트에서 부팅옵션을 수정하라는 코멘트가 있었다. 

>  Modify the boot option to add "nvme_load=YES" and remove "quiet splash ---"

![부팅옵션 화면](https://h-dyeon.github.io/assets/img/Dev/Linux/191202-Linux-bualbootfail/bootoption.png)

ubuntu를 설치할 방법을 선택하는 화면에서 'e'를 누르면 위 사진과 같은 화면이 뜨는데 "quiet splash ---" 를 삭제하고 그 자리에  "nvme_load=YES"를 넣고는 부팅을 시도했다. 결과는 컴퓨터가 멈췄고 식겁하면서 전원 버튼을 눌러서 강제 종료했다 ^-^....

### BIOS 업데이트

이건 그냥 시도조차 안했다.





# 결론

포기! ^-^ 
가상환경으로 결정....
노트북을 수리할 때 ssd를 교체해야 했다.
새로 살 때 500GB라며 좋아하면서 구매했는데... 
듀얼 부팅 하실 분은 삼성 970 Evo Plus (NVME M.2) 사지마세요.... 
(+ 어쩌면 그냥 linux설치도 안될 수 도 있어요....)




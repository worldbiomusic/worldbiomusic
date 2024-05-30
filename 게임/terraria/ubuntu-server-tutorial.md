---
title: 우분투 테라리아 서버 세팅 튜토리얼
date: 2020-01-01 00:00:00 +09:00
categories: [게임, 테라리아]
tags: [테라리아]
---

# 환경
- Oracle cloud
- Ubuntu 20.04

# 순서
시작 전 terraria를 실행하기 위한 툴 다운받아야 함
`sudo apt install mono-complete`

1. terraria dir 생성
2. [Terraria servers](https://terraria.fandom.com/wiki/Server#Downloads)에서 버전에 맞는 것 다운로드 (`wget <url>`)
3. 다운받은 zip파일을 unzip으로 풀기
4. `<버전>/Linux`로 들어가서 `mono ./TerrariaServer.exe`로 실행하면 끝
(screen 이용해서 `screen -S <name> mono ./TerrariaServer.exe`도 가능)

# 기타
- 포트 당연히 포워딩 해야 함 (테라리아 기본포트: `7777`) (리눅스는 firewall-cmd로 재설정 해야 함)
- 파일 실행모드로 변경하려면 `chmod ug+x <file>`
- 만약 밑과 같은 오류로 서버 실행중 팅긴다면 
```
3/4/2023 8:41:25 AM
System.TypeInitializationException: The type initializer for 'System.Net.IPAddress' threw an exception. ---> System.MissingMethodException: Method not found: !0 modreq(System.Runtime.InteropServices.InAttribute)& System.ReadOnlySpan`1.get_Item(int)
  at System.Net.IPAddress..ctor (System.Byte[] address, System.Int64 scopeid) [0x00010] in <32fc020d7373456995b3d44fa885e01a>:0
  at System.Net.IPAddress..cctor () [0x00032] in <32fc020d7373456995b3d44fa885e01a>:0
   --- End of inner exception stack trace ---
  at Terraria.Netplay.StartServer () [0x00000] in <b998d50b13c541e38cc44446c2f4660e>:0
  at Terraria.Main.DedServ () [0x00cd9] in <b998d50b13c541e38cc44446c2f4660e>:0
  at Terraria.Program.RunGame () [0x00077] in <b998d50b13c541e38cc44446c2f4660e>:0
```
다음 명령어들로 특정 파일 삭제 ([참고](https://forums.terraria.org/index.php?threads/system-typeinitializationexception-on-1-4-2-1-1-4-1-2-works.104689/))
```
cd /path/to/terraria-server/
rm System*
rm Mono*
rm monoconfig
rm mscorlib.dll
```
- 지금 다운받은 것은 바닐라 서버 프로그램으로 플러그인 등을 적용시키려면 [TShock](https://github.com/Pryaxis/TShock) 사용해야 함
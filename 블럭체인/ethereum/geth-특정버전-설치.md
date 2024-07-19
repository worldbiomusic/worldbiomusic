# src 빌드
https://github.com/ethereum/go-ethereum/releases에서 원하는 버전의 src code 빌드하기 (오래걸림)

# package manager
`apt install ethereum=1.14.0`과 같이 버전 명시 이용

# download page
> 이미 다운받은 파일이 있으면 관련 파일 제거
> 예. sudo apt autoremove ethereum

1. https://geth.ethereum.org/downloads에서 특정 파일 다운로드
```sh
wget https://gethstore.blob.core.windows.net/builds/geth-linux-amd64-1.13.15-c5ba367e.tar.gz
```
2. 압축해제
```sh
tar -xzvf geth-linux-amd64-1.13.15-c5ba367e.tar.gz
```
3. 압축해제한 파일 bin 등록
```sh
sudo mv geth /usr/bin
```
4. 실행권한 등록
```sh
sudo chmod +x /usr/bin/geth
```
5. 버전 확인
```sh
geth version
```

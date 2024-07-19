# 설명
- Wallet Import Format의 줄임말로 지갑의 개인키를 간단한 주소로 변환시켜서 복사하기 편하게(보기도 편하게) 해주는 기법

# 기능
- 개인키(private key)를 checksum과 Base58Check encoding을 이용해서 간단한 문자열로 변환시켜주는 기능
- WIF로 변환된 문자열을 다시 private key로 변환시켜주는 기능(checksum으로 유효한 값인지 검사 가능)

# 참고
- https://en.bitcoin.it/wiki/Wallet_import_format

# Security
### Tx Sign이 0 < s < N/2인데 공격을 못하는 리유
### PoW에서 Nonce찾기가 < Diff인데 즉시에 찾지 못하는 리유
# Fork
### 같은 시각에 N+1의 블록이 여러개 동시에 만들어지는 경우 최종 어느것이 선택되는가?
### Block Time, Miners, Nodes, Fork사이관계
# State + VM
### block trie와 storage trie
    - block tries
      state trie
      receipts trie
### tx실행시 block과 vm의 작용
    - transfer인 경우
      block의 trie에서 해당 계약과 관련된 hash값을 변화시키면 끝이다.
    - contract실행인 경우(from,to,value)
    - contract실행인 경우(a,b)
    - contract생성인 경우
### ERC20 TOKEN의 from, to, balance가 어디에 기억되고 어떻게 리용되는가? 어떻게 처리되는가?
# Contract
### Contract처리시 State이 리용되는가?
### 리용된다면 Trie와 어떻게 상호작용하는가?
### 모든 Contract은 VM을 통하여 실행된다. Contract을 포함하지 않는 Tx는 VM과 무관하다?
### 
# Miscellaneous      
### 블록체인에서 가장 핵심적인 산법들
### bloom은 무엇? 어떻게 리용되는가?
### snapshot는 무엇? - backup기능을 수행

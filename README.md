# -Maximum-number-of-dungeon
#python
# In the list in the list, the number of k that can pass before the list, and the number of k after it is the damage that is cut off. What is the maximum number of dungeons that can be passed? 리스트안에 있는 리스트 앞에는 지나갈수 있는 k의 수이고 뒤쪽은 k의 숫자가 깍이는 데미지 이다.
최대 통과 가능 던전의 수는?

from itertools import permutations

def solution(k, dungeons):
    answer = 0
    len_dungeons = len(dungeons)
    for permu in permutations(dungeons, len_dungeons):  # 순열로 경우를 만들어줌
        temp_k = k  # k는 그대로 보존하기 위해 temp_k를 k로 초기화 하고 사용
        count = 0  # 던전 수
        for p in permu:
            if temp_k >= p[0]:  # 최소 필요 피로도가 있는지 확인
                temp_k -= p[1]  # 소모 피로도 빼주기
                count += 1  # 던전 수 업데이트
        answer = max(answer,count)  # 최대 던전 탐험 수 업데이트
    return answer
dungeons=[[80,20],[50,40],[30,10]]
a=solution(80,dungeons)
print(a)
# result--> 3

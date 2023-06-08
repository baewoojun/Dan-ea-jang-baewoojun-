
# 그냥 함수 지정해서 불러오기 or txt나 yml로 저장해서 출력후 저장하기 or class로 불러오기

#===============언어===================
Language = ""  # 언어

#===============난이도=================
# 단어의 난이도 측정을 어떻게 할건가요?
Seconds = 0  # 문제당 시간
Count = 0  # 문제 개수
Life = 0  # 목숨 수

#=================색맹================
Color_Blindness = 0  # 색맹용 0이면 아니면 1
#=================난이도================
# random 문제 출제
# 맞으면 count+=1, 틀리면 Life -=1

class DJOptions:
    def Language(self, x):
        global lang
        lang = x

    def Count(self, x, wordbook):
        if x <= 0:
            print("문제 개수는 1 이상이어야 합니다.")
            return

        questions = generate_questions(wordbook, x)

        for i, question in enumerate(questions, start=1):
            print(f"Question {i}: {question}")
            answer = input("Answer: ")
            check_answer(question, answer)

            DJOptions.Life -= 1  # 라이프 감소
            if DJOptions.Life <= 0:
                print("Game Over")
                break

    def Life(self, x):
        if x <= 0:
            print("목숨은 1 이상이어야 합니다.")
            return

        DJOptions.Life = x
        print(f"목숨이 {x}개로 설정되었습니다.")

import random

def generate_questions(wordbook, count):
    # 문제를 저장할 리스트 생성
    questions = []

    # wordbook에서 count 개수만큼의 문제를 랜덤하게 선택하거나 생성하여 questions 리스트에 추가
    for _ in range(count):
        # wordbook에서 랜덤하게 단어 선택
        random_word = random.choice(wordbook)

        # 단어를 기반으로 문제 생성 또는 단어 그 자체를 문제로 사용
        question = generate_question_from_word(random_word)

        # 문제 리스트에 추가
        questions.append(question)

    # 생성된 문제 리스트 반환
    return questions

def generate_question_from_word(word):
    # 단어를 기반으로 문제 생성 또는 단어 그 자체를 문제로 사용하는 로직을 구현
    # 예를 들어, 단어의 뜻을 문제로 만들거나 단어의 알파벳을 섞어서 문제로 만들 수 있습니다.
    # 이 예시에서는 단어 그 자체를 문제로 사용하도록 가정합니다.
    return word


def check_answer(question, answer):
    # 정답을 제공합니다
    correct_answer = get_correct_answer(question)

    if answer == correct_answer:
        count += 1
        print("정답입니다!")
    else:
        life -= 1
        print("오답입니다!")

    print("맞은 개수:", count)
    print("남은 기회:", life)



   

# Dan-ea-jang
# 언어공부 단어장 (영, 한)
어떤 단어에 A 대해 영어 한국어를 집어넣고 단어장에 저장 
게임이 시작되면 난이도 설정 후 단어장에 있는 단어를 랜덤하게 출력  
출력된 단어를 한국어로 적어서 정답이면 점수를 + 아니면 0 
난이도 설정에 맞춰 모든 단어가 나오면 최종 점수를 기록  
 
1.파이썬 사용  
2.사용되는 단어 통일화  
3.텍스트파일의 확장자는 yml, 이미지는 dds로  
4.자유로운 참여  
5.공지, 건의는 이슈 활용  
6.코드는 암호화 없이 자유롭게 배포 가능  
7.단어를 추가할 시 하나의 단어에 하나의 뜻만 있게 <- 해결 방법 있으면 수정 가능

옵션과 관련된 주의점  

언어와 관련된 부분에서 옵션을 사용한다면 DJ_ptions.Language(x)를 사용  
x에 넣은 값이 lang에 저장됨 x에는 1, 2, 3 이 들어가는데 1은 한국어 2는 일본어 3은 영어임  
ex) DJ_ptions.Language(1)인 상황에서 DJ_rule_local(lang)을 한다면 한국어 규칙이 출력됨  

문제 출제와 관련된 부분은  

def Count(x): #<- 인풋 받아서 x만큼 문제 출력한다(구현 필요)  

def Life(x): #<- 인풋 받아서 x만큼 목숨 부여한다 (구현 필요)  

가 구현된다면 활용합시다.  


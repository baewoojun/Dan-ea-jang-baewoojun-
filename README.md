# Dan-ea-jang
# 언어공부 단어장 (영, 한, 일, 한자(?))
어떤 단어에 A 대해 영어 한국어 일본어를 집어넣고 단어장에 저장 <= 단어장에서 삭제하는 기능도 필요?  
게임이 시작되면 난이도 설정 후 단어장에 있는 단어를 랜덤하게 출력  
출력된 단어를 한국어로 적어서 정답이면 점수를 + 아니면 0  
난이도 설정에 맞춰 모든 단어가 나오면 최종 점수를 기록  

=============================================================  
1. 사용되는 단어의 뜻 통일화 
2. 이미지삽입이 필요하면 확장자는 dds로  
3. 단어의 난이도에 따라 단어 분류가 필요(단어의 길이에 따라 난이도 분류?)

단어를 저장하는 클래스
public static void addWord() {
    Scanner scanner = new Scanner(System.in);

    System.out.print("단어를 입력하세요: ");
    String word = scanner.nextLine().trim().toLowerCase();

    if (wordbook.containsKey(word)) {
        System.out.println("이미 등록된 단어입니다.");
        return;
    }

    System.out.print("뜻을 입력하세요: ");
    String meaning = scanner.nextLine().trim();

    wordbook.put(word, meaning);

    System.out.println(word + "이(가) 추가되었습니다.");
}

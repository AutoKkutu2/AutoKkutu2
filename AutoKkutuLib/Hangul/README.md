# AutoKkutuLib.Hangul

한글 입력을 가상으로 시뮬레이션하는 기능이 구현된 네임스페이스입니다.

자동 입력 기능 중 '단어 입력 시뮬레이트' 옵션을 활성화했을 때, 한글 단어가 마치 키보드로 직접 친 듯이 초성-중성-종성의 순서로 입력게 하기 위한 모든 밑작업들과 분류 작업 등은 모두 여기에서 처리됩니다.

기본적으로 단어를 키보드로 친 듯이 하기 위해서는 크게 다음 2개의 준비 과정과 3단계의 실행 과정이 필요합니다.

준비 과정

1. 각 단어들의 각 글자들을 초성-중성-종성으로 나눈다. 각 부분은 '키 입력'이라 하자.
2. 만약 초성이나 종성에 자음군(쌍자음)이 있다면, 이들을 다시 두 개의 자음 '키 입력'으로 나눈다.

실행 과정

1. 지금까지 입력된 문자열, 추가로 입력할 '키'와 이의 자모 종류\(초성, 중성, 종성\)를 받는다. 지금까지 입력된 문자열의 맨 마지막 글자를 찾아, 여기에 덧붙여 입력할 수 있는 자모는 무엇인지 찾는다.
(예시: 만약 지금까지 입력된 문자열이 '안녕하세ㅇ'라면 맨 마지막 글자 'ㅇ'의 중성이 비어있기에 중성을 넣을 수 있다.)
2. 문자열의 맨 마지막 문자를 초성-중성-종성으로 분해한 뒤, 해당 자모를 넣고 다시 합성한다.
3. 만약, 현재 넣을 수 있는 자모 종류가 '종성'이고, 맨 마지막 글자의 종성이 비어있지 않으며, 현재 덧붙여 입력할 자모와 합성될어 자음군을 생성할 수 있다면, 맨 마지막 글자의 종성을 합성된 자음군으로 덮어씌운다.

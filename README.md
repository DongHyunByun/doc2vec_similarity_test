# doc2vec_similarity_test

1. **기간 : 2020.08~2020.09**

2. **기술스택 : python, gensim, konlpy(okt), pickle**

3. **내용 : doc2vec모델을 이용하여 문서의 유사도 측정**
    1. 위키피디아 데이터 다운
    2. 위키피디아의 문장을 konlpy의 okt클래스를 이용하여 형태소분해
    3. 문서별 형태소로 분해된 문장을 gensim라이브러리를 이용하여 학습
    4. 학습한 모델을 이용하여 새로운 문장의 유사도를 판단
    
4. **파일설명**
    1. 1.extract_morph  
        **[ input file : "(위키피디아 데이터)" , output file : "(숫자).p", "doc_dict.p" ]**
        - extract_morph.ipynb : 위키피다아의 문장들을 형태소 단위로 분해하고 tagged list 형식으로 바꾼 객체를 pickle형식으로 저장해주는 코드
        - extract_key.ipynb : 문서번호를 키, 문서제목을 value로 가지는 dictionary 객체를 pickle형식으로 저장해주는 코드
    2. 2.learning  
        **[ input file : test_folder/(숫자).p, output file : doc2vec_morph.model ]**
        - 1.extract_morph에서 전처리한 형태소 분해된 문장들을 학습시킨 doc2vec 모델 만들기
    3. 3.similarity_test  
        **[ input file : doc2vec_morph.model ]**
        - 2.에서 학습한 모델을 이용하여 문장의 유사도 확인
    4. model_by_class.ipynb
        - 형태소 분석을 따로하지 않고 class에서 학습하기 직전에 형태소 분해 후 바로 yield하는 코드. 시간이 오래걸

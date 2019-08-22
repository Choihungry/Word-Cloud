## Word-Cloud
### cosmos 개인 독후감을 이용한 첫 워드 클라우드 제작

![첫](https://user-images.githubusercontent.com/46768786/63535811-46a6c900-c54d-11e9-99a9-c0246a73004b.png)

~~~R
setwd("C:\\studygo")
install.packages("KoNLP")
install.packages("wordcloud")
library("KoNLP")
library("wordcloud")
library("RColorBrewer")
useSejongDic()
cosmos <- readLines("cloud.txt")
cosmos2 <- sapply(cosmos, extractNoun,USE.NAMES=F)
cosmos3 <- unlist(cosmos2)
cosmos3 <- Filter(function(x){nchar(x)>=2}, cosmos3)

 
 cosmos3 <- gsub("잘알고","",cosmos3)
 cosmos3 <- gsub("자체","",cosmos3)
 cosmos3 <- gsub("세계","",cosmos3)
 cosmos3 <- gsub("기능","",cosmos3)
 cosmos3 <- gsub("이름","",cosmos3)
 cosmos3 <- gsub("가지","",cosmos3)
 cosmos3 <- gsub("내용","",cosmos3)
 cosmos3 <- gsub("기술","",cosmos3)
 cosmos3 <- gsub("임무","",cosmos3)
 cosmos3 <- gsub("코드","",cosmos3)
 cosmos3 <- gsub("수행","",cosmos3)
 cosmos3 <- gsub("상상","",cosmos3)
 cosmos3 <- gsub("집착","",cosmos3)
 cosmos3 <- gsub("“가","",cosmos3)
 cosmos3 <- gsub("것”","",cosmos3)
 cosmos3 <- gsub("첫이였던","",cosmos3)
 cosmos3 <- gsub("다시한번","",cosmos3)
 ... 길었던 순간
 

write(unlist(cosmos3),"cloudcosmos.txt")
Gocosmos <- read.table("cloudcosmos.txt")
wordcount <- table(Gocosmos)
wordcount
library(RColorBrewer)
palete <- brewer.pal(9,"Set1") 
wordcloud(names(wordcount),freq=wordcount, scale=c(5,1), rot.per=0.1, min.freq=3, random.order=F, color=T, colors=palete)
~~~

참고 사이트
https://bigdatapy.tistory.com/6?category=855927
https://jjeongil.tistory.com/355
          


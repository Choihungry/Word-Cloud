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


### 취재기사 워드 클라우드 제작

![더뉴히어로즈](https://user-images.githubusercontent.com/46768786/63542424-4ca3a680-c55b-11e9-8065-54d54a90cc22.png)
~~~R
setwd("c:\\")
library("KoNLP")
library("wordcloud")
library("RColorBrewer")
useSejongDic()
New <- readLines("Thenew.txt")
New2 <- sapply(New, extractNoun,USE.NAMES=F)
New3 <- unlist(New2)
New3 <- Filter(function(x){nchar(x)>=2}, New3)
New3

New3 <- gsub("","",New3)


write(unlist(New3),"cloudNew.txt")
GoNew <- read.table("cloudNew.txt")
wordcount <- table(GoNew)
wordcount

library(RColorBrewer)
palete <- brewer.pal(9,"Set1") 
wordcloud(names(wordcount),freq=wordcount, scale=c(5,1), rot.per=0.1, min.freq=3, random.order=F, color=T, colors=palete)
~~~
          


# CaseStudy2DDS
title: "DDS Group Project"

author: "Cliffod Otun"

date: "8/15/2020"






#Load Libraries and Data 

library(dplyr)

library(grid)

library(ggplot2)

library(tidyr)

library(maps)

library(usmap)

library(stringr)

library(class)

library(caret)

library(Hmisc)

library(gridExtra)
library(magrittr)

library(naniar)
library(tidyverse)
library(ggthemes)


install.packages("dplyr")
install.packages("grid")
install.packages("tidyverse")
install.packages("magrittr")
install.packages("maps")
install.packages("usmap")
install.packages("stringr")
install.packages("class")
install.packages("caret")
install.packages("Hmisc")
install.packages("gridExtra")
install.packages("naniar")
install.packages("mutate")
install.packages("plot_usmap")
install.packages("ggplot2")
install.packages("ggthemes")

CaseStudy2DDS = read.csv(file.choose(),header = TRUE)
CaseStudy2DDS

ggplot(data=CaseStudy2DDS,aes(fill=Attrition))+
  geom_histogram(mapping = aes(x=HourlyRate))+
  facet_grid(Attrition~Department)

ggplot(data=CaseStudy2DDS)+
  geom_smooth(mapping=aes(x=HourlyRate,y=PercentSalaryHike, linetype=Attrition,color=Attrition))+
  ggtitle("Hourly Rate v Perent Salary Hike") + xlab("Hourly Rate")+ylab("Percent Salary Hike")

ggplot(data=CaseStudy2DDS)+
  geom_point(mapping = aes(x=HourlyRate,y=PercentSalaryHike, color=Department))+
  geom_smooth(mapping=aes(x=HourlyRate,y=PercentSalaryHike, linetype=Attrition,color=Attrition))+
  ggtitle("Hourly Rate v Perent Salary Hike") + xlab("Hourly Rate")+ylab("Percent Salary Hike")

#Transformation
CaseStudy2DDS %>% ggplot(aes(x=Department)) + geom_bar(stat="count")

CaseStudy2DDS %>% ggplot(aes(x=Attrition,fill=DistanceFromHome)) + geom_bar()+theme_excel()

# Assuming we want to keep all the employees with Job satisfaction <= 1

result = CaseStudy2DDS %>% filter(JobSatisfaction <=1)
result

# Assuming we want to keep all the Attrition with YES and Job Satisfaction <= 1
CaseStudy2DDS %>% filter(Attrition=="YES" & JobSatisfaction<=1)




CaseStudy2DDS %>% ggplot(aes(x=HourlyRate,color=Department))+ geom_freqpoly()

CaseStudy2DDS %>% ggplot(aes(y=HourlyRate,color=Department))+ geom_boxplot()
CaseStudy2DDS %>% ggplot(aes(x=DistanceFromHome,color=Attrition))+ geom_histogram()+ facet_grid(rows=vars(Attrition))


CompetitionSet = read.csv(file.choose(),header = TRUE)
CompetitionSet

NoSalary = read.csv(file.choose(),header = TRUE)
NoSalary

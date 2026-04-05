data(iris)
summary(iris)
str(iris)
table(iris$Species)

ind <- sample(2, nrow(iris), replace = TRUE, prob = c(0.7, 0.3))
trainData <- iris[ind == 1, ]
testData <- iris[ind == 2, ]

trainData1 <- trainData[,-5]
testData1 <- testData[,-5]
trainLabels <- trainData$Species
testLabels <- testData$Species

library(class)
pred <- knn(train = trainData1, test = testData1, cl = trainLabels, k = 3)

library(gmodels)

CrossTable(x = testLabels, y = pred, prop.chisq = FALSE)

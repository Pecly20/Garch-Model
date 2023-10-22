# Garch-Model
Garch Model (Cálculo de Volatilidade)

Utiliza os pacotes fGarch 
(getwd())

install.packages('readxl')
library(readxl)

install.packages('fGarch')
library(fGarch)

setwd("/")

Retornos<-read_excel("Retornos.xlsx", sheet="Planilha1")

head(Retornos)
summary(Retornos)

var(Retornos)

fit=garchFit(~ garch(1,1), cond.dist = "norm", data=Retornos)

summary(fit)

volatility=volatility(fit, type="sigma")
head(volatility)
class(volatility)

options(max.print=2000)
volatility

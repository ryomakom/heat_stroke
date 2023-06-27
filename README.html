---
title: "朝日新聞の熱中症分析について"
output: html_notebook
date: 2023/6/27
author: 朝日新聞デジタル企画報道部　小宮山亮磨 @ryomakom
---


朝日新聞は6月27日の朝刊で（デジタル版では26日夜に）、「熱中症、涼しい地域ほど注意　暑さ慣れず、同じ35度でも搬送2倍」との[記事を掲載した](https://digital.asahi.com/articles/ASR6V5TRJR6FULBH00D.html)。東京大の橋爪真弘教授（疫学）に監修してもらいながら、熱中症搬送数と気温との関係を、科学みらい部の市野塊記者と小宮山が分析した。

この文書では、どこからどんなデータを持ってきて、どのように分析したか、Rのコードとともに説明する。

## 必要なパッケージ読み込み

tidyverseとかlubridateといったあたりは定番選手。modelsummary以下の三つは（たしか）回帰分析のためのパッケージ。

```{r}
library(tidyverse)
library(readxl)
library(lubridate)
library(modelsummary)
library(leaps)
library(MASS)
```


## 熱中症の搬送数データ

総務省消防庁の[ウェブサイト](https://www.fdma.go.jp/disaster/heatstroke/post4.html)にあるデータを読み込んで整形する。データは熱中症で運ばれた人の都道府県別、日別の合計人数のほか、搬送者の年齢、症状の重さ、発生場所の内訳の数字がある。なお、発生場所の内訳が記録があるのは2017年以降のみ。

```{r}
hs08 <- bind_rows(read_xlsx("data/hs/heatstroke003_data_h20.xlsx",sheet=1),
                  read_xlsx("data/hs/heatstroke003_data_h20.xlsx",sheet=2),
                  read_xlsx("data/hs/heatstroke003_data_h20.xlsx",sheet=3))

hs09 <- bind_rows(read_xlsx("data/hs/heatstroke003_data_h21.xlsx",sheet=1),
                  read_xlsx("data/hs/heatstroke003_data_h21.xlsx",sheet=2),
                  read_xlsx("data/hs/heatstroke003_data_h21.xlsx",sheet=3))

hs10 <- bind_rows(read_xlsx("data/hs/heatstroke003_data_h22.xlsx",sheet=1),
                  read_xlsx("data/hs/heatstroke003_data_h22.xlsx",sheet=2),
                  read_xlsx("data/hs/heatstroke003_data_h22.xlsx",sheet=3),
                  read_xlsx("data/hs/heatstroke003_data_h22.xlsx",sheet=4))

hs11 <- bind_rows(read_xlsx("data/hs/heatstroke003_data_h23.xlsx",sheet=1),
                  read_xlsx("data/hs/heatstroke003_data_h23.xlsx",sheet=2),
                  read_xlsx("data/hs/heatstroke003_data_h23.xlsx",sheet=3),
                  read_xlsx("data/hs/heatstroke003_data_h23.xlsx",sheet=4))

hs12 <- bind_rows(read_xlsx("data/hs/heatstroke003_data_h24.xlsx",sheet=1),
                  read_xlsx("data/hs/heatstroke003_data_h24.xlsx",sheet=2),
                  read_xlsx("data/hs/heatstroke003_data_h24.xlsx",sheet=3),
                  read_xlsx("data/hs/heatstroke003_data_h24.xlsx",sheet=4))

hs13 <- bind_rows(read_xlsx("data/hs/heatstroke003_data_h25.xlsx",sheet=1),
                  read_xlsx("data/hs/heatstroke003_data_h25.xlsx",sheet=2),
                  read_xlsx("data/hs/heatstroke003_data_h25.xlsx",sheet=3),
                  read_xlsx("data/hs/heatstroke003_data_h25.xlsx",sheet=4))

hs14 <- bind_rows(read_xlsx("data/hs/heatstroke003_data_h26.xlsx",sheet=1),
                  read_xlsx("data/hs/heatstroke003_data_h26.xlsx",sheet=2),
                  read_xlsx("data/hs/heatstroke003_data_h26.xlsx",sheet=3),
                  read_xlsx("data/hs/heatstroke003_data_h26.xlsx",sheet=4))

hs15 <- bind_rows(read_xlsx("data/hs/heatstroke003_data_h27.xlsx",sheet=1),
                  read_xlsx("data/hs/heatstroke003_data_h27.xlsx",sheet=2),
                  read_xlsx("data/hs/heatstroke003_data_h27.xlsx",sheet=3),
                  read_xlsx("data/hs/heatstroke003_data_h27.xlsx",sheet=4),
                  read_xlsx("data/hs/heatstroke003_data_h27.xlsx",sheet=5))

hs16 <- bind_rows(read_xlsx("data/hs/heatstroke003_data_h28.xlsx",sheet=1),
                  read_xlsx("data/hs/heatstroke003_data_h28.xlsx",sheet=2),
                  read_xlsx("data/hs/heatstroke003_data_h28.xlsx",sheet=3),
                  read_xlsx("data/hs/heatstroke003_data_h28.xlsx",sheet=4),
                  read_xlsx("data/hs/heatstroke003_data_h28.xlsx",sheet=5))

# この年以降に発生場所の情報が加わる
hs17 <- bind_rows(read_xlsx("data/hs/heatstroke003_data_h29.xlsx",sheet=1),
                  read_xlsx("data/hs/heatstroke003_data_h29.xlsx",sheet=2),
                  read_xlsx("data/hs/heatstroke003_data_h29.xlsx",sheet=3),
                  read_xlsx("data/hs/heatstroke003_data_h29.xlsx",sheet=4),
                  read_xlsx("data/hs/heatstroke003_data_h29.xlsx",sheet=5))

hs18 <- bind_rows(read_xlsx("data/hs/heatstroke003_data_h30.xlsx",sheet=1),
                  read_xlsx("data/hs/heatstroke003_data_h30.xlsx",sheet=2),
                  read_xlsx("data/hs/heatstroke003_data_h30.xlsx",sheet=3),
                  read_xlsx("data/hs/heatstroke003_data_h30.xlsx",sheet=4),
                  read_xlsx("data/hs/heatstroke003_data_h30.xlsx",sheet=5))

hs19 <- bind_rows(read_xlsx("data/hs/heatstroke003_data_r1.xlsx",sheet=1),
                  read_xlsx("data/hs/heatstroke003_data_r1.xlsx",sheet=2),
                  read_xlsx("data/hs/heatstroke003_data_r1.xlsx",sheet=3),
                  read_xlsx("data/hs/heatstroke003_data_r1.xlsx",sheet=4),
                  read_xlsx("data/hs/heatstroke003_data_r1.xlsx",sheet=5))

hs20 <- bind_rows(read_xlsx("data/hs/heatstroke003_data_r2.xlsx",sheet=1),
                  read_xlsx("data/hs/heatstroke003_data_r2.xlsx",sheet=2),
                  read_xlsx("data/hs/heatstroke003_data_r2.xlsx",sheet=3),
                  read_xlsx("data/hs/heatstroke003_data_r2.xlsx",sheet=4))

hs21 <- bind_rows(read_xlsx("data/hs/heatstroke003_data_r3.xlsx",sheet=1),
                  read_xlsx("data/hs/heatstroke003_data_r3.xlsx",sheet=2),
                  read_xlsx("data/hs/heatstroke003_data_r3.xlsx",sheet=3),
                  read_xlsx("data/hs/heatstroke003_data_r3.xlsx",sheet=4),
                  read_xlsx("data/hs/heatstroke003_data_r3.xlsx",sheet=5))

hs22 <- bind_rows(read_xlsx("data/hs/heatstroke003_data_r4.xlsx",sheet=1),
                  read_xlsx("data/hs/heatstroke003_data_r4.xlsx",sheet=2),
                  read_xlsx("data/hs/heatstroke003_data_r4.xlsx",sheet=3),
                  read_xlsx("data/hs/heatstroke003_data_r4.xlsx",sheet=4),
                  read_xlsx("data/hs/heatstroke003_data_r4.xlsx",sheet=5))

hs <- bind_rows(hs08,
                hs09,
                hs10,
                hs11,
                hs12,
                hs13,
                hs14,
                hs15,
                hs16,
                hs17,
                hs18,
                hs19,
                hs20,
                hs21,
                hs22)

hs[is.na(hs)] <- 0

hs <- hs %>% 
  rename(date=日付,
         prefID=都道府県コード,
         cases=`搬送人員（計）`,
         age_newborn=`年齢区分：新生児`,
         age_infant=`年齢区分：乳幼児`,
         age_youth=`年齢区分：少年`,
         age_adult=`年齢区分：成人`,
         age_elder=`年齢区分：高齢者`,
         age_unknown=`年齢区分：不明`,
         severity_dead=`傷病程度：死亡`,
         severity_serious=`傷病程度：重症`,
         severity_moderate=`傷病程度：中等症`,
         severity_mild=`傷病程度：軽症`,
         severity_other=`傷病程度：その他`,
         place_house=`発生場所：住居`,
         place_work1=`発生場所：仕事場①`,
         place_work2=`発生場所：仕事場②`,
         place_school=`発生場所：教育機関`,
         place_public_inside=`発生場所：公衆(屋内)`,
         place_public_outside=`発生場所：公衆(屋外)`,
         place_road=`発生場所：道路`,
         place_other=`発生場所：その他`) %>% 
  mutate(date=as.Date(date)) %>% 
  left_join(read_csv("data/pref.csv")) %>% 
  mutate(year=as.double(year(date)),month=as.double(month(date)))

```

```{r}
hs
```

## 気温データを読み込む

各都道府県庁所在地における5～9月の日ごと最高気温と平均気温のデータを読み込んで整形する。出典は[気象庁](https://www.data.jma.go.jp/obd/stats/etrn/)。

```{r}


climate <- bind_rows(read_csv("data/climate/hokkaido.csv",
                              skip=3,
                              locale = locale(encoding = "shift-jis"))[,c(1,2,5,8)] %>%
                       filter(!is.na(年月日)) %>%
                       mutate(pref="北海道",
                              date=as.Date(年月日),
                              max_temp=`最高気温(℃)...2`,
                              avg_temp=`平均気温(℃)...5` ,
                              humidity=`平均湿度(％)...8`) %>%
                       select(pref,date,max_temp,avg_temp,humidity),
                     read_csv("data/climate/aomori.csv",
                              skip=3,
                              locale = locale(encoding = "shift-jis"))[,c(1,2,5,8)] %>%
                       filter(!is.na(年月日)) %>%
                       mutate(pref="青森県",
                              date=as.Date(年月日),
                              max_temp=`最高気温(℃)...2`,
                              avg_temp=`平均気温(℃)...5` ,
                              humidity=`平均湿度(％)...8`) %>%
                       select(pref,date,max_temp,avg_temp,humidity),                    
                     read_csv("data/climate/iwate.csv",
                              skip=3,
                              locale = locale(encoding = "shift-jis"))[,c(1,2,5,8)] %>%
                       filter(!is.na(年月日)) %>%
                       mutate(pref="岩手県",
                              date=as.Date(年月日),
                              max_temp=`最高気温(℃)...2`,
                              avg_temp=`平均気温(℃)...5` ,
                              humidity=`平均湿度(％)...8`) %>%
                       select(pref,date,max_temp,avg_temp,humidity),
                     read_csv("data/climate/miyagi.csv",
                              skip=3,
                              locale = locale(encoding = "shift-jis"))[,c(1,2,5,8)] %>%
                       filter(!is.na(年月日)) %>%
                       mutate(pref="宮城県",
                              date=as.Date(年月日),
                              max_temp=`最高気温(℃)...2`,
                              avg_temp=`平均気温(℃)...5` ,
                              humidity=`平均湿度(％)...8`) %>%
                       select(pref,date,max_temp,avg_temp,humidity),
                     read_csv("data/climate/akita.csv",
                              skip=3,
                              locale = locale(encoding = "shift-jis"))[,c(1,2,5,8)] %>%
                       filter(!is.na(年月日)) %>%
                       mutate(pref="秋田県",
                              date=as.Date(年月日),
                              max_temp=`最高気温(℃)...2`,
                              avg_temp=`平均気温(℃)...5` ,
                              humidity=`平均湿度(％)...8`) %>%
                       select(pref,date,max_temp,avg_temp,humidity),
                     read_csv("data/climate/yamagata.csv",
                              skip=3,
                              locale = locale(encoding = "shift-jis"))[,c(1,2,5,8)] %>%
                       filter(!is.na(年月日)) %>%
                       mutate(pref="山形県",
                              date=as.Date(年月日),
                              max_temp=`最高気温(℃)...2`,
                              avg_temp=`平均気温(℃)...5` ,
                              humidity=`平均湿度(％)...8`) %>%
                       select(pref,date,max_temp,avg_temp,humidity),
                     read_csv("data/climate/fukushima.csv",
                              skip=3,
                              locale = locale(encoding = "shift-jis"))[,c(1,2,5,8)] %>%
                       filter(!is.na(年月日)) %>%
                       mutate(pref="福島県",
                              date=as.Date(年月日),
                              max_temp=`最高気温(℃)...2`,
                              avg_temp=`平均気温(℃)...5` ,
                              humidity=`平均湿度(％)...8`) %>%
                       select(pref,date,max_temp,avg_temp,humidity),
                     read_csv("data/climate/ibaraki.csv",
                              skip=3,
                              locale = locale(encoding = "shift-jis"))[,c(1,2,5,8)] %>%
                       filter(!is.na(年月日)) %>%
                       mutate(pref="茨城県",
                              date=as.Date(年月日),
                              max_temp=`最高気温(℃)...2`,
                              avg_temp=`平均気温(℃)...5` ,
                              humidity=`平均湿度(％)...8`) %>%
                       select(pref,date,max_temp,avg_temp,humidity),
                     read_csv("data/climate/tochigi.csv",
                              skip=3,
                              locale = locale(encoding = "shift-jis"))[,c(1,2,5,8)] %>%
                       filter(!is.na(年月日)) %>%
                       mutate(pref="栃木県",
                              date=as.Date(年月日),
                              max_temp=`最高気温(℃)...2`,
                              avg_temp=`平均気温(℃)...5` ,
                              humidity=`平均湿度(％)...8`) %>%
                       select(pref,date,max_temp,avg_temp,humidity),
                     read_csv("data/climate/gunma.csv",
                              skip=3,
                              locale = locale(encoding = "shift-jis"))[,c(1,2,5,8)] %>%
                       filter(!is.na(年月日)) %>%
                       mutate(pref="群馬県",
                              date=as.Date(年月日),
                              max_temp=`最高気温(℃)...2`,
                              avg_temp=`平均気温(℃)...5` ,
                              humidity=`平均湿度(％)...8`) %>%
                       select(pref,date,max_temp,avg_temp,humidity),
                     read_csv("data/climate/saitama.csv",
                              skip=3,
                              locale = locale(encoding = "shift-jis"))[,c(1,2,5,8)] %>%
                       filter(!is.na(年月日)) %>%
                       mutate(pref="埼玉県",
                              date=as.Date(年月日),
                              max_temp=`最高気温(℃)...2`,
                              avg_temp=`平均気温(℃)...5` ,
                              humidity=`平均湿度(％)...8`) %>%
                       select(pref,date,max_temp,avg_temp,humidity),
                     read_csv("data/climate/chiba.csv",
                              skip=3,
                              locale = locale(encoding = "shift-jis"))[,c(1,2,5,8)] %>%
                       filter(!is.na(年月日)) %>%
                       mutate(pref="千葉県",
                              date=as.Date(年月日),
                              max_temp=`最高気温(℃)...2`,
                              avg_temp=`平均気温(℃)...5` ,
                              humidity=`平均湿度(％)...8`) %>%
                       select(pref,date,max_temp,avg_temp,humidity),
                     read_csv("data/climate/tokyo.csv",
                              skip=3,
                              locale = locale(encoding = "shift-jis"))[,c(1,2,5,8)] %>%
                       filter(!is.na(年月日)) %>%
                       mutate(pref="東京都",
                              date=as.Date(年月日),
                              max_temp=`最高気温(℃)...2`,
                              avg_temp=`平均気温(℃)...5` ,
                              humidity=`平均湿度(％)...8`) %>%
                       select(pref,date,max_temp,avg_temp,humidity),
                     read_csv("data/climate/kanagawa.csv",
                              skip=3,
                              locale = locale(encoding = "shift-jis"))[,c(1,2,5,8)] %>%
                       filter(!is.na(年月日)) %>%
                       mutate(pref="神奈川県",
                              date=as.Date(年月日),
                              max_temp=`最高気温(℃)...2`,
                              avg_temp=`平均気温(℃)...5` ,
                              humidity=`平均湿度(％)...8`) %>%
                       select(pref,date,max_temp,avg_temp,humidity),
                     read_csv("data/climate/niigata.csv",
                              skip=3,
                              locale = locale(encoding = "shift-jis"))[,c(1,2,5,8)] %>%
                       filter(!is.na(年月日)) %>%
                       mutate(pref="新潟県",
                              date=as.Date(年月日),
                              max_temp=`最高気温(℃)...2`,
                              avg_temp=`平均気温(℃)...5` ,
                              humidity=`平均湿度(％)...8`) %>%
                       select(pref,date,max_temp,avg_temp,humidity),
                     read_csv("data/climate/toyama.csv",
                              skip=3,
                              locale = locale(encoding = "shift-jis"))[,c(1,2,5,8)] %>%
                       filter(!is.na(年月日)) %>%
                       mutate(pref="富山県",
                              date=as.Date(年月日),
                              max_temp=`最高気温(℃)...2`,
                              avg_temp=`平均気温(℃)...5` ,
                              humidity=`平均湿度(％)...8`) %>%
                       select(pref,date,max_temp,avg_temp,humidity),
                     read_csv("data/climate/ishikawa.csv", 
                              skip=3,
                              locale = locale(encoding = "shift-jis"))[,c(1,2,5,8)] %>%
                       filter(!is.na(年月日)) %>%
                       mutate(pref="石川県",
                              date=as.Date(年月日),
                              max_temp=`最高気温(℃)...2`,
                              avg_temp=`平均気温(℃)...5` ,
                              humidity=`平均湿度(％)...8`) %>%
                       select(pref,date,max_temp,avg_temp,humidity),
                     read_csv("data/climate/fukui.csv",
                              skip=3,
                              locale = locale(encoding = "shift-jis"))[,c(1,2,5,8)] %>%
                       filter(!is.na(年月日)) %>%
                       mutate(pref="福井県",
                              date=as.Date(年月日),
                              max_temp=`最高気温(℃)...2`,
                              avg_temp=`平均気温(℃)...5` ,
                              humidity=`平均湿度(％)...8`) %>%
                       select(pref,date,max_temp,avg_temp,humidity),
                     read_csv("data/climate/yamanashi.csv",
                              skip=3,
                              locale = locale(encoding = "shift-jis"))[,c(1,2,5,8)] %>%
                       filter(!is.na(年月日)) %>%
                       mutate(pref="山梨県",
                              date=as.Date(年月日),
                              max_temp=`最高気温(℃)...2`,
                              avg_temp=`平均気温(℃)...5` ,
                              humidity=`平均湿度(％)...8`) %>%
                       select(pref,date,max_temp,avg_temp,humidity),
                     read_csv("data/climate/nagano.csv", 
                              skip=3,
                              locale = locale(encoding = "shift-jis"))[,c(1,2,5,8)] %>%
                       filter(!is.na(年月日)) %>%
                       mutate(pref="長野県",
                              date=as.Date(年月日),
                              max_temp=`最高気温(℃)...2`,
                              avg_temp=`平均気温(℃)...5` ,
                              humidity=`平均湿度(％)...8`) %>%
                       select(pref,date,max_temp,avg_temp,humidity),
                     read_csv("data/climate/gifu.csv",
                              skip=3,
                              locale = locale(encoding = "shift-jis"))[,c(1,2,5,8)] %>%
                       filter(!is.na(年月日)) %>%
                       mutate(pref="岐阜県",
                              date=as.Date(年月日),
                              max_temp=`最高気温(℃)...2`,
                              avg_temp=`平均気温(℃)...5` ,
                              humidity=`平均湿度(％)...8`) %>%
                       select(pref,date,max_temp,avg_temp,humidity),
                     read_csv("data/climate/shizuoka.csv",
                              skip=3,
                              locale = locale(encoding = "shift-jis"))[,c(1,2,5,8)] %>%
                       filter(!is.na(年月日)) %>%
                       mutate(pref="静岡県",
                              date=as.Date(年月日),
                              max_temp=`最高気温(℃)...2`,
                              avg_temp=`平均気温(℃)...5` ,
                              humidity=`平均湿度(％)...8`) %>%
                       select(pref,date,max_temp,avg_temp,humidity),
                     read_csv("data/climate/aichi.csv",
                              skip=3,
                              locale = locale(encoding = "shift-jis"))[,c(1,2,5,8)] %>%
                       filter(!is.na(年月日)) %>%
                       mutate(pref="愛知県",
                              date=as.Date(年月日),
                              max_temp=`最高気温(℃)...2`,
                              avg_temp=`平均気温(℃)...5` ,
                              humidity=`平均湿度(％)...8`) %>%
                       select(pref,date,max_temp,avg_temp,humidity),
                     read_csv("data/climate/mie.csv",
                              skip=3,
                              locale = locale(encoding = "shift-jis"))[,c(1,2,5,8)] %>%
                       filter(!is.na(年月日)) %>%
                       mutate(pref="三重県",
                              date=as.Date(年月日),
                              max_temp=`最高気温(℃)...2`,
                              avg_temp=`平均気温(℃)...5` ,
                              humidity=`平均湿度(％)...8`) %>%
                       select(pref,date,max_temp,avg_temp,humidity),                  
                     read_csv("data/climate/shiga.csv",
                              skip=3,
                              locale = locale(encoding = "shift-jis"))[,c(1,2,5,8)] %>%
                       filter(!is.na(年月日)) %>%
                       mutate(pref="滋賀県",
                              date=as.Date(年月日),
                              max_temp=`最高気温(℃)...2`,
                              avg_temp=`平均気温(℃)...5` ,
                              humidity=`平均湿度(％)...8`) %>%
                       select(pref,date,max_temp,avg_temp,humidity),
                     read_csv("data/climate/kyoto.csv",
                              skip=3,
                              locale = locale(encoding = "shift-jis"))[,c(1,2,5,8)] %>%
                       filter(!is.na(年月日)) %>%
                       mutate(pref="京都府",
                              date=as.Date(年月日),
                              max_temp=`最高気温(℃)...2`,
                              avg_temp=`平均気温(℃)...5` ,
                              humidity=`平均湿度(％)...8`) %>%
                       select(pref,date,max_temp,avg_temp,humidity),
                     read_csv("data/climate/osaka.csv",
                              skip=3,
                              locale = locale(encoding = "shift-jis"))[,c(1,2,5,8)] %>%
                       filter(!is.na(年月日)) %>%
                       mutate(pref="大阪府",
                              date=as.Date(年月日),
                              max_temp=`最高気温(℃)...2`,
                              avg_temp=`平均気温(℃)...5` ,
                              humidity=`平均湿度(％)...8`) %>%
                       select(pref,date,max_temp,avg_temp,humidity),
                     read_csv("data/climate/hyogo.csv",
                              skip=3,
                              locale = locale(encoding = "shift-jis"))[,c(1,2,5,8)] %>%
                       filter(!is.na(年月日)) %>%
                       mutate(pref="兵庫県",
                              date=as.Date(年月日),
                              max_temp=`最高気温(℃)...2`,
                              avg_temp=`平均気温(℃)...5` ,
                              humidity=`平均湿度(％)...8`) %>%
                       select(pref,date,max_temp,avg_temp,humidity),
                     read_csv("data/climate/nara.csv",
                              skip=3,
                              locale = locale(encoding = "shift-jis"))[,c(1,2,5,8)] %>%
                       filter(!is.na(年月日)) %>%
                       mutate(pref="奈良県",
                              date=as.Date(年月日),
                              max_temp=`最高気温(℃)...2`,
                              avg_temp=`平均気温(℃)...5` ,
                              humidity=`平均湿度(％)...8`) %>%
                       select(pref,date,max_temp,avg_temp,humidity),
                     read_csv("data/climate/wakayama.csv",
                              skip=3,
                              locale = locale(encoding = "shift-jis"))[,c(1,2,5,8)] %>%
                       filter(!is.na(年月日)) %>%
                       mutate(pref="和歌山県",
                              date=as.Date(年月日),
                              max_temp=`最高気温(℃)...2`,
                              avg_temp=`平均気温(℃)...5` ,
                              humidity=`平均湿度(％)...8`) %>%
                       select(pref,date,max_temp,avg_temp,humidity),
                     read_csv("data/climate/tottori.csv",
                              skip=3,
                              locale = locale(encoding = "shift-jis"))[,c(1,2,5,8)] %>%
                       filter(!is.na(年月日)) %>%
                       mutate(pref="鳥取県",
                              date=as.Date(年月日),
                              max_temp=`最高気温(℃)...2`,
                              avg_temp=`平均気温(℃)...5` ,
                              humidity=`平均湿度(％)...8`) %>%
                       select(pref,date,max_temp,avg_temp,humidity),
                     read_csv("data/climate/shimane.csv",
                              skip=3,
                              locale = locale(encoding = "shift-jis"))[,c(1,2,5,8)] %>%
                       filter(!is.na(年月日)) %>%
                       mutate(pref="島根県",
                              date=as.Date(年月日),
                              max_temp=`最高気温(℃)...2`,
                              avg_temp=`平均気温(℃)...5` ,
                              humidity=`平均湿度(％)...8`) %>%
                       select(pref,date,max_temp,avg_temp,humidity),
                     read_csv("data/climate/okayama.csv",
                              skip=3,
                              locale = locale(encoding = "shift-jis"))[,c(1,2,5,8)] %>%
                       filter(!is.na(年月日)) %>%
                       mutate(pref="岡山県",
                              date=as.Date(年月日),
                              max_temp=`最高気温(℃)...2`,
                              avg_temp=`平均気温(℃)...5` ,
                              humidity=`平均湿度(％)...8`) %>%
                       select(pref,date,max_temp,avg_temp,humidity),
                     read_csv("data/climate/hiroshima.csv",
                              skip=3,
                              locale = locale(encoding = "shift-jis"))[,c(1,2,5,8)] %>%
                       filter(!is.na(年月日)) %>%
                       mutate(pref="広島県",
                              date=as.Date(年月日),
                              max_temp=`最高気温(℃)...2`,
                              avg_temp=`平均気温(℃)...5` ,
                              humidity=`平均湿度(％)...8`) %>%
                       select(pref,date,max_temp,avg_temp,humidity),
                     read_csv("data/climate/yamaguchi.csv",
                              skip=3,
                              locale = locale(encoding = "shift-jis"))[,c(1,2,5,8)] %>%
                       filter(!is.na(年月日)) %>%
                       mutate(pref="山口県",
                              date=as.Date(年月日),
                              max_temp=`最高気温(℃)...2`,
                              avg_temp=`平均気温(℃)...5` ,
                              humidity=`平均湿度(％)...8`) %>%
                       select(pref,date,max_temp,avg_temp,humidity),
                     read_csv("data/climate/tokushima.csv", 
                              skip=3,
                              locale = locale(encoding = "shift-jis"))[,c(1,2,5,8)] %>%
                       filter(!is.na(年月日)) %>%
                       mutate(pref="徳島県",
                              date=as.Date(年月日),
                              max_temp=`最高気温(℃)...2`,
                              avg_temp=`平均気温(℃)...5` ,
                              humidity=`平均湿度(％)...8`) %>%
                       select(pref,date,max_temp,avg_temp,humidity),
                     read_csv("data/climate/kagawa.csv",
                              skip=3,
                              locale = locale(encoding = "shift-jis"))[,c(1,2,5,8)] %>%
                       filter(!is.na(年月日)) %>%
                       mutate(pref="香川県",
                              date=as.Date(年月日),
                              max_temp=`最高気温(℃)...2`,
                              avg_temp=`平均気温(℃)...5` ,
                              humidity=`平均湿度(％)...8`) %>%
                       select(pref,date,max_temp,avg_temp,humidity),
                     read_csv("data/climate/ehime.csv",
                              skip=3,
                              locale = locale(encoding = "shift-jis"))[,c(1,2,5,8)] %>%
                       filter(!is.na(年月日)) %>%
                       mutate(pref="愛媛県",
                              date=as.Date(年月日),
                              max_temp=`最高気温(℃)...2`,
                              avg_temp=`平均気温(℃)...5` ,
                              humidity=`平均湿度(％)...8`) %>%
                       select(pref,date,max_temp,avg_temp,humidity),
                     read_csv("data/climate/kochi.csv",
                              skip=3,
                              locale = locale(encoding = "shift-jis"))[,c(1,2,5,8)] %>%
                       filter(!is.na(年月日)) %>%
                       mutate(pref="高知県",
                              date=as.Date(年月日),
                              max_temp=`最高気温(℃)...2`,
                              avg_temp=`平均気温(℃)...5` ,
                              humidity=`平均湿度(％)...8`) %>%
                       select(pref,date,max_temp,avg_temp,humidity),
                     read_csv("data/climate/fukuoka.csv",
                              skip=3,
                              locale = locale(encoding = "shift-jis"))[,c(1,2,5,8)] %>%
                       filter(!is.na(年月日)) %>%
                       mutate(pref="福岡県",
                              date=as.Date(年月日),
                              max_temp=`最高気温(℃)...2`,
                              avg_temp=`平均気温(℃)...5` ,
                              humidity=`平均湿度(％)...8`) %>%
                       select(pref,date,max_temp,avg_temp,humidity),
                     read_csv("data/climate/saga.csv",
                              skip=3,
                              locale = locale(encoding = "shift-jis"))[,c(1,2,5,8)] %>%
                       filter(!is.na(年月日)) %>%
                       mutate(pref="佐賀県",
                              date=as.Date(年月日),
                              max_temp=`最高気温(℃)...2`,
                              avg_temp=`平均気温(℃)...5` ,
                              humidity=`平均湿度(％)...8`) %>%
                       select(pref,date,max_temp,avg_temp,humidity),
                     read_csv("data/climate/nagasaki.csv",
                              skip=3,
                              locale = locale(encoding = "shift-jis"))[,c(1,2,5,8)] %>%
                       filter(!is.na(年月日)) %>%
                       mutate(pref="長崎県",
                              date=as.Date(年月日),
                              max_temp=`最高気温(℃)...2`,
                              avg_temp=`平均気温(℃)...5` ,
                              humidity=`平均湿度(％)...8`) %>%
                       select(pref,date,max_temp,avg_temp,humidity),
                     read_csv("data/climate/kumamoto.csv",
                              skip=3,
                              locale = locale(encoding = "shift-jis"))[,c(1,2,5,8)] %>%
                       filter(!is.na(年月日)) %>%
                       mutate(pref="熊本県",
                              date=as.Date(年月日),
                              max_temp=`最高気温(℃)...2`,
                              avg_temp=`平均気温(℃)...5` ,
                              humidity=`平均湿度(％)...8`) %>%
                       select(pref,date,max_temp,avg_temp,humidity),
                     read_csv("data/climate/oita.csv",
                              skip=3,
                              locale = locale(encoding = "shift-jis"))[,c(1,2,5,8)] %>%
                       filter(!is.na(年月日)) %>%
                       mutate(pref="大分県",
                              date=as.Date(年月日),
                              max_temp=`最高気温(℃)...2`,
                              avg_temp=`平均気温(℃)...5` ,
                              humidity=`平均湿度(％)...8`) %>%
                       select(pref,date,max_temp,avg_temp,humidity), 
                     read_csv("data/climate/miyazaki.csv",
                              skip=3,
                              locale = locale(encoding = "shift-jis"))[,c(1,2,5,8)] %>%
                       filter(!is.na(年月日)) %>%
                       mutate(pref="宮崎県",
                              date=as.Date(年月日),
                              max_temp=`最高気温(℃)...2`,
                              avg_temp=`平均気温(℃)...5` ,
                              humidity=`平均湿度(％)...8`) %>%
                       select(pref,date,max_temp,avg_temp,humidity),
                     read_csv("data/climate/kagoshima.csv",
                              skip=3,
                              locale = locale(encoding = "shift-jis"))[,c(1,2,5,8)] %>%
                       filter(!is.na(年月日)) %>%
                       mutate(pref="鹿児島県",
                              date=as.Date(年月日),
                              max_temp=`最高気温(℃)...2`,
                              avg_temp=`平均気温(℃)...5` ,
                              humidity=`平均湿度(％)...8`) %>%
                       select(pref,date,max_temp,avg_temp,humidity),
                     read_csv("data/climate/okinawa.csv",
                              skip=3,
                              locale = locale(encoding = "shift-jis"))[,c(1,2,5,8)] %>%
                       filter(!is.na(年月日)) %>%
                       mutate(pref="沖縄県",
                              date=as.Date(年月日),
                              max_temp=`最高気温(℃)...2`,
                              avg_temp=`平均気温(℃)...5` ,
                              humidity=`平均湿度(％)...8`) %>%
                       select(pref,date,max_temp,avg_temp,humidity)) %>% 
  mutate(year=as.double(year(date)),month=as.double(month(date)))

```

```{r}
climate
```

## いよいよ分析

夏（5～9月）の平均気温を都道府県別に計算する。今回は2020年以降の3年間にしぼった。

```{r}
avg_temp_summer <- climate %>%
  filter(as.double(year(date))>=2020) %>%
  group_by(pref) %>%
  summarize(avg_temp_summer=mean(avg_temp)) %>%
  left_join(read_csv("data/pref.csv")) %>%
  arrange(prefID)

```

```{r}
avg_temp_summer
```

## 最高気温と搬送数の関係をグラフにする

各地の日別最高気温と熱中症搬送数の関係をグラフにする。平均気温が①22度以下の涼しい地域②22～23度のやや涼しい地域③23度超の涼しくはない地域、の3パターンに分けて描く。

1つめのグラフは散布図で、2つめはその近似曲線。

```{r}
hs %>%
  mutate(year2=ifelse(year<2010,2005,
               ifelse(year<2015,2010,
               ifelse(year<2020,2015,2020)))) %>% # 5年ごとに行われる国勢調査の人口データを突合する「基準年」を決める
  left_join(read_csv("data/population.csv")) %>% # 国勢調査の都道府県別人口データを突合する
  left_join(climate) %>%  # 気温データを突合する
  left_join(avg_temp_summer) %>%  # 夏場の平均気温データを突合する
  mutate(cases_pop=100000*cases/population) %>%  # 人口10万人あたりの搬送数を計算する
  mutate(夏場の平均気温=ifelse(avg_temp_summer>23,"23度超",
                        ifelse(avg_temp_summer>22,"23~22度",
                        ifelse(avg_temp_summer<=22,"22度以下",NA)))) %>%
  ggplot(aes(max_temp,cases_pop,color=夏場の平均気温)) +
  geom_point(alpha=.5) +
  labs(title="人口１０万人あたりの搬送件数と日別最高気温の関係",
       x="その日の最高気温（度）",
       y="救急搬送数（人口10万人当たり）")


hs %>%
  mutate(year2=ifelse(year<2010,2005,
               ifelse(year<2015,2010,
               ifelse(year<2020,2015,2020)))) %>%
  left_join(read_csv("data/population.csv")) %>%
  left_join(climate) %>%
  left_join(avg_temp_summer) %>%
  mutate(cases_pop=100000*cases/population) %>%
  mutate(夏場の平均気温=ifelse(avg_temp_summer>23,"23度超",
                        ifelse(avg_temp_summer>22,"23~22度",
                        ifelse(avg_temp_summer<=22,"22度以下",NA)))) %>%
  ggplot(aes(max_temp,cases_pop,color=夏場の平均気温)) +
  geom_smooth(method="gam",se=FALSE) +
  labs(title="人口１０万人あたりの搬送件数と日別最高気温の関係",
       subtitle="一般化加法モデルによる近似曲線",
       x="その日の最高気温（度）",
       y="救急搬送数（人口10万人当たり）")

```

## 以下は予備的にやった分析

涼しい地域ほど搬送数が増えやすいというのは、私たちが始めから知っていたことではなく、以下のような分析をしたら分かったこと。

搬送数の増減にどんな要素が効いているのかを知るため、もっとも当てはまりの良い重回帰分析のモデルをステップワイズ法で探した。説明変数の候補として、都道府県別の気温や平均収入、ジニ係数、エアコン保有台数などを用意した。目的変数としては、搬送数の合計だけではなく、搬送者の年齢や発生場所などに分けた件数も検討した。

```{r}
regs <- list()
indices <- c(3:8, 10:22)

for (i in indices) {
x <- colnames(hs)[i]
modelname <- paste0("model_",x)

hs_analysis <- hs %>%
  rename(x=x) %>% 
  mutate(year=year(date)) %>%
  filter(year %in% c("2018","2019","2020","2021","2022")) %>%
  group_by(date,pref) %>%
  summarize(x=sum(x)) %>%
  left_join(read_csv("data/population2020.csv")) %>%
  mutate(x_pop=x*100000/population2020) %>%
  mutate(rate_elder=over65/population2020) %>%
  left_join(read_csv("data/variables3.csv")) %>% 
  left_join(climate %>% dplyr::select(pref,date,max_temp,humidity)) %>% 
  ungroup() %>% 
  dplyr::select(-date,-pref) %>% 
  scale() %>% 
  as_tibble()

hs_analysis <- hs_analysis[,6:23] %>% 
  na.omit()

full_model <- lm(x_pop ~., data = hs_analysis)

step_model <- full_model %>%
  stepAIC(direction = "both", trace = TRUE)

model <- modelsummary(step_model,stars=TRUE,title=paste(x))

assign(modelname,model)
}

```

全搬送件数を説明する最良のモデルは以下の通りで、結局、日ごとの最高気温の影響が圧倒的に大きい（これは当たり前）。つぎに影響が大きいのは夏場の平均気温で、暑い地域ほど搬送数が少なくなることがわかった。目的変数を別のものにしたモデルでもこれは同様で、かなりロバストなものと考えられた。「涼しい地域の人ほど暑さに慣れておらず、熱中症になりやすい」という専門家の知見とも矛盾しないとわかったため、このデータを記事の中核に据えることを決めた。

このほか、生活保護を受けている人の多い地域ほど搬送数が増える、などの傾向も見えたが、効果量はあまり大きいとは言えず、記事に盛り込むのは見送った。

```{r}
model_cases

```

すでに書いたように、搬送数のデータには搬送者の年齢のほか、症状の重さと発生場所の内訳の数字もあるが、これらは今回の記事にはまったく盛り込まなかった。まだ味わえる余地のあるデータかも。

おしまい。

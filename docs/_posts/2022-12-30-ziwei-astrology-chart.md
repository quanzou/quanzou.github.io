---
layout: post
title: "紫薇斗数排盘"
katex: True
toc: true
categories:
  - Math
tags:
  - culture
date:   2022-12-30 1:37:39 PM
---

紫微斗数为中国古代算命的方法之一，用**农历**之出生年月日和时辰来排个人命盘，进而窥探吉凶。命盘形式，
分十二宫垣，以干支为经纬，星宿罗布，将中天、北斗、南斗和神煞诸星列置其中；其排盘方法毋需查阅星历，
与西洋占星学有所不同，而是透过命宫之**纳音五行数**先推算出紫微星位置，其余中、南、北三斗等共13颗星位置再因紫微星而排定，
含紫微星在内共主星14颗，也因以紫微星为首，故称为**[紫微斗数](#refa)**。

## 前言

紫微斗数推命术的基本方法是以一个人的出生年、月、日、时定出其命宫所在，依此推断其终生的地位、人格、贫富、运势，
然后依次列出兄弟宫、夫妻宫、子女宫、财帛宫、疾厄宫、迁移宫、交友宫、事业宫、田宅宫、福德宫、父母宫，作出紫微斗数命盘；
从而观察各宫位的星曜组合，推知其人生轨迹；最后再通过四化星（化科、化禄、化权、化忌）的牵引，推演一生运势运程。

## 安十二宫

### 天干地支

干支是天干与地支的合称，由两者顺序两两组合，可搭配成六十对，为一个周期，循环往复，称为六十甲子或六十花甲子。

| 天干与地支配对规则 |  |  |  |  |  |  |  |  |  |  |  |  |  |
| :-: |:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
|     | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | …… |
| 天干 | 甲 | 乙 | 丙 | 丁 | 戊 | 己 | 庚 | 辛 | 壬 | 癸 | 甲 | 乙 | …… | 
| 地支 | 子 | 丑 | 寅 | 卯 | 辰 | 巳 | 午 | 未 | 申 | 酉 | 戌 | 亥 | …… | 

干支系统为什么不是120种组合呢？ 因为天干与地支必须按照顺序，两两相配，始于甲子，终于癸亥，
一循环恰巧为干支的最小公倍数六十。天干地支的组合必须顺序相配，不是随机组合，因此不是120种。

公历年(格里历，西历)转化农历，可以采用如下简化公式：

$$\begin{aligned}
 天干数 & = & (西历年-3)\bmod 10  \\
 地支数 & = & (西历年-3)\bmod 12
\end{aligned}$$

具体证明，参见**[干支](#refb)**。

以12时辰为期1日之地支纪时法，可参考下表：

| 时辰地支 |  |  |  |  |  |  |  |  |  |  |  |  |
| :-: |:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
| 地支 | 子 | 丑 | 寅 | 卯 | 辰 | 巳 | 午 | 未 | 申 | 酉 | 戌 | 亥 |
| 时间 | 23-1 | 1-3 | 3-5 | 5-7 | 7-9 | 9-11 | 11-13 | 13-15 | 15-17 | 17-19 | 19-21 | 21-23 |

### 定命宫、身宫

以十二地支盘为基，**起寅宫**；**顺数生月逆数生时**定命宫，以命宫**逆时针**布命迁十二宫：命、兄弟、夫妻、
子女、财帛、疾厄、迁移、交友、官禄、田宅、福德、父母。，**起寅宫**；**顺数生月顺数生时**定身宫。

为示范起见，以阳历2008年1月15日（农历丁亥年腊月初八）寅时出生的女性为例。 起寅宫，先顺数生月**12**到丑，
再逆数生时**3**到亥。命宫的位置在亥。注意这一步计数是包括起点宫位的。口诀：**顺数生月，逆数生时**。

![ziwei_01](https://bnz06pap002files.storage.live.com/y4mWFisA6xV8flDW_c-HFJCK4buQZNW5bZ_jTMY1MaMOi3IzSor7TJyGSKImNce83uWwL91hyKg1dLrBfJ7cECBTXIhplFHhPHyibTfc1HNusoOXLiGet2XXaYHYNC7dqnSV98eZrbuF6OQGcSPSPyJpMp-eV9uWP1Nl9iUpMwD7I49udQ9wG3niFgyFU6rcme7?width=660&height=494&cropmode=none){: width="660" height="494"} 
 
如果安身宫，则**起寅宫**，先顺数生月**12**到丑，再顺数生时**3**到寅。 易证：身宫只可能为命、夫、财、迁、官、福之一，
因为它和命宫之间隔着双倍的生时。

## 起寅首、定纳音五行局

以出生年干支之天干数，乘于二加一除十取余，是为寅宫宫干；顺布宫干至命宫处，再以命宫干支定命造纳音五行。

{: #ref02a}
### 起寅首

十二地支盘中的每一个地支（子、丑、寅、卯……）配合一个天干（甲、乙、丙、丁……）合称：“**宫干**”。 地支是不变的，
但是天干则会依照出生年的不同而改变。找到对照于寅宫这个地支的天干，称为**起寅首**。

在找到**生年**的天干数之后，可以根据《**[五虎遁决](#refb)**》来定宫干：


![ziwei_2a](https://bnz06pap002files.storage.live.com/y4mWCnbAIyJJwZhN5x2iPcIv5LRkNF58-cjPXEsm9szn3PRH8Bxj2FbB45ryGR65AJ1p1HtIRaFEe9363bi4gQNtSFsBnJ8tHqHJneVBs0MKu7ZTODNyJYQMUpCSVj8jkVmkzUJfO78SiTuvQVGPGlOvAPn5SD5MtDMKuZZ9j2eVxhxGbZG4IIQ0Altod4zg5Rh?width=660&height=632&cropmode=none){: width="660" height="632"} 

>甲己之年丙作初，乙庚之岁戊为头，丙辛岁首从庚起，丁壬壬位顺流行，更有戊癸何方觅，甲寅之上好推求。

该口诀本是在**干支纪月**中决定每月的天干数。因为十二地支盘对应月地支，起于寅，终于丑，所以恰好可以用来定宫干。
此口诀的简化公式如下：

$$(1 + 生年天干数字 \times 2) \bmod 10$$

如果将所有可能的天干数带入简化公式，寅宫的的天干数只有五种可能：

| 天干 | 天干数 | $$(2\times天干+1)\bmod 10$$ | 寅宫天干 |
| :-: |:-----:|:--------------------------:|:------:|
|甲、己 | 1 or 6| 3 | 丙 |
|乙、庚 | 2 or 7| 5 | 戊 |
|丙、辛 | 3 or 8| 7 | 庚 |
|丁、壬 | 4 or 9| 9 | 壬 |
|戊、癸 |5 or 10| 1 | 甲 |

例如出生年为丁亥年，根据口诀<ins>丁壬壬位顺流行</ins>，地支盘中的正月为壬寅宫。根据公式，
$$(1+4\times2)\bmod 10 = 9$$，亦为壬寅宫。 然后从寅宫开始，把壬、癸、甲、乙、…… 顺时针依序排下去，
得到下图：

![ziwei_02a](https://bnz06pap002files.storage.live.com/y4mPqdPpI_4IvU2IfNWnyB3lqSbophN28EJIaK8BDGOo1RMV-Qc1hgXOCr9SO-o6VlFYvWoCJJUDJaNBxV3yNVgO1OGj9tL565l-oDBRa9DeFaiu3qa6dnBK_eiZUMLyiZ0RSNI44uFClbiPd1-40cqp_qF07EJALSsQ2yc6hKFXy5kebzxe4ys1-Oip9VwEkC0?width=660&height=495&cropmode=none){: width="660" height="495"} 

### 定纳音五行局

“**干支纳音**”， 也叫“**纳音**”。纳，包容、归纳。音，指宫、商、角、徵、羽，这五音。五音在五行的应运中，
土为宫音、金为商音、木为角音、火为徵音、水为羽音。五行局包括了水二局、木三局、金四局、土五局、火六局。
天干地支则是古人计算时间的方法，将五音理论跟时间所结合所得到的就是**纳音**。十天干与十二地支共有60种组合，
很类似苏美尔(Sumerian)文明的六十进制(Sexagesimal)。而在这六十种干支组合中，任何一个天干与地支的组合，
都有一个五行相对应，五行运行干支十二宫，形成纳音五行。

纳音首先以十天干和十二地支相配成六十甲子组合，然后以每两个干支组合表示一个五行意义。举例说明，以十天干的甲，
配十二地支的子组合成甲子，以十天干的乙，配十二地支的丑，组合成乙丑。最后用甲子和乙丑两个组合在一起表示海中金，
金四局。由于六十干两两组合，形成了30个纳音五行。

[六十甲子纳音歌](#refc)：
> 甲子乙丑海中金，丙寅丁卯炉中火，戊辰己巳大林木。
> 庚午辛未路旁土，壬申癸酉剑锋金，甲戌乙亥山头火。
> 丙子丁丑涧下水，戊寅己卯城头土，庚辰辛巳白蜡金。
> 壬午癸未杨柳木，甲申乙酉井泉水，丙戌丁亥屋上土。
> 戊子己丑霹雳火，庚寅辛卯松柏木，壬辰癸巳长流水。
> 甲午乙未砂中金，丙申丁酉山下火，戊戌己亥平地木。
> 庚子辛丑壁上土，壬寅癸卯金箔金，甲辰乙巳覆灯火。
> 丙午丁未天河水，戊申己酉大驿土，庚戌辛亥钗钏金。
> 壬子癸丑桑柘木，甲寅乙卯大溪水，丙辰丁巳砂中土。
> 戊午己未天上火，庚申辛酉石榴木，壬戌癸亥大海水。

以命宫辛亥为例，根据口诀<ins>**庚戌辛亥钗钏金**</ins>，因此五行纳音为钗钏金四局。

附纳音五行速查表，如下：

![ziwei_02b](https://bnz06pap002files.storage.live.com/y4maY36ptu5c6qjccnoAjaO3mFcha5J-89WBu_QXK3tXE89e1qRo34sfiUYf1-PMj6TWny1Vg8aFgBfCP_R9CrWpsDNGjcmtF4zjpTIjY96INH8YV49N8WmCEiTSd6axeZ2strC0graPlv2TppQvHjxbS8JCPzci2ctb3zn9WNDl2jzPV5M7-OXjx-zRvmy_yrH?width=660&height=301&cropmode=none){: width="660" height="301"} 

### 纳音推算公式

纳音的原理来自《易经》数术，是一种根据先天八卦演化出来的规律，历代以来，凡是研究阴阳五术者，
特别是古代医术“子午流注”的阴阳干支的推算，都以此为依据，应用天干地支数据相加，就可得出五行属性。

> 歌曰：甲己子午九，乙庚丑未八。丙辛寅申七，丁壬卯酉六。戊癸辰戌五，巳亥数归四。

歌诀的十天干和十二地支都含着固定数字，例如甲己子午四个字，每个字的数均为九，乙庚丑未都属八，以此类推。
具体见下表：

|天干| 9 | 8 | 7 | 6 | 0 |
|:-:|:-:|:-:|:-:|:-:|:-:|
| 阳 | 甲 | 庚 | 丙 | 壬 | 戊 |
| 阴 | 己 | 乙 | 辛 | 丁 | 癸 |

|地支| 9 | 8 | 7 | 6 | 5 | 4 |
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
| 阳 |子午|   |寅申|   |辰戌|  |
| 阴 |   |丑未|   |卯酉|   |巳亥|

干支系统中，定义奇数为阳，偶数为阴。因此在六十甲子的顺序组合中，阳天干只会配对阳地支，反之亦然，
阴天干也只会配对阴地支。假设将五行按顺序赋予如下数字：

|五行|火|土|木|金|水|
|:-:|:-:|:-:|:-:|:-:|:-:|
|   | 1 | 2 | 3 | 4 | 5 |

则五行纳音的计算公式为： 

$$\begin{aligned}
 (n_{天干数} + m_{地支数} + n_{天干数+1} + m_{地支数+1}) \bmod 5 &, & 如果干支属阳  \\
 (n_{天干数-1} + m_{地支数-1} + n_{天干数} + m_{地支数}) \bmod 5 &, & 如果干支属阴
\end{aligned}$$

例如命宫辛亥，辛亥属阴，要配合在干支排列中辛亥前一位，即庚戌。庚戌属阳，阳前阴后乃天地常规。将每个干支对应的固定数字相加，
$$7+4+8+5=24$$，用$$5$$除以$$24$$，得余数为$$4$$，就得出辛亥的命宫对应五行纳音为金四局。注意纳音的局数和五行对应的固定数字没有关系。

这种方法在推箅时，只要阴阳两个干支数相加在一起，用$$5$$除之，马上即可推出纳音五行属性，但分不出是钗钏金、
白蜡金 ……，可是在排盘时，，只要知道纳音五行，不用知道钗钏金，白蜡金，即可推排了。

## 起大限

![ziwei_02c](https://bnz06pap002files.storage.live.com/y4mHoRC4ErehyOXWboQeX7ZB_nZJx3G8Uak72XS_SYQZ2HWXfnTu4rEPQ8QS9R7JC4KoQYE2mbdwjM_Vpwb_mDxvXX_LSoRNRh2W6b9_Ew0ZYxvy6F0UHzR26h9uc0QGTDOFNhAjEBCtNvRUd2AVsdIcrtPXjVHXi6Dx8d7__FZrOtPernWxgUSVLMuWwCx6vx4?width=492&height=660&cropmode=none){: width="492" height="660"} 

起大限需要知道出生年的天干数，如甲、丙、戊、庚、壬年出生人属阳，男命为阳男，女命为阳女。
乙、丁、巳、辛、癸年出生属阴命，男命为阴男，女命为阴女。 大限由命宫起，**阳男阴女顺行**；**阴男阳女逆行**，
**每十年过一宫限**。**起大限之岁，悉依局数**。如水二局人，由二岁起限；火六局人，由六岁起限。

例：命宫在辛、金四局、阴女，大限排列如图：

![ziwei_02d](https://bnz06pap002files.storage.live.com/y4mvlewwMBSDiV8YhdKUK3pCfQBoCzyBdmH5f65pGtiN38AadeAKLgKZBLxsmQln-pqUldbhF54MqfckVCGMis3umve8qHyTkTk-TKAO8AJ9DkZG2GI_b9yg0pCK7zgKoWbePfOpVBfaxKiVShVSRdnga-5b4PsOzYzkDNKCV7Ov1fdMXjlY8SdT1jf-naLyu9b?width=1031&height=773&cropmode=none){: width="1031" height="773"} 

大限由命宫开始计算，起大限之年岁，由命造之五行局数来决定。每一个大限掌管该十年的吉凶灾咎。大限之宫位，
就是该十年的命宫，称为“大限命宫”，每当命造每进入一个新的大限时，其馀人事物十一宫亦随著大限命宫依次移动，
只有“身宫”例外，维持原位。十年过一宫限。阳男阴女，大限在星盘之中顺行过宫；阴男阳女，大限在星盘之中逆行过宫。
例如大限顺行者，第二个大限的命宫，就是原局之父母宫；大限逆行者，第二个大限的命宫，就是原局之兄弟宫。
大限有大限的四化和大限的流曜。

## 安紫微星

安紫微星需要农历出生日和之前算出来的五行局数。

### 查表法

#### 水二局

口诀： 
> 水二局中初一丑，单双不论顺行流；顺行一宫安二日，最末一天在于辰。

解释： 在水二局中，出生日在初一，紫薇星在丑宫，不管单双数日都顺著排，接下来按照顺时针，每一宫放两个日，最后一天30日会位在辰宫。

![ziwei_03a](https://bnz06pap002files.storage.live.com/y4mtm3aUBBG3B0dCPhX_oyH47HlC5cDd1DPVQVrs9_oFGcHpZQ2qA1RLV3LQopBMGg0HSerdvp6yLy2TcsZEQ-SQk52ILY6rMdbGlQScJh4GUKtO0q3nMfAkV6K0f3nKn484CCcsWIUhfBBu6qr6oYEWd3OVKoEgfJNI9rr4KlPEZelMNiPrg2hLUyt2wVgZxIj?width=660&height=495&cropmode=none){: width="660" height="495"} 

#### 木三局

口诀： 
> 木三局中初一辰，逆退二步安二天，顺行四宫安一日； 双日初二丑宫寻，顺行四宫安一日，逆退二步安二天

解释： 木三局中初一辰宫，单数日逆时针（退）两宫放两天，例如初三、初五在寅宫，然后顺时针（进）四宫再放一天，
例如初七在午宫……，最后29日落在戌宫；双数日初二在丑宫，采取进四退二的方法排其余双数日，先前顺时针（进）四宫放一天，
初四在巳宫，再逆时针（退）两步放两天，卯宫是初六、初八……，最后30日会在亥宫。

![ziwei_03b](https://bnz06pap002files.storage.live.com/y4mIi8pLIOrh9D6H7u11rS3ioFnuouZd1yyPxQKOtQH0htvT_UUYlKaIUneY1HfvGir9MUxV-BkYhxWNEeOwcDJavl6IiHb5a8RLevzcxSsrN0Rl-53vZVC2xiWFJ58M7k8sw7HfFq-z-sNB7QrYh6p5TqWVrEi-f7_yau6YC0Fcn2gj8Q7ZRnjvH-IgsRZV8MS?width=660&height=495&cropmode=none){: width="660" height="495"} 

#### 金四局

口诀： 
> 金局四数紫微宫，初一在亥初二辰；顺二逆一安单日，逆二顺三双日逢。

解释：金四局初一在亥宫，初二在辰宫，单数日用顺时针（进）二逆时针（退）一的方式来排，双数日用逆时针（退）两步顺时针（进）三步的的方式来排。

![ziwei_03c](https://bnz06pap002files.storage.live.com/y4mELDHk4QKKSnlILln6kSxHd2984qJUJWN0HmH5SD1EsL04oJYxvliAvg7bpnS-OtGlP0ZidmODYY3vWkgo4jfeg8VZo3jrzvIdLYHtDFlhCJwAa6ECEu8m0H-DtuPrey1r7nCQce6-nMoxfUYs3lfkoAtin7oX9vUhbe7aXRI13chDS1rKzlMjEY5GCRD8Sdx?width=660&height=494&cropmode=none){: width="660" height="494"} 

#### 土五局

口诀：
> 土五局中初一午，逆行二宫安一日，值九移向寅辰午；双日初二在亥宫，顺二三次逆二两，值六移向未酉亥。

解释：土五局单数日初一在午宫，逆时针（退）每两宫安一单数日，排好后，初九、十九和二十九本应分别出现在戌宫、子宫和寅宫，
将其移动到寅、辰、午三个宫。双数日初二在亥宫，首先顺时针进两宫排一天，总共三次，再逆时针退两宫排一天，
总共两次，排好后，将初六，十六和二十六分别就移到未酉亥三宫。

![ziwei_04d](https://bnz06pap002files.storage.live.com/y4mnRaNIKSG3Ps0Rs1XLRXlmYeJp9fjce81H0b4xrKfty1OHKweVQfHXD_iru37i_yAvikRT-XLDdyZb9S9VfdvkP-kb6i2HuIrANZCgHFtRN3O7IsZEzFkBu2awBLbBQsV4Vp3Ap2VqqgliavtIu7t2fK8mkhAyqY05Veie12kRcoBWo1nM4BL34lDF_V0UkcD?width=660&height=495&cropmode=none){: width="660" height="495"} 

#### 火六局

口诀：
> 火六局中初一酉，顺二两次逆三一；双日初二午宫寻，逆二两次顺五一。

解释：火六局初一在酉宫，顺时针进两宫两次，然后逆时针退三宫一次，每次排一日；双日初二在午宫，逆时针退两宫位两次，
然后顺时针进五个宫位一次，每次皆排一天。

![ziwei_03e](https://bnz06pap002files.storage.live.com/y4mcic_Qq3Y_uhLiPvLwL1316FqK--Pp6fRpLdf86lFAC9JVGK6rdT0tPH90lZ7QeT8im0BFc8F_Va8Xphl4suSEzWZPqeL0fN2MqyLk1HxqBqKbbmayiii_d9odPGNpnxLV8eiR-ONjmfLeAdil8Enkv1Ryjv_GKHXNPqDqpnZ8hzdWB0M1TDWC9TUn5_6m-B0?width=660&height=495&cropmode=none){: width="660" height="495"} 

### 紫薇星宫位算法

+ 1，求不小于生日数的五行局数的最小整数倍：$$z=\min\{z\in Z \vert z \times 五行局数\ge生日数\}$$。
如果五行局数大于生日数，则$$z=1$$。
+ 2，计算$$z$$倍五行局数和生日数之差数：$$差=z \times 五行局数 - 生日数$$。
+ 3，如果差数是奇数就用，$$步数=z - 差数$$；如果差数是偶数，$$步数=z + 差数$$。
+ 4，然后从寅宫开始顺时针走计算出的步数，就是紫微星所在位置。

定义$$生日数=五行局数\times商数+余数$$，如果$$余数=0$$，则$$z=商数$$，且$$差数=0$$；
如果$$余数>0$$，则$$z=商数+1$$，且$$差数>0,差数+余数=五行局数$$。因此寅宫起步数公式如下：

$$\begin{aligned}
 生日数 & = & z \times五行局数-差数 \quad\quad \\
 寅宫起步数 & = & ((-1)^{差数})\times差数+z
\end{aligned}$$

注意寅宫起步数如果为负数，则需要加上12，转化为顺时针步数。而且寅宫本身步数为一，也就是起步数包含寅宫。例如，
水二局生日数初七的最小整数倍$$z=4$$，差数为奇数$$1$$，则寅宫起步数为$$4-1=3$$，紫薇星在辰宫。再例，
火六局生日数十三的最小整数倍$$z=3$$，差数为奇数$$5$$，则寅宫起步数为$$3-5+12=10$$，紫薇星在亥宫。最后，
金四局生日数初八的最小整数倍$$z=2$$，差数为偶数$$0$$，则寅宫起步数为$$2$$，紫薇星在卯宫。

## 定天府星

天府星和紫微星永远关于寅--申线对称。 紫微和天府是由寅宫开始，分向相对，到申宫再聚同一宫，例如紫微在子，
天府在辰。紫微在辰，则天府在子。因为紫薇星宫位算法的最后一步，逆时针步数既是天府星位置。例如，
水二局生日数初七的紫薇星在辰宫，则天府星在子宫；火六局生日数十三的紫薇星在亥宫，则天府星在巳宫；
金四局生日数初八的紫薇星在卯宫，则天府星在丑宫。

完成以上步骤后，阳历2008年1月15日（农历丁亥年腊月初八）寅时出生女性的命盘，如下图：

![ziwei_04f](https://bnz06pap002files.storage.live.com/y4m9uXl2K9PLYrXh6L4aUOOFg5NrAjYeBjTcqbe9X05KF0YCE9FFMCzSXMhjlEWwpxnxnZ7JpAZihGlBzg3kswQh5chLnHfDz-HriuSFBx0acUcCanKqD4hei5WS64Nb3RRLdMDsPQC3CxygaqP8_QcGG-lzU_Y8gzUSnZt6IF42ot9MdUACCYXmyT37GOrlS3x?width=660&height=495&cropmode=none){: width="660" height="495"} 

## 安十四正曜

在[紫微斗数]中，最重要的基础星曜包括北斗、南斗系的正星主曜各六颗，太阴、太阳两个中天星系的主星两颗，合称为十四正曜。
北斗系按顺序分别为：紫薇（星主）、贪狼、巨门、禄存、文曲、廉贞、武曲和破军；
南斗系按顺序分别为：天府（星主）、天机、天相、天梁、天同、七杀和文昌。其中北斗系第三、四星，禄存和文曲，南斗系第六星文昌，
由于组成星系的条件特殊、所以均不入正曜之列。如果按照星曜的影响力来分类，十四正曜属于甲级星，其影响力最大。

其安星口诀如下：

> 紫微逆去宿天机，隔一太阳武曲移，天同隔二廉贞位，空三复见紫微池，天府顺行有太阴，贪狼而后巨门临，随来天相天梁继，七杀空三是破军。

解释： 紫微系从紫薇星逆时针排列： 紫微-天机-空-太阳-武曲-天同-空-空-廉贞-空-空-空；
天府系由天府星顺时针排列： 天府-太阴-贪狼-巨门-天相-天梁-七杀-空-空-空-破军-空。

根据紫薇星，或天府星的位置，从寅到申一共有六种组合：

![ziwei_05](https://bnz06pap002files.storage.live.com/y4mVmJdk-rE8M-FDkJWysGAypZZ4qJuSmbf1BSuhqT7DFaQqTgBS5Ic5jFUUOIlHoAbVhL_9ZRbzEB_mnJ_k55tWn0in4aFt5DQF8A6KMd2ZpogpHDIi3gkNpNmWqGSJ0E4cwB_96y0FFboApd0CvClVpW49iKWNdY19UARMls6ymZdV3H3OetPKjtAr7Iv53lR?width=1024&height=484&cropmode=none){: width="1024" height="484"} 

根据寅-申宫取镜像（180°旋转）后可得到另外六种组合（虽然正曜组合相同，但是组合所在的宫位地支数不同），在此不列出。

通过排列组合，不难看出下列性质：
1. 天府系的杀破狼永远在彼此的三方位置
2. 紫微系的紫武廉永远在彼此的三方位置
3. 紫微系诸星的对宫永远为空
4. 天府对宫永远是七杀
5. 天相对宫永远是破军
6. 天机-天同，天府-天相，太阴-天梁均成三合 (相隔3个宫位) 关系

阳历2008年1月15日（农历丁亥年腊月初八）寅时出生女性，目前的命盘如图：

![ziwei_5b](https://bnz06pap002files.storage.live.com/y4m8VFYZ8Umg75MtlPZ6oN1BBDYqe6NrlI6YNrM73BnN922QmE9F9RcG_9CPcKECZ_cBQMEVP7Dcdj-QGMMJIiRMZxG71KeyaSjq10fcVznJD53UPYZ-g2gNV1PL5i9MsC0HRYlgaSgy8jnfVELbh77wIEB7kClLXR1PC9MHJ3ymwO4eR60puTXl6wfvJci5XQl?width=660&height=495&cropmode=none){: width="660" height="495"} 

{: #ref05}
## 安辅弼昌曲空劫

左辅、右弼属于月系诸星；文昌、文曲、地空和地劫属于时系诸星。它们都属于甲级辅星（共十四颗），如果按照星曜的按性质划分，
辅弼属于辅曜，昌曲属于佐曜，空劫则属于煞曜，所以先行介绍它们的安星法。

虽然起星时暂时不按年系、月系、时系等次序，看似紊乱，但优点在于按照次序起星时，可以一面安星一面依次序观察，
星盘起妥， 已有大致的印象。例如安「紫微系」及「天府系」十四颗正曜后，立即安「辅弼、昌曲、空劫」
六曜，然后立即安「四化曜」，整个星盘的架构便已成形。

以后一路安星，便只是基本性质的加强或削弱，如安魁、钺之后，立刻起禄存及四煞「火星、铃星、擎羊及陀罗」，
然后起天官、天福，便可以大致对其人的「官」及「禄」有大致印象。所以，熟悉此安星的次序，对认识星盘应有相当帮助。

口诀： 
> 辰上顺正寻左辅 戌上逆正右弼当（月） 辰上顺时文曲位 戌上逆时觅文昌（时） 亥上子时顺安劫 逆回便是地空亡（时）

解释： 辰宫开始顺时针数生月为左辅，戌宫开始逆时针数生月为右弼。辰宫开始顺时针数生时为文曲，戌宫开始逆时针数生时为文昌。
亥宫开始顺时针数生时为地劫，亥宫开始逆时针数生时为地空。

![ziwei_5a](https://bnz06pap002files.storage.live.com/y4mBwEh28KIy1Hi2bvSis5qomGK9wdWPxgoJjaBqmE5L0dmgJI9f10BxzED83g_cgJyh8I06vGCSA5Kjzc2JAUgJV0_rF3Tm6zcAfNSeOGQWRCn4m1koMOaaeWDBNK53V5wNq_E0CHlOQEyBP9y8Uhyv3GSSoqBPsHjQCcAntFwh1ZkjyYQTSua2R1eHxFxIzav?width=248&height=256&cropmode=none){: width="248" height="256"}![ziwei_5b](https://bnz06pap002files.storage.live.com/y4mLHabQ4fh-DU43gtFLgTrI5FB3frsQpOiWEH7CxXXeCmxw5kn8J9GDAgZRyC1QVjAsSxO_YFEyzDMMwkhJKOYvdhs8XDhOuSM5o3dDsJQ4q0SCYJEKNx74rTyLVxk3KMTOdD3jd8BP-x-GnK55WKnqXPdI3Dg47twFdxTNIbzLz8PZIHDRGBH3zs87SyEstTH?width=254&height=256&cropmode=none){: width="254" height="256"}![ziwei_5c](https://bnz06pap002files.storage.live.com/y4m_wQhKsan4r6bFRdvoo5dNWs2zk_CEMReqYNuYedZKvRqo8cEESbVRztjIs-5cbxqBN0JN_yHpC4xgX0gjD7GAqKdYJoLmxTtl0z2t5_-4zu2IYRfnfsPUzfcLXAUWD_dP22KeKRy1ed7V6dL3W5x_RClB_s-DIn61xekhhmevXDKr3Qenjx5GndoBVxfkTZn?width=256&height=256&cropmode=none){: width="256" height="256"} 

由上可得：
+ 辅弼、昌曲都关于丑未线对称（辰戌丑未是四墓地）
+ 空劫关于巳亥线对称
+ 同时辰出生则昌曲、空劫位置相同
+ 同月出生则辅弼位置相同
+ 若要命三方四正同时逢昌曲，则需昌曲分别在卯亥、巳酉、未、丑、辰戌的位置，且满足一定生时条件。经计算，有下列几种情况：

|昌曲宫位|命宫|出生时辰|出生月份|
|:------:|:---------:|:----------:|:------:|
|卯亥|卯亥未 (4 8 12)|未亥|正月 五月 九月|
|巳酉|巳酉丑 (6 10 2)|丑巳|正月 五月 九月|
|未|卯亥未丑 (2 4 8 12)|卯|正月 三月 五月 九月|
|丑|卯亥未丑 (2 4 8 12)|酉|三月 七月 九月 十一月|
|辰戌|辰戌 (5 11)|子午|三月 九月 五月 十一月|

+ 若要命宫被辅弼夹，则需命宫在丑未：

|辅弼宫位|命宫|出生时辰|出生月份|
|:------:|:---------:|:----------:|:------:|
|寅子|丑|酉|九月|
|寅子|丑|亥|十一月|
|午申|未|酉|三月|
|午申|未|亥|正月 |

结论：偶数月份出生的命宫不会被辅弼夹宫。
+ 地空文昌、地劫文曲不可能同宫

阳历2008年1月15日（农历丁亥年腊月初八）寅时出生女性的命盘如下图：

![ziwei_5d](https://bnz06pap002files.storage.live.com/y4mx3nae_3pdfLZVJuxkYMigTxnk-sziAiLDWwhqzNroSOkYzs5t0lJ6WUrXlxktl60zSgTku56QxNnVlMy577LH2eRC1-RopYWOQoGx0HdvVh4uC_gIq2T6_3WLddW8fF3dysywF5Tfab2ZJeTRP4RpzGOOpoAhYnhmxfGjGxTBkddZ9nI4wyYpse9q8wumHfP?width=660&height=495&cropmode=none){: width="660" height="495"}

{: #ref06}
## 安四化星

四化星分别是化禄、化权、化科、化忌，是根据出生**年干**而产生，由诸星所演化，致令星相能量产生变化，
相当于一年的春、夏、秋、冬四季，宇宙法则、自然规律对人的影响。口诀如下：

> 甲廉破武阳、乙机梁紫阴、丙同机昌廉、丁阴同机巨、戊贪阴阳机、己武贪梁曲、庚阳武府同、辛巨阳曲昌、壬梁紫府武、癸破巨阴贪

也可以查表：

![ziwei_06](https://bnz06pap002files.storage.live.com/y4mbNBfWDH5Q3yn1T9Fst5amqPsH9lsqrmE6dbulxkALDc2pdZ6vIjAt77Jhad60m7UeyPAVDKeI3HTKr2GZ3Cj7DsZ_JMYCgFmIx1WBnNnZs3Qc3sOb6CNjJeB30M5uQtZIFhIKkLgO5_pi5p6GcCPjwW5bvT9fKVxcQEdmGDXoQKttNvD04Wv9tG65JFa3CEg?width=660&height=256&cropmode=none){: width="660" height="256"} 

如果农历丁亥年出生，则太阴化禄，天同化权，天机化科，巨门化忌，如下图：

![ziwei_6b](https://bnz06pap002files.storage.live.com/y4mYHmy5DapEe3-DULCmZ28fAGphFWojHgDFaiM4gN_Ls2MR3_4zmt1CIdSFVjH8-hobmIHKvUfS32qbka0Grv3SAJtNqGtLHCkbW1Qsxq6xdWaSTR9KXjVf6z3lMkEqch6FW30hPPn5cIlZXsmLTGwISEMmb5KTZr2y7_bZGaORfvDHig7IvkaDfgTAypTTj0R?width=1024&height=767&cropmode=none
){: width="1024" height="767"}

{: #ref07}
##  安年干系属诸星

根据出生年干定干系诸星总表如下：

![ziwei_07](https://bnz06pap002files.storage.live.com/y4mtJZz0D8fi-0ZxEmP-DTJiefn3JCaP1VOIUud62Du6nRcjIx9ptFiO506mE59W5nzyzPtc1BxywLnwA_GQeOFViFY-S0ICy958SBJmFGasHyu0EL3INzB9MCLN2JU5NNVwXVHYELJBQGK1SiWq5E3pJs6vA_6tmb2M1gHfwdHtArH3GZj7iA12kwzXzNcaXXg?width=660&height=534&cropmode=none){: width="660" height="534"} 

### 安禄存、擎羊、陀罗

口诀：

> 甲禄到寅宫、乙禄居卯府、丙戊禄在巳、丁己禄在午、庚禄定居申、辛禄酉上补、壬禄亥中藏、癸禄居子户、禄前羊刃当、禄后陀罗府

解释：先依口诀定禄存位于何宮，即以禄存前一宮安擎羊，禄后一宫安陀罗。禄存不会落在四墓宫：辰、戌、丑、未。
这四宫也称做「四库地」。「墓」、「库」顾名思义则有收藏、收敛之意涵。因为禄存不会落在辰、戌、丑、未宫，而且禄存前一宫为陀罗，
因此陀罗不会落在卯、酉、子、午四宫。这四宫被称做「四陷地」，有濒临失败之意。同理，擎羊不会落在巳、申、亥、寅死宫。
这四宫被称做「四马地」，因为“天马”只会落脚在这四个宫位里。

+ 如果在命盘上顺时针走，必会先后连续遇到陀罗、禄存、擎羊
+ 四墓地没有禄存
+ 四陷地没有陀罗
+ 四马地没有擎羊（亦即，擎羊不在角上）

![ziwei_7a](https://bnz06pap002files.storage.live.com/y4mPw9hdBTe8_KBKymLPIZ-sCS307Cl1FdHNs60a7SGp1nZIv5XqAKI5DjtCNhjW8T_QSKOHGeGzfh1G6B6uLJX0yklW3ncLOTwNKMYvtFK3M1VepVZhKRgE5_2a35CcXm2mnLaAuKdAN1YK3aqOm3grezACMzMJ6oaL9O8UvZ6gVp6EsTfuk6t3PNaQmiBrr1G?width=256&height=249&cropmode=none){: width="256" height="256"} 

### 安魁钺

口诀：
> 甲戊庚牛羊、乙己鼠猴乡、丙丁猪鸡位、壬癸兔蛇藏、六辛逢马虎、魁钺贵人方、

解释：甲戊庚年生人，天魁在牛位，即丑宮，天钺在羊位即来宫，如此类推。

![ziwei_7b](https://bnz06pap002files.storage.live.com/y4muTfwCq2UM6FTqrinAYNtyNHCSWStPG1TkoPSC0WRC0g1XhLTM_b_jLQilecvXcDPAK2e-D0bvW4Dg_KSpXdlx_rUpJ7Ie_bxlH8V7m4KBfxLoIv_opYkuGiPR9aMM9mftWB1yeyP6e8Ft9a96ehpQAd9g1Dg7-a__1ukdkWQ5Vs8mg5vZ6hX6DA6Mikm5hmb?width=660&height=313&cropmode=none){: width="660" height="313"} 

由此可看出魁钺关于辰-戌线对称。若要命宫三方四正同时逢魁钺，则：

|魁钺宫|命宫|生年|
|:--:|:--:|:--:|
|亥酉|卯|丙丁|
|子申|子申辰|乙己|
|丑未|丑未|甲戊庚|
|午寅|午寅亥|辛|
|卯巳|酉|壬癸|

### 安天官、天福

安天官天福贵人诀：
> 甲喜羊鸡乙龙猴、丙年蛇鼠一窝谋、丁虎擒猪戊玉兔、己鸡居然与虎俦、庚猪马辛鸡蛇走、壬犬马癸马蛇游、

解释：己年出生人，根据口诀**己鸡居然与虎俦**，鸡位为天官，即酉宫；天福为虎位，即为寅宫，以此类推。

![ziwei_7c](https://bnz06pap002files.storage.live.com/y4mcNpluiHvCU2FdRYOOHZwV9DEiPzZ6F5cO2ogrOqRNKUkAMI74RvqnoPMvf5F0CauE3cwvYNqsRB6an6mhFS993TySc2CLS8lnI5knF5YTJh6QOXWlAOc3KR-4E1SnUJREIxa7vlJBe1WsIDO_7HqCfvY8aAIrFyxwVZAVFreFTtK_TdAj8vXWiyEWDUNpm4p?width=660&height=322&cropmode=none){: width="660" height="322"} 

### 安天厨星

安天厨诀：
> 甲丁食蛇口、乙戊辛马方、丙从鼠口得、己食子猴房、庚食虎头上、壬鸡癸猪堂

解释：己年出生人，天厨在猴房，即申宫，以此类推。

![ziwei_7d](https://bnz06pap002files.storage.live.com/y4mZeBArJg87PEyCpGtLXcfNPuVuRpXCyW6Y4W7uqxbBNjV-5P5lkezshqPDG-uMh5LIox4UT7_kCdctcrAZfFM7LwWg0VRNqwX653PgyqhcfjfoOlLwMNIQRMKMmjEt5kSn_8jTGf9y1OlqpyIGuZ5GJOCtR2T8nTGnte67Z3iMWrH5_mC_59aFsccSzPxozsP?width=256&height=250&cropmode=none){: width="256" height="250"} 

### 安截空

截空星全名为截路空亡星，截空是一个星占居二个宮位，在应用时，分为一正一副，正称为**正空**，副称**傍空**，
以别轻重。正空重傍空轻。如出生年干属阳，则阳宮便为正截空，阴宮为傍截空；反言之，若阴年生人，则阴宮为正截空（截路），
阳宮为傍截空（空亡）。

根据生年年干安截空诀：
> 戊癸子丑起、推至甲己止、申酉是截空、戌亥不论此

解释：丁年出生，寅卯宫为截空星，而丁为阴年，则阴宫卯宫为正截空，阳宫寅宫为旁截空。

![ziwei_7e](https://bnz06pap002files.storage.live.com/y4mDX4MYVmPPdBz2mOdd02ANvGK2ePprpsYhr4e7rgcY83tAesahGe_emuUJGDHuSeeL7pX4BqXBpCxuG45p45KEzedzfjWO42dAkkUMG2f-7rvicDonjhHTfNzrnf1ctIz__DapYtAYNITZj1SipBuP-oVtNEKauddPGfdxfnq3ITCq9jXYFU4gjo-Qqpl8sY6?width=256&height=249&cropmode=none){: width="256" height="249"}

### 安旬空

旬空星全名为旬中空亡星，在阳宫为空，在阴宫为亡。天干有十个，十为一旬，以十天干配十二地支，但地支有十二个，
所以有两个地支没有天干，这两个地支便是旬空星的位置。而旬空星是依**生年年干**对应**生年地支**的位置找出来的。
但谨记阳天干配阳地支或阴天干配阴地支是为正旬空（旬中），阳天干配阴地支或阴天干配阳地支是为傍旬空（空亡）。

![ziwei_7f](https://bnz06pap002files.storage.live.com/y4mBBEoUdb4In2EtI6gWXO9cxwfVccqRJegMy6XmjOi79nwJODKumpiViMYXi5lnujFtgWKkn39Z0Xi3cbcaaSwPQcn3WOXtEXJsx3bmtJrJYs2jSn7LIJxPY5a7d-8ViIoxPbRY-kxwSLedOsUYFXczVh2Nbrmc32_padaJFKab9ac9Z3WYja4sm-riEHNM4Qd?width=660&height=323&cropmode=none
){: width="660" height="323"} 

根据生年年干安旬中空亡决：
> 甲子旬中空戌亥、甲戌旬中空申酉、甲申旬中空午未、甲午旬中空辰巳、甲辰旬中寅卯、甲寅旬中空子丑。

解释：例如丁亥年出生，于亥宮起丁，子宫戊，丑宫己，寅宫庚，卯宫辛，辰宫壬，巳宫癸，天干至癸止。故旬空在午、未二宫，
生年年干丁（偶数）是阴女，午宫为阳，故为傍旬空；未宫为阴，为正旬空、此同截空例。

阳历2008年1月15日（农历丁亥年腊月初八）寅时出生女性，年干系诸星用红色标识，目前的命盘如图：

![ziwei_7g](https://bnz06pap002files.storage.live.com/y4mnuxU0pF-oNsj7AVcILUtF74Hj7Ns4hWsYP1KU736kR4dqfhh9-UFOpEBKRgeVocrzQIRH1g4fEOdNWSpgWsRES4Kc9SNz96RdojEf2L3vwLVx5ZhrlSQl-62jmgD_VmXSGukgwKjHoUVi7OIzVbKyJ64R1u-BIdVy9WdwWpe3Wlz2Mf0krZOkYVz18kYQac7?width=1024&height=767&cropmode=none
){: width="1024" height="767"} 


{: #ref08}
## 安年支系诸星

根据出生年支定支系诸星总表如下：

![ziwei_8a](https://bnz06pap002files.storage.live.com/y4mFeKfYTHbgQCy5iSk6p78Xow6yckGnM9xAZtqpjKckYZt9X73OhjPOKpbXEpNi7jagZLQpEw70oL6wVH0ocj4RkPjkCsHzl9Ua_jqFCk8687dYR5AxXuYLERqgur-S1jgnnSct24-LVXI4fiNfrkqYrsYLqDa_G61WiAzlq_Vdq0Bp-wqGhxk23u78jYnqTwi?width=660&height=489&cropmode=none
){: width="660" height="489"} 

### 安天马、天空

安天马天空诀：
> 驾前一位是天空、身命原来不可逢、寅申巳亥天马位、三合长生恰对冲

解释：天空在出生年支向前（顺时针）一宫，例如午年生人，天空在未宫。天马以三合局为准，冲三台长生之宫位，即安天马。
如申子辰年生人，长生在申(参见安长生十二神)，寅冲申，故此三年生人，天马在寅。

又一安天马诀曰：
> 寅午戍年马在申、申子辰年马在寅、巳酉丑年马在亥、亥卯未年马在巳

![ziwei_8b](https://bnz06pap002files.storage.live.com/y4mWXrX8SlEiStGq6nMMqzzI-zopPrhKmlac4DEM3tLpB1Zb-iqdBKUQq8W0IOBO_kajzh8hHLxTzV8rJNZr0U-qmmrtKSaXf5RdxyvVfGkPjtHmqAUN7VpXLrBFKMePT2fxpesEBb1un40I0P2knh6zr23_K0_MIL-Tlqd_ZayQLk8Ugklyx21ghYcsVGFmHx1?width=660&height=319&cropmode=none){: width="660" height="319"} 

例如亥年出生，则天马在巳，天空在子。由口诀可知，天马必在四马地，且必不逢擎羊。

### 安天哭、天虚

根据年支安天哭、天虚口诀：
> 天哭天虚起午宮、午宮起子两分踪、哭逆巳兮虚顺未、生年寻到便居中

解释：由午宮起子年逆行，数至出生年支即是天哭；由午宫起子年顺行，数至出生年支即是天虚。
如寅年生人，天哭在辰；天虚在申。亥年生人，天哭在未；天虚在巳。

![ziwei_8c](https://bnz06pap002files.storage.live.com/y4mzZslb4cCTe2nYPVE7ctt03MSstVZLsiSkXa2UOpbkGLArtjm0pHUY51CdtyJ5tOeT6vXNDAwfp9FGVYxb0DFQjFM8BfPKIzSb_ccKgeC2-NjZ96MUKzcsZrak39l7gMJ86OTw8hoAdPmBkht5-RqLRv2IfdaYgEctBKUfTci66rgDxnWn1mjIZTWiyM9m6tU?width=251&height=256&cropmode=none
){: width="251" height="256"} 

### 安龙池、凤阁

安龙池、凤阁口诀：
> 龙池辰上子顺行、生年到处福元真、凤阁戌宫逆起子、遇到生年是此神

解释：龙池从辰宫起子顺行，凤阁从戌宫起子逆行，分别落在出生年支相应的基本宫。
例如，戌年生人，辰宫起子顺行，龙池便在寅宫，戌宫逆行起子，凤阁即在子宫。亥年出生，龙池在卯宫，凤阁在亥宫。

![ziwei_8d](https://bnz06pap002files.storage.live.com/y4mA23SQXxNWMCu85wAHbg-Gk0JhFBFe8_kBrV-B2YWmUpomgRTfE5i00nowEG7kbEiDe0YkWjxIQhLYBjGZY_B0q661TvIWg5ehqiuXQ7mFeW3ttKx6yQGy4sTtV1Zzml4p_tPEMndNnxlTRRS2A6s3_N8HRLC_APC7nlUfekIN-lJl0AEJVCooAfQKt4xkkaq?width=256&height=247&cropmode=none
){: width="256" height="247"}

### 安红鸾、天喜

安红鸾天喜口诀：
> 卯上子年逆数之、数到当生太岁支、坐守此宫红鸾位、对宫天喜不差移

解释：从卯宮上逆行起子年，至寅宮丑年，丑宮寅年……，如是安红鸾后，天喜一定在红鸾对宮。
例如巳年出生，红鸾在戌宮，天喜在辰宮。亥年出生，由卯宫逆时针一周，红鸾辰宫，天喜在在对宫戌宫。

![ziwei_8e](https://bnz06pap002files.storage.live.com/y4m0YJwMYgXLqQlBROkPyLkcngoX3BXV8NUBkhfH6jX25XZwy9MEj-du8ojP4IbAiZ9jTXT4tPWrer0D9WrBaAe0c66IBNcU6NImgmK-N9w17Kel5tLVjmDBm-7Gx_Q_KFf_VB-clcQnzWhi4tEPRrndnUk4ojOum9M3klPUQKddTmCCtCPP4fgG2l0ITFWKc-q?width=252&height=256&cropmode=none){: width="252" height="256"} 

因为红鸾和天喜都是逆时针旋转，且起宫分别为卯、酉宫，互为对宫，所以最后也分别落在对宫。

### 安孤辰、寡宿

安孤辰寡宿口诀：
> 寅卯辰方安巳丑、巳午未方怕申辰、申酉戌方属亥未、亥子丑方寅戌嗔

解释：「亥子丑」中「子」冲「午」，「寅午戌」三合，找寅戌安星。「寅卯辰」中「卯」冲「酉」，「巳酉丑」三合，找巳丑安星。
「巳午未」中「午」冲「子」，「申子辰」三合，找申辰安星。「申酉戌」中「酉」冲「卯」，「亥卯未」三合，找亥未安星。

或者先以「方」中的旺神求冲(参见安长生十二神)，如寅卯辰年生人，卯为旺神，卯的六冲（对宫）在酉。得酉之后，
其「局」中馀宫即是孤辰寡宿位，酉属「巳酉丑金局」，所以巳宫安孤辰，丑宫安寡宿。

例如亥年出生，依口诀**亥子丑方寅戌嗔**，对宫为午，寅午戌为三合，则馀宫寅、戌分别为孤辰、寡宿位。

![ziwei_8f](https://bnz06pap002files.storage.live.com/y4m_mCJwqpsDDwGFNTSx19-XGXJp9Y2dc40exz92po8FhrOvm_25iLGm0es1C163F7wOnbj75QLy6AcJxg43YfIRRGWxaYvuLG9eDZxQS9bJQ6pW5_lp_T_V5FwRmmf-n77FPbHh30mAZVcpj40Ya0Lw9tGiR_ZrZu7Qan1fUWUh69M8w6SOcJVPE-wwHJ0AO3o?width=251&height=256&cropmode=none
){: width="251" height="256"} 

阳历2008年1月15日（农历丁亥年腊月初八）寅时出生女性，年支系诸星用红色标识，目前的命盘如图：

![ziwei_8g](https://bnz06pap002files.storage.live.com/y4maxCWahiZdHGtIGcU43mQjBxJkjRM44TqJR3-asyJ10cuO_Pao30mqq5Lx7obmFD7WhMiCyRBGGU1CU8ZfRiVY5DY9AVO4Z2BR5J4nI41xRhn8isahtq8OnqhZcDjKo77JAMU-gBFFCgSCZflfRIAVqAnENTVECcVLznVZ6MIfMQHvliWlKw9tXWh6Np53FWK?width=1024&height=767&cropmode=none){: width="1024" height="767"} 

## 安年支系诸星（继续）

根据出生年支定支系诸星续表如下：

![ziwei_9](https://bnz06pap002files.storage.live.com/y4m1XmHakjJ-oxHJYlJNkuRjphtMaeYQLsuMRKvhq0KKsyIfOSCrpNodYlu6j6m8MsZ7AArtccg30Rp92Fro4kgqjGpLl7wblMke3PQX4UIY3EyMtx48x1BLaQML_rH9muHB3O4wazI0Ph1VRGrDpTy_OFc0ZRwCIfOdvASYaF6wvSZQvtNgNkX4IML9kOECIc5?width=660&height=484&cropmode=none
){: width="660" height="484"} 

### 安天才、天寿

安天才、天寿口诀：
> 命宮起子天才顺、身宫起子天寿堂
解释： 从命宫、身宫分别顺时针起子年，数到出生年支，分别安天才，天寿。

例如亥年出生，则命宫、身宫分别在亥，卯，顺时针分别数到亥年，则天才在戌宫，天寿在寅宫。

### 天德、年解(生年解神)

安天德、年解(生年解神，不要和生月解神混肴)口诀：
> 天德星君超酉宮、顺至生年定其踪、年解戌宫逆行去、数至生年可解凶

解释：从酉宫顺时针起子年，数到生年，安天德；从戌宫逆时针起子年，数到生年，安年解。

例如亥年出生，则天德在申宫；年解在亥宫。

![ziwei_9a](https://bnz06pap002files.storage.live.com/y4mBQLCZLsrQ37ZLW1DeiL-3Rx9uQURT2Aqls9QEPk4UEGgEr_HA6d6DIko0EqaHSkCVKCo7g7eJNtVmGrMBEIKLF9d1gszLFI3J2Dza9EBG5VUJLMYHjkV-bdZU17KKNTSvN5eaYAW0iZAmHtC9pFfoKTCSkKkEpWcyppUyFeroDypIlvOYkmgd1JbpAAI12r9?width=660&height=313&cropmode=none
){: width="660" height="313"} 

### 安大耗

安大耗口诀：
> 但用年支去对冲、 阴阳移位过一宫、阳顺阴逆移其位、大耗原来不可逢

解释：大耗安法，是在年支之对冲，前一位或后一位安星。阳支顺行前一位，阴支逆行后一位。

例如：亥年出生，亥宫对宫为辰宫，亥年支为阴支，逆时针退一位，大耗在卯宫。

**注意**：这里的对冲不是传统意义的对宫，而是根据下图所示关系：

![ziwei_9b](https://bnz06pap002files.storage.live.com/y4m0m-m8dx8YfT5PcyPkAOVUR50neryEcVhi77ac4LciWMEtmst3pZ2XQ0lkbiw8SD6CTH0UgXAaduPqdwyzO7UndH6ilziTiomkXtCLG-AvbDbQTYCF9X-AAK1M9D1FFBVNyXnrjAlLwypoPMb84fF0qrmdd0nzu-1a8CcpfcM0Ns5L5HxGck5qTZw06ZxGa7z?width=256&height=246&cropmode=none
){: width="256" height="246"} 

### 安年支六曜（蜚廉、破碎、华盖、咸池、龙德、月德）

安年支六曜口诀：
> 蜚廉分方顺年移、西南东北各轮之、破碎轮排巳丑酉、不关生月与生时、辰丑戌未轮华盖、酉午卯子布咸池、龙德起羊月起巳、六星都起据年支

解释：安蜚廉星，由申宫起「子丑寅」年先顺时针在西方「申酉戌」宫，「卯辰巳」年次在南方「巳午未」；「午未申」继在东方「寅卯辰」宫，
「酉戌亥」年最后在北方「亥子丑」安立。安破碎星，子年在巳宫起，按照「巳丑酉」三合逆时针轮排。

例如亥年生，则蜚蠊在北方「亥子丑」中的丑宫，破碎在酉宫。

![ziwei_9c](https://bnz06pap002files.storage.live.com/y4m_Pc8MW0nBDWoDspJMuuUjkMsFgUca3HthiNJ5PX0_TNnXpCIKeESIlOWVtFTiaMTJFpzr0N9o5EaNldsAM1PPOsvgP_y_3xcP0uO7oZMd8zb-RU0Nf6JirukE794O4llgvxqmS-PbmMSqhXbzI2eJadsZ8D-XmlgOLLdXkyEyTW4q7JStvjLZS4GqXazKVSg?width=660&height=311&cropmode=none){: width="660" height="311"} 

解释：安华盖星，子年由辰宫起，按「辰丑戌未」逆时针轮排十二年支。安咸池星，子年由酉宫起，安「酉午卯子」逆时针轮排十二年支。

举例亥年生，华盖在未宫，咸池在子宫。

![ziwei_9d](https://bnz06pap002files.storage.live.com/y4mLstzRQngCA7yEpAsaOEaxRjfPPYMdmSoaz1aB3oSPRTZMXT4BvZhn-euWa-Dym49xW8z-dHvgf6hpeU5nzI2yUkx7G-cOo88S3I5usNqnbHNE2HMU6x6QrWcWkEnCQ9rxdgQFOYzFJ7SYZXUEtHuMtPht0SYCGPlf3mhVHfkn-85YoWnyuG5qsn6E2ipOyxV?width=660&height=313&cropmode=none){: width="660" height="313"} 

解释：安龙德星，由未宫起子年，顺时针安十二年支。安月德星，由巳宫起子年，顺时针安十二年支。

例如亥年生，龙德在午宫，月德在辰宫。

![ziwei_9e](https://bnz06pap002files.storage.live.com/y4mf11YdyC17tQQs3o1VKXF10-a6CfRRdzxTHhc22rSnmK5jVqwM3Nb-wbeoQriMDEutQ9O7YRhc3iwz2rrmw4YcOn_R9ZgpPEaT7DTiA8sHnfi2OdsEzSI0Fhpjc76bcg6t-rmNO1-R33z1epvPM0enumAzHsAQCE1LLTpTvq6QSoVkyWGCqAV6X1kR5HYr2yy?width=660&height=310&cropmode=none){: width="660" height="495"} 

### 安劫煞

安劫煞口诀：
> 申子辰人蛇开口、亥卯未人猴速走、寅午戌人猪面黑、巳酉丑人虎咆哮

![ziwei_9f](https://bnz06pap002files.storage.live.com/y4mjUVYlp5twA9I99zgbXULb2vg6Tk5CsIPyRGKSDtFP0I0siUItUfHJ3oi4knyHZwJpxIyRt-GOqB5aoR4cOJBUQmAiaO-BBPm2Yc0UGGvMmuNgByTiJsTXAe1JX7t0_2YowB0PpzcYiOOwBWjXUgQVg69_sx6HbIglFwr3GmV2xB-9bw-nF1ks_7NMlCTS-al?width=256&height=245&cropmode=none){: width="256" height="245"} 

解释：劫煞以三合局来定位，例如「申子辰」三合水局，在水局之绝位（第十个宫位），即巳位安劫煞；
「寅午戌」三合火局，绝位在亥宫，劫煞在亥；「亥卯未」三合木局，绝位在申宫，劫煞在申；「巳酉丑」三合金局，绝位在寅， 劫煞在寅。
或者根据方便法，即劫煞必在华盖顺时针前进一个宫位。

举例亥年生，「亥卯未」三合木局，绝位在申宫，劫煞在申，而亥年生的华盖在未宫，劫煞恰好在华盖的下一个宫位。

阳历2008年1月15日（农历丁亥年腊月初八）寅时出生女性，年支系诸星用红蓝两色标识，目前的命盘如图：

![ziwei_9g](https://bnz06pap002files.storage.live.com/y4ml0T7h91RRBnFOguJNEb9hw4i7mvUb3qIo-wCD572wpVaVqI4PoIj0xgbO1MaHl-I6yJjQU5FkuRG9HJhrBc2UYmEmEnVliRjZXvs8xEv2LqwRiIcsWwf_QK6c7PYEXJ3RfWPHltNIQTlS0aqzGDUmwksoIjzTCrfZl3Ub06okPhBaHU7X0blyfbfCpG5u7md?width=1024&height=767&cropmode=none){: width="1024" height="776"} ]

## 安月系诸星

辅弼星已经在**[安辅弼昌曲空劫](#ref05)**的章节中介绍过，这里继续介绍其它月系诸星的安星法。

![ziwei_10](https://bnz06pap002files.storage.live.com/y4mBfhsEkophGuGZSzA0ByFIaVLlVYU3RyJxP0_WGabulcGRELrijY-Yu0cMZlJFKmtK9YDu2VrNWmMfMFEDPmHdoLd6Uc4a05vi_9ygbA3UEUTpVPQn_-88t_HHCjkKvkzJ4Ukl_XGik6WlzIQx-Rz7clfGNlWViEE479kg7FM4y6Bis_Vf0zYuTklST6QVIu5?width=678&height=750&cropmode=none){: width="678" height="750"} 

### 安天刑、天姚

根据生月安刑姚口诀：
> 天姚丑上顺正月、天刑酉上正月轮、数至生月便住脚、即安刑姚两颗星

![ziwei_10a](https://bnz06pap002files.storage.live.com/y4mbHhxaYyy-lJYyrKhBagOprYhrWupTjxVGL95E0Cja6XOW0dWncd9K550l_K0Dz7NTX0dOPo8TRQ15qBzDFZ21qx8sVLVRnNv2GqOx-5IS-cz4ka7a5u8GmXgmLA-rYeqbRsckoYKKvggK914eAiPPrGfsts5ulRZVpoEXfvVvRmPnRMWHD8nfVRk-rzhFmQC?width=660&height=315&cropmode=none){: width="660" height="315"} 

解释：丑宫开始顺时针数生月为天姚，酉宫开始逆时针数生月为天刑。例如腊月出生，则天姚在子宫，天刑在申宫。

### 安解神、天巫

安解神、天巫口诀：
> 单月冲宫见解神、双月还依单月辰、巳申寅亥天巫位、分轮十二月星君

![ziwei_10b](https://bnz06pap002files.storage.live.com/y4mqdUU9YSZ2UyK7vhKUm3DE95NGXLD58-wCs9q9kkSwNY1MUdH8wcgIX10XjzQRGTzS07zN3-ZEk4srVGvGx4r8wUGKQ3-rXtfwd-az3cXZVEvIz-N4H7eC1-7j8XDLdJ6khsQ_6FVSewruxR48fFj-Ki5MhorQ5lhemtu063n4F0gH9uvQDRdvzfs8GKIJgyd?width=660&height=314&cropmode=none){: width="660" height="314"} 

解释：解神又名月解，与按生年所安的[年解]有别。月解的起法，按两个月起一宫，例如正月二月同宮，依正月建寅，
所以正、二月的月解同在寅的对宫，即申宫。相当于按从寅宫起正月、二月，顺时针隔一宮安二月，以此类推。
天巫从巳宫起，按照巳申寅亥四宫顺序顺时针，分排十二月的天巫星位。

例如腊月出生，则解神在午宫，天巫在亥宫。

### 安天月

安天月口诀：
> 一犬二蛇三在龙、四虎五羊六兔宫、七猪八羊九在虎、十马冬犬腊寅中

![ziwei_10c](https://bnz06pap002files.storage.live.com/y4mlFT5GIanC8-Iup-hSnlf60i5NsQCM5H9v_SQbMa4I0W987B3H1A3R_e_6UvAzO4XDIcV_whjSdnONMTMm_1AIms2KfZk0rbEHIJJxL_qL4EvLVzx8t0572hek8cthGMsX93x5Wi6TZ_tuZMF5UeKiT4YeZyMLu8rriZdhgIhjoREw42BzPvRTrJC5IHBn4Ms?width=256&height=250&cropmode=none){: width="256" height="250"}

解释：根据口诀将月份安进相应的基本宫中。例如腊月在寅宫。

### 安阴煞

安阴煞口诀：
> 寅子戌、申午辰、分六月、阴煞临

![ziwei_10d](https://bnz06pap002files.storage.live.com/y4mNQoDcnEr6hJY_SyIQnkC2ul5QleQJgaIG6ALLvpOHAhEBj3nHDZj38yZupRnTMNR_K9SNUoKGRlVmVfYWzF3PocLDyPpr0gmWj42c91CuPjWxnhSROCqZQiUFsTmqGfA6fbZKALMaU6yOJOtVWWiJkYsxDLlr0T0gpvYHYhgKr18YwvBDDdWiVkDFbGasVOo?width=256&height=248&cropmode=none){: width="256" height="248"}

解释： 正月由寅宫起，逆时针每隔一宮安一月，如是轮排十二月。很明显，每宫内的月份相差6个月。例如腊月在辰宫。


阳历2008年1月15日（农历丁亥年腊月初八）寅时出生女性，月系诸星用红色标识，目前的命盘如图：

![ziwei_10e](https://bnz06pap002files.storage.live.com/y4m_HgIqGCx23ZRpaapA4M-PnPzurNidVqqkuvvGvc8jdhEVZIgOyJElcXxz5srifMP9YF0ZTaFMoHerAcTMywxs3r3OR3HmektMpw0-S8ZiuVbREsy1l4oqutjEim0yIoOWLO-5pIqsuQjF38bfuo0pGSJGNf5MOCJUZYryBP61d-43Evpb6i5fo-L1Fnd_g0u?width=1024&height=767&cropmode=none){: width="1024" height="767"} 

## 安日系诸星

依辅弼安三台八座口诀：
> 三台左辅起初一、数至生日是台宫、八座右弼逆初一、数至生日定其踪

依昌曲安恩光天贵口诀：
> 文昌顺数至生日、退后一步是恩光、文曲顺数至生日、退后一步天贵方

![ziwei_11](https://bnz06pap002files.storage.live.com/y4mbLaZ_VNLRn4xKAh1nuD7WDAUX8d0tBY58EBICwUgJgnjT8QMnBucoJCi1Wk4rQmvt1y9ahwT954BnJIw4nedk_HnQvd4RJF-oHT8KDvxWkuVKjMnvoNvwE1fr1sGs592yQIuXre21tnaKOl8721FgyH6ETbC8vyXPunDGjPHzfPCyxAyYLZZ1Q8zlEjauAmH?width=660&height=210&cropmode=none){: width="660" height="210"} 

解释：阳历2008年1月15日（农历丁亥年腊月初八）寅时出生女性，初八生日，左辅卯宫起初一，顺数初八，三台在戌宫；
右弼亥宫起初一，逆数初八，八座在辰宫；文昌申宫起初一，顺数初七，恩光在寅宫；文曲午宫起初一，顺数初七，天贵在子宫。

![ziwei_11b](https://bnz06pap002files.storage.live.com/y4mJN6j-CC0MySxO86-kQOhM3wSx8vX1VGOykanm4vtcboqPNtybzm9j9CWmgdJRWZIJcJqiRjzh3b6023iOz6IYPVKovyWgCFAATMfrAfqEJvNFxVnpTkJLUCDZAnvA8jsEUbcP6XEGL_d1rr8GB2BLfMkRw-Ws1zOZzpdaoQUdzeD0-YPIL0yjnVGU_Eznvvq?width=1024&height=670&cropmode=none){: width="1024" height="670"} 

## 安时系诸星

昌曲空劫星已经在**[安辅弼昌曲空劫](#ref05)**的章节中介绍过，简单概括则为：辰宫开始顺时针数生时为文曲，
戌宫开始逆时针数生时为文昌。 亥宫开始顺时针数生时为地劫，亥宫开始逆时针数生时为地空。这里继续介绍其它时系诸星的安星法。

![ziwei_12](https://bnz06pap002files.storage.live.com/y4my3IKAgcz37AaQB7j53oF4jumQYbC1cWV0_DwHqxZElN9mfXoPcYNhxrNoZ8hHhchpxVYqNaamRJuPys8Lhqf8UPE4S0DSOuLOnBItCjn2Jf1DZncfmsTWHx_TUePv9GHdM971zHIT8yicKkNZPU-kF7F0aqO4c9P9MentMMyqyZkqLUpoNLZkNKWbZMbN6_Q?width=660&height=496&cropmode=none){: width="660" height="496"} 

### 安火星、铃星

据年支依生时，安火铃口诀：
> 申子辰人寅戌扬、寅午戌人丑卯方、巳酉丑人卯戌位、亥卯未人酉戌房

![ziwei_12a](https://bnz06pap002files.storage.live.com/y4mdQwhl6h7sgoLMjaRplgVEzzDWqZdcO2fC3ExeJQdouFkB4FC8hyr97jkCcz5oGek0dHYs7utDWlR_AKvAxypNXlwsrPfH7PQgxIj9_cyB3JQel-lZ9ikrE8VEeYqJEqVLMycv32V-Z5I3Y8RNGMny_5kuysJbCqBoeXgPVZs4lELsYCXM63U63Okurrcl6Tg?width=660&height=314&cropmode=none){: width="660" height="314"} 

解释：起火铃二曜先据出生年支，依口诀定火铃起子时位。
例如壬辰年卯时生人，据「**申子辰人寅戌扬**」口诀，故火星在寅宫起子时，铃星在戌宫起子时，顺数至卯时，
即火星在巳，铃星在丑。如果丁亥年寅时出生，则火星在酉宫起子时，顺时针数至亥宫，而铃星在戌宫起子时，顺时针数至子宫，
即火星在亥宫，铃星在子宫。

### 安台辅、封诰

根据出生时辰，安台辅封诰口诀：
> 曲前二位是台辅、曲后二位封诰乡

![ziwei_12b](https://bnz06pap002files.storage.live.com/y4mekf4vSW_73D8BEOOwVaAsStAp0wwVSjZmHqzs_eclLfkHyX9qtNttqRHt2mPfsS5z-B3c1Ud-Vj8QUSmsLHU6t4cUGevU5e0WvYT_AhOpOWs8iC3Lrny_wPiihkU_wmgAXT9JhNa7HOLiz5ga4hp7VR7WwY1IEj0mzmChRXtlgyWPMhVTqsbVIsNxM7uT1dM?width=256&height=245&cropmode=none
){: width="256" height="245"} 

解释：文曲星顺时针前进二位安台辅，文曲逆时针退后二位安封诰。例如文曲在未……，则台辅在酉、封诰在巳。
如果寅时出生，辰宫开始顺时针数生时，文曲在午宫，则台辅在申宫，封诰在辰宫。

阳历2008年1月15日（农历丁亥年腊月初八）寅时出生女性，时系诸星用红色标识，目前的命盘如图：

![ziwei_12c](https://bnz06pap002files.storage.live.com/y4mrkcFQov0v87KFn2FiCH0OW_ezfz0oKkHrHfcvwl1nDzRSN9wDvhqdiR1vluUHpMZOApPVaFuEXG6-kTyHxh_zNFoJfjplGdOBBIhAlY5Y0PZOZeS0V4eWae6eCIEtg_PebElUt1Vha-8qdHvO8HdXHIdz4nP948mX-dY25lBiqM_Pxq3nNzHZN7HuvkG8-zw?width=1024&height=670&cropmode=none){: width="1024" height="670"} 

## 安长生十二神

金、木、水、火、土，五行五种元素在十二宫中都有一定生长，壮旺而至哀死的过程，有如春天的草木萌芽，夏天开花，
秋天结果，冬天衰死而果实埋藏，到春天后又再发芽，五行的变化，术数中便以下列十二个阶段来形容：

![ziwei_13a](https://bnz06pap002files.storage.live.com/y4m4sudFp2-0dyXQ2ZJCAvYxmb-8sVYVRFnwAptg4qVn25YE86EltBOEKMhXp3ZeYNzxUR8w2OLvKnb8bXQHcylHuQD1VaXORTw7X-XkoYCRH4QwV3nCyRYgrU9bgndO5U4swsR_bnlq2fZA-4lcjKiC9Njgile7xIok2X2p7Spn4IRHamirrdaXc0_htPRpmz3?width=527&height=660&cropmode=none){: width="527" height="660"} 

五行十二宫，各有不同的生旺衰绝期，现将之分列如下：

![ziwei_13c](https://bnz06pap002files.storage.live.com/y4mTvHIeib5o84_zdy5Ul39taCjYdokhid_tyuIZGtoiLJD9FZ0AA8PBt_6vXcDGHqbv1zA4VUQVIOaAoRtAOcm1aB0nq62RvyXmcxAlpaPVFHq0JJ7HzzAimob2hgzoENQ2UB_h5PpSqRqTgqG7dZHHSF4NQZIaCP0_ZAxIbIXmmZvU7hp01FLo55NjBc0HPlL?width=622&height=660&cropmode=none){: width="622" height="660"} 

五行十二宫中，又以长生、帝旺(或沐浴)及墓库三者为变化的主要阶段，因此三者便可组成一局：

|地支|寅申巳亥|子午卯酉|辰戊丑未|
|:--:|:--:|:--:|:--:|
||四长生|四帝旺、沐浴|四墓库|

根据五行局，定五行长生口诀：
> 金生巳、木生亥、火生寅、水土生申

另一口诀：
> 六五三四二、寅申亥巳申、阳男阴女顺排、阴男阳女逆排

![ziwei_13b](https://bnz06pap002files.storage.live.com/y4mQI1OmFjrFSMY8NfVV6aX7X37Ictp2c-5LlguQuWKfcuuQoQl9uBmvRF4e4Fkxo0xUnek40CvvB8dEJEoZ40EzkZeLAeYYy4HelXg1L05XB06SdQk-H4kEmyBk6H5fedGvI_-OkYfIQqmfN2e_dZlipZzn5-lzhZQPC0j_PFjgSTCBuQcK_kZq5rIGqO4aDJy?width=256&height=248&cropmode=none){: width="256" height="248"} 

解释：根据五行局数，确定长生宫位，阳男阴女顺行，阴男阳女逆行。依十二神顺序：长生、沐浴、冠带、临官、帝旺、衰、
病、死、墓、绝、胎、养。

由安星法可知，长生十二神定位取决于五项因素：命宫的位置、五行局、性别。农历丁亥年腊月初八寅时出生阴女，
金四局，长生位于巳宫，顺时针排列长生十二神。长生十二神用红色标识，目前的命盘如图：

![ziwei_13d](https://bnz06pap002files.storage.live.com/y4mkZIYgf-Y0GYCaIDPAr10_89vYRP7dS7X_e5NcQw9MSFO8V1fHT8Y07yXTl2Yvvqu0Ec05tFOu25lgWLA3ei7hO20ZpxREJYCItqBJW2sUHJJP98mwePkH3o6ssUjMdCpLwfu46gSyZWn1IGk9l-43kjCOhDewgC_GOZm6H-caPVjtAJ-loXxxZxeVOX8VxkV?width=1024&height=670&cropmode=none){: width="1024" height="670"} 

## 安博士十二神

博士十二神：博士、力士、青龙、小耗、将军、奏书、飞廉、喜神、病符、大耗、伏兵、官府，是紫微斗数中的丙级星。
博士十二神在本命盘中的作用不是太大，但是在流年命盘中的作用则举足轻重。

博士十二神歌诀：
> 博士聪明力士权、青龙喜气小耗钱、将军威武奏书福、飞廉口舌喜神延、病符大耗皆非吉、伏兵官府相勾缠

以出生年干定禄存起，分顺逆，阳男阴女顺行，阴男阳女逆行，依歌诀顺序，安生年博士十二神。
例如丁亥年腊月初八寅时出生阴女，禄存在午宫，顺时针安博士十二神。博士十二神用红色标识，目前的命盘如图：

![ziwei_14](https://bnz06pap002files.storage.live.com/y4m4MqcMFaTvWwDuQbSHxFsu-QZzH74LNZcPb-_HNISNImx30zzpmmdOSj8CAIYSZkogT3yAYdthMO9f_R70aEDVyLpu2DGHMOXeOGqXdCw8s96Ke6ADioA4oLEBWUY1pRIaqQXvTCOXFa-ZbxfwuXEuCr8gtSFAe8Q_VIvLxA6_I8t6maoi3Unxl0sZzvtR5xe?width=1024&height=671&cropmode=none){: width="1024" height="671"} 

## 安流年诸系星曜

**流年**是从每年的农历正月初一开始，到除夕结束；下一年正月初一又是一个新的流年。“流”字取取时间有川流不息之意，
来简易的表达每一年不同的运程。“流月”、“流日”和“流时”，也是跟“流年”是一样的，就代表每月、每日或每个时辰运程的变化。
所有流年星曜都不写入命盘，要于心中推算。此教程为方面学习，将其一一列出。

### 安流年太岁十二神

十二岁君又称十二神煞：岁建（太岁）、晦气、丧门、贯索、官符、小耗、岁破（大耗）、龙德、白虎、天德、吊客、病符。

![ziwei_15](https://bnz06pap002files.storage.live.com/y4mR7oP8prLik9b8Z8mcL-NmDnSb4dpwiiRJCUHw_JwqqEc0z35XfyQobdARe62UjZxz5-sDI0c3nbnAHOuiFDyJkItNWZQYUMkejw2m2GkG3iqf2ndpf9cd87_ts_0iB6OZJLKuiWa5EEo--eKI3nYVqoxTQ6FNux6iTdwYQ6tLyaR_qkZQIJCqKHbiStW7i5N?width=541&height=660&cropmode=none){: width="541" height="660"} 

太岁十二神歌诀：
> 太岁晦气丧门起、贯索官符小耗比、岁破龙德白虎神、天德吊客病符止

又有歌决：
> 太岁一年一替换、岁前首先是晦气、丧门贯索及官符、小耗大耗龙德继、白虎天德连吊客、病符居后须当记

解释：流年岁建宫位安在流年**地支**，例如农历2022年为**壬寅**年，地支为**寅**，岁建在寅宫，
该宫位就是**流年命宫**，再依顺时针方向安其余11颗流年岁前排列出**流年命盘**。2023年为**癸卯**年，
则**卯**宫为流年命宫。要查这一年中详细的运程，以流年太岁（岁建）宫作为本年的命宮，按兄弟、夫妻等十
二宫逆行安排，则一年中夫妻、子女、财帛等运程便可以推算。

以流年命宫就在寅宫为例，在实际应用中，本命亥宫以1开始算，顺时针走4个宫位到寅宫，那么其他十一宫依次以本宫为1开始算顺时针走4个宫位，
这样就能得到流年兄弟宫、流年夫妻宫、……，以此类推。计算宫位差的顺序并不重要，只要选宫位差小于7的方向即可。
因为十二宫位置是循环排列，顺时针的4个宫位（含本命宫和流命宫2个宫位），和逆时针的10个宫位（含本命宫和流命宫2个宫位），
是相同的位置。如果本命宫位，和流年支相同，则**流年命盘**就是本名盘。

此外三方宫位的判别。以（流）命宫为1开始，顺时针，逆时针分别数到5个宫位，这两宫分别是（流）财帛宫和（流）事业宫。
命宫的三方宫位是财帛宫和事业宫。兄弟宫三方宫位是田宅宫和疾厄宫，以此类推。找三方对宫位时，则根据子午相对，
丑未相对，寅申相对，卯酉相对，辰戊相对，巳亥相对，这样就找到了三方宫位，判断先天的命格都要结合三方宫位的吉凶星来综合判断。

农历丁亥年腊月初八寅时出生阴女，太岁十二神和流年宫位用红色标识，壬寅年的流年命盘如图：

![ziwei_15b](https://bnz06pap002files.storage.live.com/y4m4S05nS-kUFATxL_6e-rQF1CLV85jfKmNy8BkeSwVLnkKUbOhPrsVzCj0nTqVvuCIyi2NV3QFxibaaMhcEGGYz0Nx-9vPP5_tKbqIVRko5ZVAsza6XHu_RN-k3KN_waKXvwgyDnux377z5dEG7nkC7QGAhbG0c7w05czmNkh2dbDwI1FPXXTjgAr8S9H-SchH?width=660&height=507&cropmode=none){: width="660" height="507"}

注1：博士十二神中的大耗又叫天耗，小耗又叫地耗，而岁前十二神的大耗叫岁破，这些皆为流曜，而依生年支安星的大耗则不是流曜。

注2：岁前十二神中的小耗与博士十二神中的小耗不是同一颗星，但基本性质相同。

### 流年将前十二神

流年将前十二星包括：将星、攀鞍、岁驿、息神、华盖、劫煞、灾煞、天煞、指背、咸池、月煞、亡神。
将前十二神随**流年年支**发生变化，可以影响命主流年的运势，于该年流月、流日起作用。
具体牵动何事的变化，需要依据每个人不同的命盘具体解释。

![ziwei_16](https://bnz06pap002files.storage.live.com/y4mmj14o7QeTumGbFKaXHpzVgbvXsg3qe7gGLPAxENCCHgxVY8KTZMtLDxrk5kV4Ql4QfRPlRbHgRUy4TY6EohtmtqJSTDnrxN-C-wqFpCZkbdcZMJniPVZSQDt_ZckYQ9a91EAZZmtHNNZq58Vkc5yKSU0z4lJT6p2FNgCJuvhBfoy5lMi3Udu2OXfsbAaOA9_?width=605&height=660&cropmode=none){: width="605" height="660"} 

将前诸星口诀：
> 将星三合起旺地、攀鞍岁驿息神方、华盖劫灾天三煞、指背咸池月煞亡

又有安流年将前诸星歌诀曰：
> 寅午戌年将星午、申子辰年子将星、巳酉丑将酉上驻、亥卯未将卯上停、攀鞍岁驿并息神、华盖劫煞灾煞经、天煞指背或池续、月煞亡神次第行

解释：**将星**处地支三合局之旺地，即寅、午、戌三合火局见午；申、子、辰三合水局见子；巳、酉、丑三合金局见酉；
亥、卯、未三合木局见卯即为将星。所以将星都起于子午卯酉宫，将星是斗数中将前十二神之首，所谓将前，即是十二神由将星起，
其余星曜依次顺时针方向排列。

![ziwei_16b](https://bnz06pap002files.storage.live.com/y4mBVI-hc-zMkWU_RaIsMpsmhmzuIasLxC_ADQg6I4HDowO6u2YgePI2Nrds8kswSB_Hxa6TsiaZ8PFKeRk7FweOJ8Y_QUqv9s2zANA9iTkobg9d3LKPvGoI7BZy-qLU1qIPSte0gBd8h6XZNv6NgBfcECXzZKhpVwxbuSCvSJUlDLQupq-oil65bbe8hUewNzp?width=256&height=249&cropmode=none){: width="256" height="249"} 

流年将前十二星是由流年年支决定的，例如农历2023年为**癸卯**年，地支为**卯**，将前在卯宫。
2022年为**壬寅**年，地支为**寅**，将前在午宫。其余诸星顺时针排列。

农历丁亥年腊月初八寅时出生阴女，流年将前诸星用红色标识，**壬寅**年的流年命盘如图：

![ziwei_16c](https://bnz06pap002files.storage.live.com/y4moOMRV_l-KIcZ5IUeG_cBF7lDK46juIKjGv-C0EEhrtyOm5nOo2PdmSCi0pmlD18EFZj3P441KaUS-BHLn4k3l3zcBKaKy_djzA7eXzOywbRF9I--q9_T0yXn0nJTDOhbgN33dMRz_UIxSd0yq1QfpWPoTDB6wXksOAEaeXKT6G7RnAunPsXoidlC9Kh71dbj?width=660&height=507&cropmode=none){: width="660" height="507"}

### 安流昌流曲

流昌、流曲星的排法则与命盘昌曲星的排法不同，昌曲星乃时系星,它是以本命的生时支排列的,而流昌星则是由**流年年干**排定的。

![ziwei_17b](https://bnz06pap002files.storage.live.com/y4mNp-6jywol7EiFkpIlHiNuZzi7JFm3ZuhSljSVs7BqhtfIupiU4Tt9zjUttC7EvRI9pzHjtrurMJvf-17iYRt_8kdOSaxBMtYplgheHTQ6Tlw9fDedix40iNK-scv8_kMMFpcmIfLaIZB3OoVQU4FiWAN-tBVpfmjaoSbHfuaqHSnlRaHr2Ncgea31qvReY1U?width=660&height=141&cropmode=none){: width="660" height="141"} 

安流曲、流昌口诀：
> 流昌起巳位、甲乙顺流去、不用四墓宫、日月同年岁、流曲起酉位、甲乙逆行踪、亦不用四墓、年日月相同

![ziwei_17](https://bnz06pap002files.storage.live.com/y4m_FDJDCcyDg5LcE-gSvT2cMkqP6RabAnb7vrSV9ORsVOGDQe3ny_rWB_QuFHnJJd5hP9To9eg2baeoqMpEpB3JKKdFEEtGpjTIayGCq044OlLLgtn20Ac77rFqxHqA0I7rDzyvAlD0gfAbwFLntBSrTDGgUQgmuj9Dk2uW26p459edJKudVnIBUJTUQRHIS4h?width=660&height=312&cropmode=none){: width="660" height="312"} 

解释：两诀末句，谓流年流月流日流时之流昌流曲，均依天干取。例如农历2023年为**癸卯**年，流年年干为**癸**，
流昌在卯宫，流曲在亥宫。2022年为**壬寅**年，流年年干为**壬**，流昌在寅宫，流曲在子宫。

### 安流年干系流星

流年干系流星有流禄星(流年禄存星)、流羊星(流年擎羊星)、流陀星(流年陀罗星）、流魁星(流年天魁星)、和流钺星(流年天钺星)等星曜。
流年星的排法与排命盘时相似,只是流年干系流星系以**流年年干**排列，排命盘则以生年干排列。

根据**[「安年干系属诸星」](#ref07)**章节中的方法，农历农历丁亥年出生，出生年干位**丁**，禄存在午宫，擎羊在未宫，
陀罗在巳宫，天魁在亥宫，天钺在酉宫。2022**壬寅年**，流年年干为**壬**，可知流禄在亥宫，流陀在戌宫，
流羊在子宫，流魁在卯宫，流钺在巳宫。

### 安流「四化」星

推算流年尚需以**流年干**为依据的流年四化星：流化禄、流化权、流化科、流化忌，其排法则与生年[「安四化星」](#ref06)相似，
但生年四化星以**生年干**为依据，而流年四化星系以**流年干**为依据。

农历农历丁亥年出生，出生年干位**丁**，化禄、化权、化科、化忌，分别为太阴，天同，天机，巨门；2022**壬寅年**，
流年年干为**壬**，流四化星，禄、权、科、忌分别在天梁、紫薇、天府、武曲。

### 安流年支系流星

流年支系流星有流马星(流年天马星)、流鸾星(流年红鸾星)和流喜星（流年天喜星）等星曜，
它们的排法与排命盘时[「安年支系诸星」](#ref08)相同,只是流年支系流星是以**流年支**为依据，
命盘则以生年为依据。

农历农历丁亥年出生，出生年支位**亥**，天马、红鸾和天喜分别在巳宫、辰宫和戌宫；
2022**壬寅年**，流年年支为**寅**，流马、流鸾和流喜分别在申宫、丑宫和未宫。

农历丁亥年腊月初八寅时出生阴女，流曜诸星用红色标识，**壬寅**年的流年命盘如图：	

![ziwei_17c](https://bnz06pap002files.storage.live.com/y4mYYEK4tmROvyKtHLXBATxTX3fy0nno3QPADmbglPJYCT2EfyPolGIj-jj-WAVdmZsZojoz-qNnUlQ01KrInB6Sf_TEmnD3s37IkysSYLYx9EQ3S-o5gDgrDUao13JQbuZWpzyD1dHJ_8Qi-kVS0mYDkLrCDA93N8CU_fAWuR3alWBkvcHqvefPpl-L51H_4G4?width=660&height=507&cropmode=none){: width="660" height="507"} 

## 安小限、命主、身主、斗君

### 定小限

![ziwei_18](https://bnz06pap002files.storage.live.com/y4mkw1NHqzLt2NsbrW1wdwefayFN_Sl_JWsv1EskdDKFMh6qaXMD6M6Gj1gCx0hlIaIHwhoCsQCJCGXWnSQ6yxKcTLVyWDZFI4RHHvkHDVj122ixGLIm0GMu1-nVmNc03wtu6uw2LUErONgMwdio8lrWToj1SEhlSM-Z8KJ36LatMV8Wx2OS1NUvPxRq7DABoZm?width=506&height=660&cropmode=none){: width="506" height="660"} 

根据**生年年支**定小限口诀：
> 先将生年分四局、墓库冲处小限起、男顺女逆一路行、不轮阴阳各排比

![ziwei_18b](https://bnz06pap002files.storage.live.com/y4mzygOa4TB1TNDBkQCOsG1sWrz75vuOLVvflce3EE6XpyY2TP4vcUt0jAdqVTwinyqx8hsj7EmUhT_MgOCV5e11nRvDHUFA1fgR-0rtNjfwtSwZaE66WN-g-DHDW2-GVNp3CY3wfG1R7KhWACMOgAC3l6p-bIMf88qSB0qUzo8Ds_2gp0QjAgj_D46KfxRvILa?width=251&height=256&cropmode=none){: width="251" height="256"} 

解释：寅午戌人，戌墓冲辰，小限一岁由辰宫起；亥卯未人，未墓冲丑，小限一岁由丑宫起；申子辰人，辰墓冲戌，小限一岁由戌宮起；
巳酉丑人，丑墓冲未，小限一岁由未宫起。男命顺行，女命逆行，不分阴阳。例如丁亥年出生，小限一岁由丑宫起。

农历丁亥年腊月初八寅时出生阴女，小限用红色表示，命盘如图：

![ziwei_18c](https://bnz06pap002files.storage.live.com/y4mhPJOa9wNdLsKOALFl4YraqDaJm8CGPD6kyudsG8nZG44Zu35MR1R9YD7KonQg1eECEXhH9rIH967qSloEMLVvmlDLOEQXNdVYZPOxaRAGv7vTMfbgoWvGvl00ru6qjRI8008Ws2dKA2l7pvDAR1S7XtTpDcPQdFB1-0Y_kkxmQ1XHl3wmkMtQci2YxK4RKqs?width=1024&height=670&cropmode=none){: width="1024" height="670"} 

图中小限只显示一岁至12岁，其它小限可以分别加上12的倍数可得。

### 安命主、身主

![ziwei_18c](https://bnz06pap002files.storage.live.com/y4mbG1XghIcbsLVsrpGbGDKPmv8XBxfp9ufzKt593ecWFkcHUZU9hL_YFe4O2YO54kuZOktS_srl7gIlHArnbOX7iGBeYMe2vKgnh_ekNH66xUdyPGq2NhsOsYK438cdWY7bpwcfbUD8LibR18fNPGfvE7U97-f7gn3GmlRll0X2SoXg4cygAjpyWuQwbLMDpNe?width=660&height=201&cropmode=none){: width="660" height="495"} 

根据生年年支安命主口诀：
> 子属贪狼丑亥门、寅戌生人属禄存、卯酉属文巳未武、辰申廉宿午破军

根据生年年支安身主口诀：
> 子午安身铃火宿、丑未天相寅申梁、卯酉天同身主是、巳亥天机辰戌昌

解释：例如亥年出生，根据口诀命主在巨门，身主在天机。

### 安斗君

![ziwei_18d](https://bnz06pap002files.storage.live.com/y4ma8YCWAOXhDjxXIzNJxm0kiAYjs8GDRqgQC0_wrwl1-QcGE877t5dUD0UNnia5bMUC2UdR5lPK7j8dFu3pbp0_rvK-x3VbVihSYXPUcjJ9ArEuomIGaRbUtZhk2M0BwJoyOocfSCtDrZD40sbXM8spXG2WAwAjKtoXa4SewC5TE4ubKqQbCZBrDPnqerwBZg_?width=481&height=660&cropmode=none){: width="481" height="660"} 

注：此表只起子年斗君。

根据生月生时安斗君口诀：
> 太岁宫中便起正、逆回数至生月停、此宫顺流子时位、流于生时安斗君

解释：子年斗君是根据本命的生月和生时所排定的。**子年斗君**所在的宫位是固定的，它不会因每年的流年而有所改变。
安子年斗君的方法如下：先由命盘中的子宫起正月，逆时针数至生月宫止，再顺时针由子时起算，数至生时宫为止，安下子年斗君。

例如推算腊月寅时生人的子年斗君，于子宫起正月逆行，亥宫二月，……，直到丑宫腊月，于丑宫起子时顺回，寅宫丑时，
卯宫寅时，得子年斗君在卯宫。

安流年斗君方法一：以流年命宫（流年太岁，流年年支）起正月，逆时针数至生月所落的宫位，再由此宫位起子，顺时针数至生时支的宫位，
即是流年斗君所在的宫位。例如推算腊月寅时生人的壬寅年流年斗君，于寅宫起正月逆行，丑宫二月，……，直到卯宫腊月，
于卯宫起子时顺回，辰宫丑时，巳宫寅时，得壬寅年流年斗君在巳宫。

安流年斗君方法二：根据子年斗君所在宫位的地支起子，依顺时针方向起算，数至该流年的地支宫位为止，即为安流年斗君的宫位。
例如已知腊月寅时生人的子年斗君在卯宫，推算壬寅年流年斗君，在卯宫起子，顺数至寅，流年斗君落在巳宫。

## 流月流日流时命宫定法

推算流月，是以**流年斗君**所在宫位为正月命宫，顺时针排列流月命宫。例如子年斗君在午，则丑年斗君排在未，因些丑年正月便以未宫起宫。
又如寅年斗君在申，则寅年正月在申宫，如此类推。但是推流月时，流四化则以**流月之天干**来决定。
例如某命流年乙丑年三月，假设子年斗君在午，则丑年斗君在未宫起正月，申二月，酉三月，流月命宫在酉。
但天干则以乙年（五虎遁月诀中「**乙庚之岁戊为头**」）起戊寅（正月）、己卯（二月）、庚辰（三月）。
故推命时虽流月之命排在酉宫，但四化仍按庚辰月算，即「**庚阳武府同**」。

现行农历置闰，每隔两年到三年，就必须增加一个与上一个月相同的农历月份，增加的这个月叫闰月。如遇闰月，
则闰月以前半月属上月，下半月属下月推算（注：有些派别则统归下月）。

流日推算法是以流月命宫起初一，顺数回命宫为十三、廿五等。干支则以万年历中当日之干支来推各流曜。闰月之推法，
例如三月有闰月，则三月顺数卅日后加上闰月前半月之十五日，共四十五日顺推，四月也是另起初一后，以四十五日顺推。
例如三月在酉宫，则三月十五日在亥宫，因三月初一在酉，初二在戌，初三在亥，……，顺至十三在酉，十四在戌，十五在亥宫。

流时推算法是以流日命宫起子时，顺数至亥时，流时四化以流时的干支算。

**五虎遁法**用来推演月干，在**[「起寅首」](#ref02a)**的章节中已经介绍过；**五鼠遁法**用来推演时干。
天干是从甲开始，地支是从子开始，每天的十二个时辰从子时开始，但每年的正月从寅月开始，二月为卯月，……，以此类推。
而子月还是前一年的冬天、又叫冬月，立春以后就是寅月。

寅属虎，子属鼠，在六十甲子循环中，每个天干出现六次，每个地支出现五次，也就是说，寅或子只出现五次，所以叫五虎或五鼠。

日上起时法口诀：
> 甲己还加甲、乙庚丙作初、丙辛从戊起、丁壬庚子居、戊癸何方发，壬子是真途

解释：甲己还加甲，是讲的甲日，已日的子时起甲子时，这甲子，就是甲日己日子时的名称。其法与年上起月法相同。
至于甲日，或者己日的名称，是从万年历上查到的，然后按查到的日子名称，再根据其日干来查时上的名称。
这样，只要知道了每一天“子”时的名称，以下各时的名称按表顺查就知道了。

![ziwei_18f](https://bnz06pap002files.storage.live.com/y4mWNAnpqYFVzD1fx2IdPz_YZoi1DlqarX02s_aqj2KUVXD8BfGupV_pRCjmxWAWV-vgaCBUHl2gklVmFNOXAIsrZCriSHhTjXktleUwYW-pR7FlDbpRduKAeC1DKPuET71uxHRdI7dexRtRrqsWCCRlfTIH55XW9rviXCmR4yORrBA23kuK6ypOoNeFhM40Lto?width=660&height=632&cropmode=none){: width="660" height="654"} 

快速计算日上起时法：

$$(生日天干数字 \times 2 - 1) \bmod 10$$

（即按十天干排位数：1甲、2乙、3丙、4丁、5戊、6己、7庚、8辛、9壬、10癸）
例如：日干为己的时候，$$(6\times2-1) \bmod 10 = 1$$，1是甲，子时从甲起。
又例：日干为戊的时候，$$(5\times2-1) \bmod 10 = 9$$，9是壬，子时就是壬子。其它类推。


## 安诸星庙陷

![ziwei_19](https://bnz06pap002files.storage.live.com/y4mKvHk8cBo6ZT-KRGhsABCH2PgfU18-xFyqJE3w5fnrcRa9Riwxm8CmSMrA1kzrVwScIbHA5Gk4H8YRlgbfPr5XnVIhJkHlEgOFIX5PY6-5WWjuACu8B6vxiRmn2Xp_YedjZEje0Jm_FLR5sKCnkcKHHc_RsGKt89ouDyEEhCHHUZcuySA4j9UWYMUx0pvrnSC?width=1024&height=542&cropmode=none){: width="1024" height="542"} 


农历丁亥年腊月初八寅时出生阴女，诸星庙陷用红色表示，命盘如图：

![ziwei_19b](https://bnz06pap002files.storage.live.com/y4m1IAwvGzmH8N3KXWrE75ALb9Y9KPXFyCgv-PC6QPcTTENSqG2iZp5-GI797CH8iXOIwvodSMLWhwzpT-gNFGZBk7akPkUG6Nwo-pBdxnrtv23GsuJSGlC_a11o54YnKDFWDUgTPU3Wc7c2l034r81CXp3l3vYj78LXvmFGbUYhV4jSUfkn7WfUrf22jJ_J4t7?width=1024&height=670&cropmode=none){: width="1024" height="670"} 

## 基本术语

+ 正曜：紫微天府等十四主星
+ 辅曜：左辅右弼天魁天钺
+ 佐曜：文昌文曲禄存天马
+ 煞曜：擎羊陀罗火星铃星称为四煞，加上地空地劫，称为六煞
+ 空劫：地空地劫
+ 化曜：化禄，化权，化科，化忌
+ 三奇：指化禄、化权、化科
+ 空曜：指地空地劫天空，截空旬空亦可作空曜，但力量较弱
+ 刑曜：擎羊及天刑
+ 忌曜：化忌及陀罗
+ 桃花诸曜：红鸾天喜，咸池大耗，天姚沐浴六颗，廉贞贪狼虽有桃花性质，但入正曜系列
+ 文曜：文昌文曲，龙池凤阁，天才，化科
+ 科名诸曜：除上述文曜外，加上三台八座，恩光天贵，台辅封诰，天官天福八颗
+ 本宫：是一种代名词，研究命宫则以命宫为本宫，研究夫妻宫则以夫妻宫为本宫，命盘十二宫皆可为本宫。
+ 对宫：面对本宫的宫位，在论本宫的吉凶时，对宫具有相当大的影响力，其重要性次于本宫。
+ 合宫：与本宫地支，有三合关系的宫位，三宫相并而成。巳酉丑三合；亥卯未三合；申子辰三合；寅午戌三合。
+ 三方：本宫的三合宫，加上本宫的对宫，共三个宫位，称三方。如以子宫为本宫，则三合宫为辰宫、申宫，加上子宫的对宫午宫，辰、申、午三宫为子宫的三方。
+ 四正：指本宫加上三方，合称四正。一般所言“四正”，均是指此。另外，寅、申、巳、亥四宫，亦谓“四正”之地，盖取其正方形命盘之四角，故也称四正之位。命盘之四正，又称“四生”、“四马”之地，盖长生及天马星只入寅、申、巳、亥宫。是以一个命盘有两种“四正”，不可混淆。
+ 邻宫：指位于本宫前一位与后一位的二宫而言，其主要作用在辅助本宫。如以命宫为本宫，则父母宫、兄弟宫为邻宫。就本宫而言，邻宫所具有的影响力，不及对宫与三合宫来得重要，但在特殊情况下例外。
+ 暗合宫：指是与本宫地支成六合的宫位。暗合宫主要作为辅助之用，只限于在特殊情况下采用，不能用在一般的情形上。
+ 天罗地网：天罗指命盘中的辰宫，地网指命盘中的戌宫。
+ 加会：指本宫、对宫、三合宫中的某些星曜会合而言。本宫、对宫、三合宫可视为一个整体进行论断，此点尤其在推断命宫吉凶时，就显得分外重要。
+ 守照：某星坐于本宫曰守，照指本宫之三合宫及对宫之星曜与本宫所发生之感应。
+ 杀破狼：指七杀、破军、贪狼三星，永远在命盘上互相会照，成三合的关系。
+ 四生、四败、四墓：四生之地指命盘中的寅申巳亥宫，此为五行长生之处；四败之地指命盘中的子午卯酉宫，此为五行沐浴之处；四墓之地指命盘中的辰戌丑未宫，此为五行入墓之处。
+ 庙（灿烂）：星曜最明，得数最强，吉曜极吉，凶曜不凶。
+ 旺（光辉）：星曜次明，得数次强，吉曜吉，凶曜不凶。
+ 得地（光明）：星曜光明，得数适度，吉曜仍吉，凶曜不凶。
+ 利益（尚明）：星曜尚明，得数渐弱，吉曜尚吉，凶曜渐凶。
+ 平和（微明）：星光已低，得数已弱，吉曜力微，凶曜肆凶。
+ 不得地（已暗）：星光已暗，得数最弱，吉曜无力，凶曜愈凶。
+ 落陷（暗黑）：星曜无光，无数可得，吉曜无用，凶曜最凶。

注：中州派分为庙旺平闲陷五级。

## 总结

并不要求记住每颗星的排法，但最好必须掌握的内容。

1. 真太阳时
2. 天干地支阴阳五行属性
3. 安命身宫，天干五虎遁，定五行局，起大限
4. 起紫微星的方法，十二基本盘的排布
5. 四化表，尤其重要
6. 安左辅右弼天魁天钺文昌文曲的方法
7. 安禄存天马擎羊陀罗地空地劫火星铃星的方法
8. 安斗君的方法

## 参考文献

+ 紫微斗数。[https://zh.wikipedia.org/wiki/紫微斗数](https://zh.wikipedia.org/wiki/%E7%B4%AB%E5%BE%AE%E6%96%97%E6%95%B0){: target="_blank"}.
{: id="refa"} 
+ 干支。 [https://zh.wikipedia.org/zh-hans/干支](https://zh.wikipedia.org/zh-hans/%E5%B9%B2%E6%94%AF){: target="_blank"}.
{: #refb}
+ 纳音。 [https://zh.wikipedia.org/wiki/纳音](https://zh.wikipedia.org/wiki/%E7%B4%8D%E9%9F%B3){: target="_blank"}.
{: #refc}
+ 中州派紫微斗数讲义--初级讲义，王庭之，紫微文化服務社。
+ 新锓希夷陈先生紫微斗数全书， 明代南阳堂（或 葆和堂）写刻刊本


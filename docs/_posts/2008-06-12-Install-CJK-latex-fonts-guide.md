---
layout: post
title: "Install CJK Latex Fonts Guide"
toc: true
categories:
  - Tech
tags:
  - software
  - linux
date:   2008-06-12
---

Basically, I am going to explain you how to install Chinese fonts for Latex on 
a linux system. I had a very old system SuSE 9.1 running on my Toshiba laptop.

## Prerequisite

Research before installation shows that prerequisites are: **`TeX/e-Tex/Latex`**, 
**`CJK`** and **`freetype1`** packages. The packages I was using all came with 
**`SuSE9.1`**: 

+ Tex(web2c) of v7.4.5
+ CJK of v4.5.2 
+ freetype of v1.3

Please note that these packages may come in different name according to your 
very own linux distribution and version. It's your responsibility to have 
a working CJK latex before you proceed this tutorial.

## Acquire the font you want to install

Obtain the chinese truetype fonts you would like to install. TrueType fonts are 
scalable which means the glyphs can be displayed at any resolution and any point 
size (though the glyphs may not look good in extreme cases). A TrueType font is 
a binary file containing a number of tables. TrueType is not standardized. It 
is an evolving specification with at least three groups working on it and 
changing it in different ways. The major players are Apple, Microsoft and Adobe. 
None of these is entirely consistent with the others.

What I had here is **`Hua Kang`** Hand writing fonts in 6 styles of ttc format. 
A **`TrueType Collection`** file, or **`TTC`** file, is a collection of 
truetype fonts. From Microsoft's web site: 

A TrueType Collection (TTC)
: a means of delivering multiple TrueType fonts in a single file structure. 

TrueType Collections are most useful when the fonts to be delivered together 
share many glyphs in common. By allowing multiple fonts to share glyph sets, 
TTCs can result in a significant saving of file space. There is a program called 
**`ttc2ttf`**, but you don't have to convert.

## Understand the fonts

Most TrueType fonts have more than one native mapping table, also called 
**`cmap'**, which maps the (internal) **`TTF`** glyph indices to the (external) 
**`TTF`** character codes. Possible platform are: 

+ Apple Unicode=0
+ Macintosh=1
+ ISO=2
+ Microsoft=3 

For each of the platform mentioned here, there are different encoding scheme, 
in another word, encoding depends on the platform. For example, Microsoft encode 
with Symbol=0, Unicode 2.0=1, Shift JIS=2, GB 2312 (1980)=3, Big 5=4, 
KSC 5601 (Wansung)=5 and KSC 5601 (Johab)=6.

## Subfont definition file

**`CJKV`** (Chinese/Japanese/Korean/old Vietnamese) fonts usually contain 
several thousand glyphs. To use them with TeX it is necessary to split such 
large fonts into subfonts. Subfont definition files (usually having the 
extension **`SFD`**) are a simple means to do this smoothly. The **`SFD`** files 
in the distribution are customized for the CJK package for LaTeX. You have to 
embed the **`SFD`** file name into the **`TFM`** font name surrounded by two 
**`@`** signs. **ttf2tfm** will create all subfont **`TFM`** files specified 
in the **`SFD`** files (provided the subfont contains glyphs) in one run, 
*i.e.*, it will build TeX metric files from a TrueType font.

## Install and configure the fonts

### Save the truetype fonts

You need to put your truetype fonts into the following directory (hkzhu.ttc is 
my interested TTC file):

~~~bash
/usr/share/texmf/fonts/truetype/hkzhu.ttc 
~~~

### Build TeX metric files from a TrueType font

**`ttf2tfm`** command will read in the **`TTC`** fonts file (hkzhu.ttc) and 
decompose it into **`TFM`** subfont files according to UBig5 **`SFD`** (Subfont 
Definition Files). -P takes platform-ID, -E takes encoding ID. Valid Microsoft 
fonts should have a (**`3,1`**) mapping table, but some fonts exist (mostly 
Asian fonts) which have a (**`3,1`**) cmap not encoded in Unicode. The reason 
for this strange behavior is the fact that some MS Windows versions will reject 
fonts having a non-((**`3,1`**)) cmap (since all non-Unicode Microsoft encoding 
IDs are for Asian MS Windows versions). For **`hkzhu.ttc`**, it has (**`3,1`**)
cmap but the characters are actually encoded in Big5 encoding.

-P platform-id
: The TrueType platform ID. Default value of this non-negative integer is 3.

-E encoding-id
: The TrueType encoding ID. Default value of this non-negative integer is 1.

-q
: Make ttf2tfm quiet. It suppresses any informational output except warning and 
error messages. For CJK fonts, the output can get quite large if you don't 
specify this switch.

Here, the output **`SFD`** file name is embeded into the **`TFM`** font name 
surrounded by two **`@`** signs. Then, type the following command: 

~~~bash
$ mkdir -p /usr/share/texmf/fonts/tfm/hk/hkzhu/ #(hk/hkzhu is my customerized directory to hold subfont TFM files)
$ cd /usr/share/texmf/fonts/tfm/hk/hkzhu/
$ ttf2tfm /usr/share/texmf/fonts/truetype/hkzhu.ttc -P 3 -E 1 -q hkzhu@/usr/share/texmf/ttf2tfm/UBig5@
~~~

Finally, I want to produce the rotated glyphs and slant font, -s will specify 
obliqueness factor, -x will rotate glyph 90 degree counter-clockwise.

-s slant-factor
: The obliqueness factor to slant the font, usually much smaller than 1. 
Default of this real number is 0.0; if the value is larger than zero, the 
characters slope to the right, otherwise to the left.

-x
: Rotate all glyphs by 90 degrees counter-clockwise. If no -y parameter is given, 
the rotated glyphs are shifted down vertically by 0.25em.

~~~bash
$ ttf2tfm /usr/share/texmf/fonts/truetype/hkzhu.ttc -P 3 -E 1 -s 0.167 -q hkzhus@/usr/share/texmf/ttf2tfm/UBig5@
$ ttf2tfm /usr/share/texmf/fonts/truetype/hkzhu.ttc -P 3 -E 1 -x -q hkzhur@/usr/share/texmf/ttf2tfm/UBig5@
4 ttf2tfm /usr/share/texmf/fonts/truetype/hkzhu.ttc -P 3 -E 1 -s 0.167 -x -q hkzhurs@/usr/share/texmf/ttf2tfm/UBig5@
~~~


### Add entries to ttfonts.map

edit **`/etc/ttf2pk/ttfonts.map`** with your faverite editor such as vi/emacs, 
add the following lines into your **`ttfonts.map`**:

~~~bash
hkzhu@UBig5@ hkzhu.ttc Pid=3 Eid=1
hkzhus@UBig5@ hkzhu.ttc Slant=0.167 Pid=3 Eid=1
hkzhur@UBig5@ hkzhu.ttc Rotate=Yes Pid=3 Eid=1
hkzhurs@UBig5@ hkzhu.ttc Rotate=Yes Slant=0.167 Pid = 3 Eid = 1
~~~

### Generate the font definition files 

Create new files **`/usr/share/texmf/tex/latex/CJK/Bg5/c00hkzhu.fd`** as: 

~~~bash
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
% This is the file c00hkzhu.fd of the CJK package
% for using Asian logographs (Chinese/Japanese/Korean) with LaTeX2e
%
% created by Quan Zou (10-June-2008)
\def\fileversion{4.5.2}
\def\filedate{2008/06/10}
\ProvidesFile{c00hkzhu.fd}[\filedate\space\fileversion]
% simplified Chinese characters
%
% character set: Big 5
% font encoding: CJK (standard)
% Huan Kang fonts Zhu Style Traditional Chinese
\DeclareFontFamily{C00}{hkzhu}{\hyphenchar \font\m@ne}
\DeclareFontShape{C00}{hkzhu}{m}{n}{<-> CJK * hkzhu}{}
\DeclareFontShape{C00}{hkzhu}{m}{sl}{<-> CJK * hkzhus}{}
\DeclareFontShape{C00}{hkzhu}{m}{it}{<-> CJKssub * hkzhu/m/sl}{}
\DeclareFontShape{C00}{hkzhu}{bx}{n}{<-> CJKb * hkzhu}{\CJKbold}
\DeclareFontShape{C00}{hkzhu}{bx}{sl}{<-> CJKb * hkzhus}{\CJKbold}
\DeclareFontShape{C00}{hkzhu}{bx}{it}{<-> CJKssub * hkzhu/bx/sl}{\CJKbold}
\endinput
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
and /usr/share/texmf/tex/latex/CJK/Bg5/c00hkzhur.fd for rotated fonts:
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
% This is the file c00hkzhur.fd of the CJK package
% for using Asian logographs (Chinese/Japanese/Korean) with LaTeX2e
%
% created by Quan Zou (10-June-2008)
\def\fileversion{4.5.2}
\def\filedate{2008/06/10}
\ProvidesFile{c00hkzhur.fd}[\filedate\space\fileversion]
% simplified Chinese characters
%
% character set: Big 5
% font encoding: CJK (standard)
% Huan Kang fonts Zhu Style Traditional Chinese, rotated
\DeclareFontFamily{C00}{hkzhur}{\hyphenchar \font\m@ne}
\DeclareFontShape{C00}{hkzhur}{m}{n}{<-> CJK * hkzhur}{}
\DeclareFontShape{C00}{hkzhur}{m}{sl}{<-> CJK * hkzhurs}{}
\DeclareFontShape{C00}{hkzhur}{m}{it}{<-> CJKssub * hkzhur/m/sl}{}
\DeclareFontShape{C00}{hkzhur}{bx}{n}{<-> CJKb * hkzhur}{\CJKbold}
\DeclareFontShape{C00}{hkzhur}{bx}{sl}{<-> CJKb * hkzhurs}{\CJKbold}
\DeclareFontShape{C00}{hkzhur}{bx}{it}{<-> CJKssub * hkzhur/bx/sl}{\CJKbold}
\endinput
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
~~~

### Create ls-R databases

**`mktexlsr`** is used to generate/rebuild the ls-R databases used by the 
**`kpathsea`** library, which performs path searching. If one or more arguments
DIRS are given, these are used as the directories in which to build ls-R. Else 
all directories in the search path for ls-R files ($TEXMFDBS) are used.

~~~bash
$ sudo mktexlsr
~~~

### Write a CJK latex file

create a test file by the this keyword:

~~~bash
% This is the file Big5.tex of the CJK package
%   for testing Chinese (in Big 5 encoding).
%
% written by Werner Lemberg <wl@gnu.org>
%
% Version 4.5.1 (17-Jun-2002)
%
%
% process this file with bg5latex

\documentclass[12pt]{article} 

\usepackage{CJK}


\begin{document}

\begin{CJK*}{Bg5}{hkzhu}
\CJKtilde

\noindent 本常問問答集~(FAQ list)~是從一些經常被問到的問題及其適當的解
答中，以方便的形式摘要而出的。跟上一版不同的是，其編排結構已徹底改變。
\textbf{有關新結構的細節，可參考「如何閱讀本問答集及了解其編排結構」該
項中的說明。}

\end{CJK*}

\end{document}

%%% Local Variables:
%%% coding: big5
%%% mode: latex
%%% TeX-master: t
%%% TeX-command-default: "CJKLaTeX"
%%% End:
~~~

remember to compile the tex with **`bg5latex`**. The final results is shown as 
following:

![CJK_Big5](https://bn1303files.storage.live.com/y4mkzH5bRAYyKsztuY8FR48LtL3zpSKCe0n_NYeqX-V3T_dDk-emDb4vXNCLB2VqKw3vrYseHpb-jf2hCnYWEYySoiQQrzXRE_yAqc4qfM_llJ9veshbjBdoyhxecNh9Xb1VSUqEuaW0tLm3HhXWWKhV1KqAO72AIWVzqPv3YKDWTNjHx-jGk_d3Y4Tll_JkjWX?width=550&height=80&cropmode=none){: width="550" height="80"}

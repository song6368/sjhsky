# sjhsky

#!/usr/bin/env python
# coding: utf-8

import pandas as pd
from matplotlib import pyplot as plt

url = "http://www.seoul.go.kr/coronaV/coronaStatus.do"

pd.read_html(url) # url읽어오기

table = pd.read_html(url) # 데이터 프레임으로 생성

# 이후 전처리
df1 = table[0]

df2 = df1.iloc[3:5]

df2.columns = ["마포구", "양천구", "강서구", "구로구", "금천구", "영등포구", "동작구", "관악구", "서초구", "강남구", "송파구", "강동구", "기타"]

df1 = df1.drop(df1.index[2:5])

df = pd.concat([df1, df2])
df["마포구"][0] = df["마포구"][3]
df["양천구"][0] = df["양천구"][3]
df["강서구"][0] = df["강서구"][3]
df["구로구"][0] = df["구로구"][3]
df["금천구"][0] = df["금천구"][3]
df["영등포구"][0] = df["영등포구"][3]
df["동작구"][0] = df["동작구"][3]
df["관악구"][0] = df["관악구"][3]
df["서초구"][0] = df["서초구"][3]
df["강남구"][0] = df["강남구"][3]
df["송파구"][0] = df["송파구"][3]
df["강동구"][0] = df["강동구"][3]
df["기타"][0] = df["기타"][3]
df["마포구"][1] = df["마포구"][4]
df["양천구"][1] = df["양천구"][4]
df["강서구"][1] = df["강서구"][4]
df["구로구"][1] = df["구로구"][4]
df["금천구"][1] = df["금천구"][4]
df["영등포구"][1] = df["영등포구"][4]
df["동작구"][1] = df["동작구"][4]
df["관악구"][1] = df["관악구"][4]
df["서초구"][1] = df["서초구"][4]
df["강남구"][1] = df["강남구"][4]
df["송파구"][1] = df["송파구"][4]
df["강동구"][1] = df["강동구"][4]
df["기타"][1] = df["기타"][4]
df.drop(df.index[2:4])


# GUI작성 시작
from tkinter import *
from tkinter import ttk
from tkinter import messagebox

win = Tk ()
win.title("코로나 감염자 현황")
win.geometry('700x200+200+200')

# 해당 구 검색시 현황 띄워주는 메소드
def clickMe1():
    try : #예외처리
        str1 = df[str.get()].iloc[0];
        str2 = df[str.get()].iloc[1];
        messagebox.showinfo("현황", str.get()+"\n현재 감염자 수: "+str1+"\n금일 감염자 수: "+str2);
    except :
        messagebox.showinfo("에러", "오류입니다.");

str = StringVar()

textbox = ttk.Entry(win, width=20, textvariable=str)

textbox.grid(row = 1, column = 0)

button0= Button(win, text="확인", command=clickMe1)

label2 = Label(win, text = "구를 입력해주세요\n(버튼 클릭 시 해당 구 현황 출력)")
label2.grid(row=0, column = 0)

def clickMe2(self) :
    messagebox.showinfo("현황", self+" 현재 감염자 수: "+df[self].iloc[0]+"\n금일 감염자 수: "+df[self].iloc[1]);
    
    
# 각 구별 버튼 생성
button1= Button(win, text="종로구", command=lambda: clickMe2('종로구'))
button2= Button(win, text="중구", command=lambda: clickMe2('중구'))
button3= Button(win, text="용산구", command=lambda: clickMe2('용산구'))
button4= Button(win, text="성동구", command=lambda: clickMe2('성동구'))
button5= Button(win, text="광진구", command=lambda: clickMe2('광진구'))
button6= Button(win, text="동대문구", command=lambda: clickMe2('동대문구'))
button7= Button(win, text="중랑구", command=lambda: clickMe2('중랑구'))
button8= Button(win, text="성북구", command=lambda: clickMe2('성북구'))
button9= Button(win, text="강북구", command=lambda: clickMe2('강북구'))
button10= Button(win, text="도봉구", command=lambda: clickMe2('도봉구'))
button11= Button(win, text="노원구", command=lambda: clickMe2('노원구'))
button12= Button(win, text="은평구", command=lambda: clickMe2('은평구'))
button13= Button(win, text="서대문구", command=lambda: clickMe2('서대문구'))
button14= Button(win, text="마포구", command=lambda: clickMe2('마포구'))
button15= Button(win, text="양천구", command=lambda: clickMe2('양천구'))
button16= Button(win, text="강서구", command=lambda: clickMe2('강서구'))
button17= Button(win, text="구로구", command=lambda: clickMe2('구로구'))
button18= Button(win, text="금천구", command=lambda: clickMe2('금천구'))
button19= Button(win, text="영등포구", command=lambda: clickMe2('영등포구'))
button20= Button(win, text="동작구", command=lambda: clickMe2('동작구'))
button21= Button(win, text="관악구", command=lambda: clickMe2('관악구'))
button22= Button(win, text="서초구", command=lambda: clickMe2('서초구'))
button23= Button(win, text="강남구", command=lambda: clickMe2('강남구'))
button24= Button(win, text="송파구", command=lambda: clickMe2('송파구'))
button25= Button(win, text="강동구", command=lambda: clickMe2('강동구'))
button26= Button(win, text="기타", command=lambda: clickMe2('기타'))

button0.grid(row = 2, column = 0)
button1.grid(row = 2, column = 1)
button2.grid(row = 2, column = 2)
button3.grid(row = 2, column = 3)
button4.grid(row = 2, column = 4)
button5.grid(row = 2, column = 5)
button6.grid(row = 2, column = 6)
button7.grid(row = 2, column = 7)
button8.grid(row = 2, column = 8)
button9.grid(row = 2, column = 9)
button10.grid(row = 2, column = 10)
button11.grid(row = 3, column = 1)
button12.grid(row = 3, column = 2)
button13.grid(row = 3, column = 3)
button14.grid(row = 3, column = 4)
button15.grid(row = 3, column = 5)
button16.grid(row = 3, column = 6)
button17.grid(row = 3, column = 7)
button18.grid(row = 3, column = 8)
button19.grid(row = 3, column = 9)
button20.grid(row = 3, column = 10)
button21.grid(row = 4, column = 1)
button22.grid(row = 4, column = 2)
button23.grid(row = 4, column = 3)
button24.grid(row = 4, column = 4)
button25.grid(row = 4, column = 5)
button26.grid(row = 4, column = 6)
win.mainloop()

import tkinter as tk
import random 
import threading
import time

def show_ware_tip():
    window = tk.Tk()
    screen_width = window.winfo_screenwidth()
    screen_height = window.winfo_screenheight()
    window_width = 300
    window_height = 60
    x = random.randint(0, screen_width - window_width)
    y = random.randint(0, screen_height - window_height)
    window.title("little tips")
    window.geometry(f"{window_width}x{window_height}+{x}+{y}")
    window.attributes('-topmost', True)  # 确保窗口在最前面
    
    tips =  ['你已经做得很好了','不必迎合所有人的期待','今天也要好好吃饭',
            '你的感受很重要,值得被重视','给自己一些休息的时间',
            '这不是浪费时间',' Progress, not perfection ','你并不孤单',
            '记得深呼吸','原谅那个不完美的自己','明天会是新的一天',
            '小小的你,也拥有巨大的能量','相信你已经尽力了',
            '对自己说一声:辛苦了','一切都会好起来的',
            '长风破浪会有时,直挂云帆济沧海','千淘万漉虽辛苦,吹尽狂沙始到金',
            '山重水复疑无路,柳暗花明又一村','追光的人,终会光芒万丈',
            '沉舟侧畔千帆过,病树前头万木春','愿你在迷茫中,坚信你的珍贵',
            '没有不可治愈的伤痛,没有不能结束的沉沦','仰望星空,脚踏实地',
            '每一个平凡的日常,都是连续发生的奇迹',
            '愿你以渺小启程,以伟大结尾','守得云开见月明',
            '天生我材必有用,千金散尽还复来','勇敢不是不害怕,而是带着恐惧依然前行',
            '最黑暗的夜晚,也终会迎来清晨'
            ]
    tip = random.choice(tips)
    bg_colors = ['#FFC0CB','#ADD8E6','#90EE90','#FFFFE0','#D3D3D3','#FFA07A']
    bg_color = random.choice(bg_colors)
    tk.Label(window, text=tip, bg=bg_color, font=("微软雅黑", 16), 
             width=30, height=3, wraplength=280).pack()  # 添加自动换行
    
    # 添加自动关闭功能
    window.after(5000, window.destroy)  # 5秒后自动关闭
    
    window.mainloop()

def start_tips():
    # 设置程序运行60秒后自动结束
    timer = threading.Timer(60.0, lambda: os._exit(0))
    timer.daemon = True
    timer.start()
    
    while True:
        t = threading.Thread(target=show_ware_tip)
        t.daemon = True
        t.start()
        time.sleep(0.1)  # 增加间隔时间，避免创建太快

if __name__ == "__main__": 
    import os  # 添加os模块导入
    start_tips()# huajian
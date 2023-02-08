import requests
import os
from bs4 import BeautifulSoup

def download_image(url, name):
    response = requests.get(url)
    if not os.path.exists(name):
        with open(name, 'wb') as f:
            f.write(response.content)
    else:
        print(f"File already exists:{name}")
# 输入起始页码
s=int(input("start page:"))
e=int(input("essssnd page:"))
# 遍历所有页码
for i in range(s,e):
    print("downloading page "+str(i))
    # 请求 URL
    url = "https://16k.club/index.php?p="+str(i)+"&size=50"

    # 发送请求
    res = requests.get(url)

    # 解析页面
    soup = BeautifulSoup(res.text, "html.parser")

    # 找到所有的图片元素
    images = soup.find_all("img")

    # 遍历本页图片元素，下载图片
    j=1
    for image in images:
        print("image"+str(j))
        url = image['src']
        name = url.split('/')[-1]
        try:
            download_image(url, name)
        except Exception as e:
            print("download failure image"+str(j))    
        j+=1
print("all images downloaded")
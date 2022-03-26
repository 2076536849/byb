# byb
import time
from selenium import webdriver
from selenium.webdriver.common.by import By


def cwj(zh):
    wd = webdriver.Chrome()
    wd.implicitly_wait(10)

    wd.get("http://xscfw.hebust.edu.cn/survey/login")

    element = wd.find_element(By.ID, 'user')
    element.send_keys(zh)
    element = wd.find_element(By.ID, 'pwd')
    element.send_keys('DianQi2020!!')

    a = wd.find_element(By.ID, 'login')
    a.click()

    b = wd.find_element(By.CLASS_NAME, 'mdui-list-item-content')
    b.click()

    c = wd.find_element(By.CLASS_NAME, 'mdui-textfield-input')
    c.send_keys('36.1')

    d = wd.find_element(By.XPATH, '//*[@id="main"]/div[5]/input')
    d.send_keys('36.1')

    e = wd.find_element(By.XPATH, '//*[@id="main"]/div[7]/label[2]/i')
    e.click()

    f = wd.find_element(By.ID, 'save')
    f.click()
    wd.quit()

import smtplib
import email
# 负责构造文本
from email.mime.text import MIMEText
# 负责构造图片
from email.mime.image import MIMEImage
# 负责将多个对象集合起来
from email.mime.multipart import MIMEMultipart
from email.header import Header
def yjfk():
    # SMTP服务器,这里使用163邮箱
    mail_host = "smtp.163.com"
    # 发件人邮箱
    mail_sender = "baiyibo2022@163.com"
    mail_license = "KVOPLFCCIMKPMNXD"
    # 收件人邮箱，可以为多个收件人
    mail_receivers = ['2076536849@qq.com']

    mm = MIMEMultipart('related')

    # 邮件主题
    subject_content = """晨午检"""
    # 设置发送者,注意严格遵守格式,里面邮箱为发件人邮箱
    mm["From"] = "sender_name<baiyibo@163.com>"
    # 设置接受者,注意严格遵守格式,里面邮箱为接受者邮箱
    mm["To"] = "receiver_1_name<2076536849@qq.com>"
    # 设置邮件主题
    mm["Subject"] = Header(subject_content,'utf-8')

    # 邮件正文内容
    body_content = """打卡成功！"""
    # 构造文本,参数1：正文内容，参数2：文本格式，参数3：编码方式
    message_text = MIMEText(body_content,"plain","utf-8")
    # 向MIMEMultipart对象中添加文本对象
    mm.attach(message_text)

    # 创建SMTP对象
    stp = smtplib.SMTP()
    # 设置发件人邮箱的域名和端口，端口地址为25
    stp.connect(mail_host, 25)
    # set_debuglevel(1)可以打印出和SMTP服务器交互的所有信息
    stp.set_debuglevel(1)
    # 登录邮箱，传递参数1：邮箱地址，参数2：邮箱授权码
    stp.login(mail_sender,mail_license)
    # 发送邮件，传递参数1：发件人邮箱地址，参数2：收件人邮箱地址，参数3：把邮件内容格式改为str
    stp.sendmail(mail_sender, mail_receivers, mm.as_string())
    print("邮件发送成功")
    # 关闭SMTP对象
    stp.quit()

def main():
    zh = [200801102]
    for i in zh:
        cwj(i)
        time.sleep(1)

        yjfk()
 main()

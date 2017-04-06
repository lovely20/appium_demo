# appium_demo,haha
# coding: utf-8
import time
import unittest
from appium import webdriver
import os


class Login_Logout(unittest.TestCase):
    def setUp(self):
        self.desired_caps = {}
        self.desired_caps["platformName"] = "Android"
        self.desired_caps["platformVersion"] = "6.0"
        self.desired_caps["deviceName"] = "127.0.0.1:62001"
        self.desired_caps['app'] = "E:/apk/kaolalicai.apk"
        self.desired_caps["appPackage"] = "com.kalengo.loan"  # app的包名
        self.desired_caps["appActivity"] = "com.kalengo.loan.activity.MPSplashActivity"
        self.driver = webdriver.Remote(str("http://localhost:4723/wd/hub"), self.desired_caps)
        time.sleep(2)

    def tearDown(self):
        self.driver.quit()

    def test_run(self):
        time.sleep(1)
        self.driver.swipe(450, 230, 20, 230, 200)
        time.sleep(1)
        self.driver.swipe(450, 230, 20, 230, 200)
        time.sleep(1)
        self.driver.find_element_by_class_name("android.widget.ImageView").click()
        time.sleep(1)

        # 关闭强制更新到2.26.0pop
        self.driver.find_element_by_id("com.kalengo.loan:id/update_none").click()

        self.driver.find_element_by_name("个人中心").click()
        self.driver.find_element_by_id("com.kalengo.loan:id/confirm_view").click()
        self.driver.find_element_by_id("com.kalengo.loan:id/login_btn").click()
        self.driver.find_element_by_id("com.kalengo.loan:id/login_account").send_keys("18520361016")
        self.driver.find_element_by_id("com.kalengo.loan:id/login_password").send_keys("123456")
        self.driver.find_element_by_id("com.kalengo.loan:id/login_login").click()
        time.sleep(5)

        # 关闭手势密码
        self.driver.find_element_by_id("com.kalengo.loan:id/close_btn").click()
        #关闭新手指引
        self.driver.find_element_by_id("com.kalengo.loan:id/confirm_view").click()

if __name__ == '__main__':
    unittest.main(verbosity=2)

from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.support.wait import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC
import math

def calc(x):
  return str(math.log(abs(12 * math.sin(int(x)))))

driver = webdriver.Chrome()
driver_wait = WebDriverWait
link = "http://suninjuly.github.io/explicit_wait2.html"
driver.get(link)
price = driver_wait(driver, 20).until(
    EC.text_to_be_present_in_element((By.ID,"price"),'$100'))
button = driver.find_element_by_id('book')
button.click()

x_selector = driver.find_element_by_id('input_value')
x = x_selector.text
y = calc(x)
field = driver.find_element_by_id('answer')
field.send_keys(y)
button = driver.find_element_by_id('solve')
button.click()
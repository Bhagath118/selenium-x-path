# selenium-x-path

```
Real-time scenario
Imagine an online student registration form.

The automation must:

Open the registration page.
Enter student name.
Enter password.
Enter additional information.
Select dropdown.
Select checkbox.
Select radio button.
Click Submit.
Verify successful submission.
 
TC	Real-time task	XPath concept
TC01	Open student registration page	get()
TC02	Locate username	Attribute XPath
TC03	Enter password	Attribute XPath
TC04	Locate Submit	text()
TC05	Locate textbox dynamically	contains()
TC06	Locate element with prefix	starts-with()
TC07	Find input using two attributes	and
TC08	Find element using alternatives	or
TC09	Find parent form	parent
TC10	Find form from input	ancestor
TC11	Find child inputs	child
TC12	Find next element	following
TC13	Find checkbox	Attribute + XPath
TC14	Find radio button	Attribute + XPath
TC15	Select dropdown	XPath + Select
TC16	Find second textbox	XPath index
TC17	Verify submitted message	text()
TC18	Find all input fields	find_elements()
TC19	Find dynamic element	contains()
TC20	Complete registration automation	Multiple XPath concepts

```

# program:
```
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.support.ui import Select
import time

driver = webdriver.Chrome()
driver.get("https://www.selenium.dev/selenium/web/web-form.html")

driver.maximize_window()

text_input = driver.find_element(
    By.XPATH,
    "//input[@name='my-text']"
)

text_input.send_keys("Bhagathkrishna A")
password = driver.find_element(
    By.XPATH,
    "//input[@name='my-password']"
)

password.send_keys("bha@12345")
submit = driver.find_element(
    By.XPATH,
    "//button[text()='Submit']"
)

print("Submit button found")
text_box = driver.find_element(
    By.XPATH,
    "//input[contains(@name,'my-text')]"
)

print("Textbox found using contains()")
text_box = driver.find_element(
    By.XPATH,
    "//input[starts-with(@name,'my-')]"
)

print("Element found using starts-with()")
password_box = driver.find_element(
    By.XPATH,
    "//input[@type='password' and @name='my-password']"
)

print("Password found using AND")
text_box = driver.find_element(
    By.XPATH,
    "//input[@name='my-text' or @type='text']"
)

print("Element found using OR")
parent = driver.find_element(
    By.XPATH,
    "//input[@name='my-text']/parent::*"
)

print("Parent element found")

form = driver.find_element(
    By.XPATH,
    "//input[@name='my-text']/ancestor::form"
)

print("Form found using ancestor")

child_inputs = form.find_elements(
    By.XPATH,
    ".//child::input"
)

print("Child input count:", len(child_inputs))
next_element = driver.find_element(
    By.XPATH,
    "//input[@name='my-text']/following::input[1]"
)

print("Following element found")

checkbox = driver.find_element(
    By.XPATH,
    "//input[@type='checkbox']"
)

checkbox.click()

print("Checkbox selected")

radio = driver.find_element(
    By.XPATH,
    "//input[@type='radio']"
)

radio.click()

print("Radio button selected")

dropdown = driver.find_element(
    By.XPATH,
    "//select[@name='my-select']"
)

select = Select(dropdown)

select.select_by_visible_text("Two")

print("Dropdown selected")


second_textbox = driver.find_element(
    By.XPATH,
    "(//input[@type='text'])[2]"
)

print("Second textbox found")

all_inputs = driver.find_elements(
    By.XPATH,
    "//input"
)

print("Total input fields:", len(all_inputs))

dynamic_element = driver.find_element(
    By.XPATH,
    "//input[contains(@name,'my-')]"
)

print("Dynamic element found")
print("Completing form...")

# Text
text_input.clear()
text_input.send_keys("Bhagathkrishna A")

# Password
password.clear()
password.send_keys("bha@12345")

# Checkbox
if not checkbox.is_selected():
    checkbox.click()

# Radio
if not radio.is_selected():
    radio.click()

# Dropdown
select.select_by_visible_text("Two")
submit.click()

print("Form submitted successfully!")

time.sleep(3)

driver.quit()
```


# ouptput:

<img width="1916" height="1040" alt="Screenshot 2026-10-08 112345" src="https://github.com/user-attachments/assets/e997e4ab-00b8-4e88-ba97-09540aeb69e1" />


<img width="1917" height="1021" alt="Screenshot 2026-10-08 112413" src="https://github.com/user-attachments/assets/0f98c20b-1009-4220-8c1b-748030f08baa" />

<img width="1917" height="988" alt="Screenshot 2026-10-08 112436" src="https://github.com/user-attachments/assets/e0090d71-a4ce-41e9-995b-62396b1db4c3" />









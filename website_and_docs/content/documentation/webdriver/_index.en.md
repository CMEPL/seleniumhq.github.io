from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.common.keys import Keys
import time

# Set up the WebDriver
driver_path = 'path_to_your_webdriver'  # e.g., 'chromedriver.exe' or '/usr/local/bin/chromedriver'
driver = webdriver.Chrome(executable_path=driver_path)

# Open WhatsApp Web
driver.get('https://web.whatsapp.com')

# Wait for the user to scan the QR code (you can add more sophisticated wait here)
input("Press Enter after scanning QR code")

# Function to count messages for a specific contact
def count_messages(contact_name):
    # Find and click on the contact
    search_box = driver.find_element(By.XPATH, '//div[@contenteditable="true"][@data-tab="3"]')
    search_box.send_keys(contact_name)
    search_box.send_keys(Keys.RETURN)
    
    time.sleep(2)  # wait for chat to load

    # Count messages in the chat
    messages = driver.find_elements(By.XPATH, '//div[contains(@class,"message-in")]')
    sent_messages = driver.find_elements(By.XPATH, '//div[contains(@class,"message-out")]')
    total_messages = len(messages) + len(sent_messages)
    
    return total_messages

# Example usage
contact_name = 'Contact Name'  # Replace with the contact's name
message_count = count_messages(contact_name)
print(f"Total messages with {contact_name}: {message_count}")

# Close the driver
driver.quit()


---
title: "WebDriver"
linkTitle: "WebDriver"
weight: 2
description: >
  WebDriver drives a browser natively; learn more about it.
aliases: ["/documentation/en/webdriver/"]
---


WebDriver drives a browser natively, as a user would, either locally
or on a remote machine using the Selenium server,
marks a leap forward in terms of browser automation.

Selenium WebDriver refers to both the language bindings
and the implementations of the individual browser controlling code.
This is commonly referred to as just _WebDriver_.

Selenium WebDriver is a [W3C Recommendation](https://www.w3.org/TR/webdriver1/)

* WebDriver is designed as a simple
  and more concise programming interface.

* WebDriver is a compact object-oriented API.

* It drives the browser effectively.


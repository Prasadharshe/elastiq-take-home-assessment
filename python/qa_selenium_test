import time
import pytest
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.common.keys import Keys

def setup_driver():
    driver = webdriver.Chrome(executable_path='/path/to/chromedriver') 
    driver.maximize_window()
    return driver

def test_search_functionality():
    driver = setup_driver()

    try:
        
        driver.get("https://www.lambdatest.com/selenium-playground/table-sort-search-demo")

        search_box = driver.find_element(By.ID, 'example_filter')
        search_box.send_keys("New York")
        search_box.send_keys(Keys.RETURN)

        time.sleep(2)

        rows = driver.find_elements(By.CSS_SELECTOR, ".table tbody tr")
        total_rows = len(rows)
       
        visible_rows = [row for row in rows if 'display: none' not in row.get_attribute('style')]

        assert total_rows == 24, f"Expected 24 rows, but got {total_rows}."
        assert len(visible_rows) == 5, f"Expected 5 visible entries, but found {len(visible_rows)}."

        print("Search functionality test passed successfully!")

    finally:
        driver.quit()

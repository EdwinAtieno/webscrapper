Problem 1: Web server (with optional secure communication

#### Problem Definition
The main goal of this project is Design a basic HTTP web-server application which can listen on a configurable TCP port and serve both static HTML and dynamically generated HTML by means of a chosen programming language, such as in the way Apache uses PHP. It is acceptable for this server application to support only a restricted subset of HTTP, such as GET or POST requests, and the only headers it must support are Content-Type and Content-Length.
#### How are we supposed to achieve this?
* Explore news sites and understand how different sites are structured so that you can have some knowledge on how to extract the information that is relevant to you
* Now that you have an idea of what you're working with, install and import the necessary dependencies for your project. That include:
  * Requests module
  ```python
    pip3 install requests
  ```
  * BeautifulSoup from bs4 package manager
  ```python
    sudo apt-get install python-bs4
  ```
* Prompt or Request input from the user. It should be a news url.
* Make a HTTP request from the any Url
```python
  import requests
  
  #Lets assume the user url is https://news.yahoo.com/
  user_url = "https://news.yahoo.com/"
  response = requests.get(user_url)
```
* Parse the HTML code from **response** using BeautifulSoup
```python
  from bs4 import BeautifulSoup
  
  soup = BeautifulSoup(response.content, "html.parser")
```
* You can find specific elements after parsing. This can be achieved in several ways including:
  * Find Elements by ID
    ```python
     results = soup.find(id="ResultsContainer")
    ```
  * Find Elements by HTML Class Name
    ```python
     job_elements = results.find_all("div", class_="card-content")
    ```
  * Extract Text from HTML elements
   ```python
     title_element = job_element.find("h2", class_="title").text
   ```
  * Find Elements by Class Name and Text Content
   ```python
     python_jobs = results.find_all("h2", string="Python")
   ```
* Store the scraped results in a txt file
```python
#store the output in a txt file in json format
with open('general-news.txt', 'w') as output_file:
        output_file.write(json.dumps(data, indent=4))
```

### Some of the Challenges I experienced
1. Every website is different. While you???ll encounter general structures that repeat themselves, each website is unique and will need personal treatment if you want to extract the relevant information.
2. Websites are always changing.






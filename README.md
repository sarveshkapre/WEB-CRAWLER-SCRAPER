# webcrawler
This assignment is intended to familiarize myself with the HTTP protocol. HTTP is (arguably) the most important application level protocol on the Internet today: the Web runs on HTTP, and increasingly other applications use HTTP as well (including Bittorrent, streaming video, Facebook and Twitter's social APIs, etc.). My goal in this assignment is to implement a web crawler that gathers data from a website. ( For this project, I have crawled a fake social networking site set up by my university for this project)

HIGH LEVEL APPROACH

1. Started by understanding how HTTP works! 
2. Analyzed the request response message using Burp Suite to get familiar with the format. 
3. Wrote a simple python code to perform form authentication using lxml and requests module. 
4. Wrote another python program to scrape a website to collect URL's just to get familiar with web scrapping. 
5. Used beautiful soup, lxml.html and requests module. Combined both the programs to login and scrape and tested on website. 

CHALLENGES

1.  Handle different server response like 200, 301, 403, 403, 500.

  1.1  Response 200 - OK - get the URL. pop it from the "urls" list and append it to "visited" list.

  1.2  Response 301 - Permanent Redirect - Extract the new URL from "Location" header and append it to "urls" list

  1.3  Response 403,404 - Push this URL to "visited" list

  1.4  Response 500 - Do not pop this url from"urls" list. Try till we get a response.

2. Creating a beautifulsoup object to perform actions such as extracting URL and headers from source code

3. Need to approach the following three main problems:

  3.1) Now, I need to maintain the state of my scrapper, so as to avoid visiting the same URI again.
        Approach was to created a stack/queue  and appended URL's continuously when visited. In order to scrape data from multiple pages         and remember that we have visited we need to create a data structure. Stack here will initially grow to a certain size and then         decrease back to zero. Hence used while loop. Wrote a program to crawl through web pages. Created two lists. One will maintain           the URL's collected and other will keep the URL's visited. After collecting the URL it is checked in visited list, if it is             present, then its dropped. Else it is added to list.

  3.2) I also need to track the relevant links to fakebook. Any other links which redirects to northeastern or david choffnes websites need to be dropped.
        Used an if statement to check if href belong with the particular domain. Only then visit them and add to visited list.
        
  3.3) Need to identify the end of program execution. To do this I need to keep tracks of the flags extracted during crawling and scraping. Once, I get 5 flags, I can stop immediately.
        Used for loop and set value of variable i to 1. It will increase by 1 as flags get displayed. When 5 flags are visited the loop         breaks and the program terminates

4. Faced several problems passing CSRF Token by extracting it from hidden fields each time we send a get request.

OVERVIEW OF TESTING CODE

        Wrote basic problems for each task like scraping and crawling and authenticating. Then combined the code.
        Printed statement for each important activity so as to test the logic. Tested for error handling using invalid input.






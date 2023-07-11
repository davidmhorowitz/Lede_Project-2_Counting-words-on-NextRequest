# Lede_Project-2_Word-Counting_NextRequest-SF
 Scraped the San Francisco NextRequest website for public records request data.

The project started super ambitious but ended up extremely lackluster. The initial goal was to figure out how well San Francisco's departments comply with records requests. The initial plan was to scrape the request and response data per department for multiple cities where the same departments primarily use NextRequest. Then, I would conduct a machine-learning text analysis to figure out, for example, which city's Public Works Department has the highest rejection rate of public records requests.

I got as far as the scraping all the data from July 2022 to July 2023. The scraping code retrieves data from NextRequest's undocumented API and works for any NextRequest portal. It pulls the data into a fetchable JSON format onto a personal hard drive as a list of dictionaries, where each dictionary is a single request and various parts of it:

e.g.,: dict_keys(['id', 'request_date', 'status', 'point_of_contact', 'department', 'requests', 'response_ids_per_request', 'responses_per_request'])

Because there were many "Public Health" categories, I merged them into the single department "Public Health." I quickly realized I didn't have the time for an actual text analysis and instead counted words using CountVectorizer. When I realized that I didn't have nearly enough time to pull off machine learning, I applied an NTLK filter with stopwords and added my own additional stopwords for generic public records request terminology. And I created a table with the most requested departments — ones with at least 50 requests sent through NextRequest.

Finally, I made a quick table with Datawrapper and a word cloud with Flourish.

I mention weaknesses in the final article, but here's a more in-depth version I was typing up while doing the project:

"The greatest weakness is that I should fix the algorithm to only count a word once per request — no more.

Moreover, certain departments publicize the NextRequest website more than others, resulting in certain departments’ words being overrepresented. I would ideally use a slightly more complicated calculation rather than count words: When calculating the total most used words, I should first isolate the departments and use the percentage of each word compared to all other words (calculation: how many requests a word was used in *divided by* total word count, with each word again getting 1 count max per request), giving the percentage points as a value. Then, at the end, I should add the top-scoring words among each department to create the total list.

I would normally be able to do these things with some formulas in pandas. However, because of the tight deadlines of the Lede program, because I still have more to catch up on, and because pandas still takes me a long time to work with, I will run with what I have."

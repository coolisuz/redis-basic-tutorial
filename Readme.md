git clone the project
npm install
Go to localhost:3000/api/search?query=Uzbekistan

See the difference between first and second response time looking
at "Network Response Headers"

Here is the request-response flow to help you understand what goes on in the /api/search route hander:

User requests for article
We look inside the Redis store to see the articles that have been cached previously
If true, we serve the cached version to the client.
Otherwise, we fetch the article from the Wikipedia API
We cache the response from the API in Redis for an hour (3600 seconds)
We send a response to the user.

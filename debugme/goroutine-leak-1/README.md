
This program spins up a basic HTTP server and then sends requests to it once
per second. Unfortunately, when I wrote this I introduced a goroutine leak!
Can you use Delve to detect the goroutine leak? Can you find the cause of the
leak? What is the fix?

<details>
  <summary>Hint 1</summary>
  
  Try using the `goroutines` command to show what goroutines are running.
</details>

<details>
  <summary>Hint 2</summary>
  
  Where are these goroutines stuck? Why might they be stuck there?
</details>

<details>
  <summary>Solution</summary>

  When making HTTP requests the client needs to read all of the data off the
  response body before continuing. Otherwise, the connection will remain open
  and will not be reused for subsequent requests.
</details>

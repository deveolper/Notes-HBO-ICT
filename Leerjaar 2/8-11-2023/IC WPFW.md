Klik [hier](https://sitepoint.com/introduction-to-the-fetch-api/) voor de informatie over de fetch-api.

# Promise
Een object wat "beloofd" dat er een bepaalde waarde ooit nog wordt gegeven.

Alles wat een promis geeft kan je met `.then` chainen.

```js
fetch('https://www.reddit.com/r/javascript/top/.json?limit=5').then(res => console.log(res));
```

Maar je kan ook dit doen:

```js
const result = await fetch('https://www.reddit.com/r/javascript/top/.json?limit=5');    // await veranderd de promis in het beloofde object.
result.json();
```

# Error-handling en status
## Status
```js
if (response.ok)
{
    // Response is successvol uitgevoerd
}
else
{
    // Niet successvol
}
```

Sommige API's geven een 200 response *zelfs* als de API-key ongeldig is.

## Errors
```js
try
{
    fetch(url);
}
catch (e)
{
    // Onderandere als je geen internet hebt.
}
```

## Uitwerking van een voorbeeldopdracht
Code van `index.html`:
```html
<!DOCTYPE html>
<html>
    <head>
        <link rel="javascript" src="logic.js"/>
        <link rel="styles" src="styles.css"/>
    </head>
    <body>
        <input type="text" placeholder="Enter Subreddit e.g. javascript" />
        <button>Fetch Posts</button>
        <div id="result"></div>
    </body>
</html>
```
Code van `styles.css`:
```css
body,
#result {
  padding: 15px;
}

ol {
  padding: 0 15px;
}

ol li {
  padding-bottom: 5px;
}

input[type="text"] {
  width: 300px;
  padding: 12px;
  border: 1px solid #ccc;
  border-radius: 4px;
  resize: vertical;
}

button {
  background-color: #4caf50;
  color: white;
  padding: 12px 20px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}
```
Code van `logic.js`:
```js
const button = document.querySelector('button');
const subInput = document.querySelector('input');
const result = document.querySelector('#result');

function renderList(json) {
  const posts = json.data.children;
  return `<ol>
    ${posts.map(
      post => `<li>${post.data.title} <a href=${post.data.url} target='_blank'>Link</a></li>`
    ).join('')}
  </ol>`;
}

async function fetchTopFive(sub) {
  const URL = `https://www.reddit.com/r/${sub}/top/.json?limit=5`;
  try {
    const fetchResult = fetch(new Request(URL, { method: 'GET', cache: 'reload' }));
    const response = await fetchResult;
    if (response.ok) {
      const jsonData = await response.json();
      result.innerHTML = renderList(jsonData);
    } else {
      result.innerHTML = `Response.status: ${response.status}`;
    }
  } catch (e) {
    result.innerHTML = e;
  }
}

button.addEventListener('click', () => {
  fetchTopFive(subInput.value);
});
```

# Cross-origin resource sharing (CORS)
Zie eerste link (informatie over fetch-api). Daar staan ook voorbeelden etc.

# Extra informatie
- Android-apps kan je als minor kiezen.

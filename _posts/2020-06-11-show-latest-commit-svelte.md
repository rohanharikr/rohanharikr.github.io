---
layout: post
title: Show latest commit on Svelte
comments: true
tags:
- svelte

---
#### [Scroll down for full code](#full-code)

#### Output

```
commit 72ea82s
```

#### Import onMount from Svelte

```
import { onMount } from 'svelte'
```

```onMount``` runs immediately after the component is rendered to the DOM.

#### Write a simple fetch function to fetch from the Github API

So here we are telling Svelte to fetch some data from this API when the component is first rendered. Note that the functions inside the ```onMount``` is only triggered when it enters the DOM.

```
onMount(async () => {
  await fetch('https://api.github.com/repos/${userName}/${repoName}/commits')
    .then((response) => response.json())
    .then((data) => {
      id = data[0].sha.slice(0, 7)
    })
})
```

```
await fetch('https://api.github.com/repos/${userName}/${repoName}/commits')
```
Performs a fetch request to the Github API's. Replace this ```userName``` and ```repoName``` with yours.

```.then((response) => response.json())```  
Converts the response to ```.json``` objects.


```.then((data) => {id = data[0].sha.slice(0, 7)})```  
Assigning only the first index ```data[0]``` ```sha``` key (where our commit id is) to a variable ```id``` since our request returned an array of objects with all the commits and info. 


```slice(0,7)```  
Takes only the first 7 digits since it is the Git default for a short SHA


#### <a name="full-code">Full Code</a>

<script src="https://gist.github.com/rohanharikr/aef6d401adc26f403efe98d6238602d4.js"></script>
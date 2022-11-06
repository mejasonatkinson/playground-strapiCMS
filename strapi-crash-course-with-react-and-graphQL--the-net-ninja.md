
## [Strapi Crash Course (with React & GraphQL) #1 - Intro & Setup](https://www.youtube.com/watch?v=4Ntd414raYc&list=PL4cUxeGkcC9h6OY8_8Oq6JerWqsKdAPxn&index=1)

Strapi is a headless CMS

A headless CMS is a CMS which does not have a frontend template or structure.
Strapi, only deals with the backend content management and provides an api to communicate that content to the frontend.

In this course the backend will be handled by Strapi. The frontend will be built in React.
The backend will communicate with the frontend using a Rest Api and GraphQL.

Before you starting this project it would help to have a basic understanding of:
React & React Hooks, GraphQL and Node.JS

[Frontend files for the course can be found here.](https://github.com/iamshaunjp/Strapi-Crash-Course)

## [Strapi Crash Course (with React & GraphQL) #2 - Create a Strapi App](https://www.youtube.com/watch?v=vG4M5f2wKK0&list=PL4cUxeGkcC9h6OY8_8Oq6JerWqsKdAPxn&index=2)

`mkdir ninja-reviews`

`cd ninja-reviews`

`npx create-strapi-app backend` 

The "backend" will be the name of the directory/folder to contain the strapi backend

Follow on screen instructions

`cd backend`

`npm run develop`

## [Strapi Crash Course (with React & GraphQL) #3 - Content Types & Endpoints](https://www.youtube.com/watch?v=TVwW01BqYQQ&list=PL4cUxeGkcC9h6OY8_8Oq6JerWqsKdAPxn&index=3)

In Strapi

...

# [Strapi Crash Course (with React & GraphQL) #4 - Permissions & Auth Requests](https://www.youtube.com/watch?v=N4JpylgjRK0&list=PL4cUxeGkcC9h6OY8_8Oq6JerWqsKdAPxn&index=4)

In Postman, 

Select New, HTTPRequest, GET: Endpoint localhost/.../, Send.

This will return a Error forbidden message.

By default Strapi protects data.

In Strapi

Settings, Roles, Public

In Postman, 

Select New, HTTPRequest, GET: Endpoint localhost/..././, Send.

This will return a the Endpoint.

Select New, HTTPRequest, DELETE: Endpoint localhost/..././, Send.

This will return a Error forbidden message.

...

# [Strapi Crash Course (with React & GraphQL) #5 - Creating a React App](https://www.youtube.com/watch?v=8IVQahYX-mc&list=PL4cUxeGkcC9h6OY8_8Oq6JerWqsKdAPxn&index=5)

`cd .` back out of the backend directory/folder.

`npx create-react-app frontend`

The "front" will be the name of the directory/folder to contain the react frontend

`cd frontend`

...

## [Strapi Crash Course (with React & GraphQL) #6 - Fetching Strapi Data](https://www.youtube.com/watch?v=cOE_hF2xjpM&list=PL4cUxeGkcC9h6OY8_8Oq6JerWqsKdAPxn&index=6)

`src/hooks/`

`useFetch.js`

`import { useEffect, useState } from "react"`

```
const useFetch = (uri) => {
	const [data, setData] = useState(null);
	const [error, setError] = useState(null);
	const [loading, setLoading] = useState(null);

	useEffect(() => {
		const fetchData = async () => {
		 setLoading(true)

		 try {
			const res = await fetch(uri)
			const json = await res.json()


			setData(json)
			setLoading(false)
		 } catch (error) {
			setError(error)
			setLoading(false)
		 }
		}

		fetchData()
	}, [uri])	

	return { loading, error, data }
}

export default useFetch
```

## [Strapi Crash Course (with React & GraphQL) #7 - Fetching a Single Record](https://www.youtube.com/watch?v=9OwZHtH6Ppo&list=PL4cUxeGkcC9h6OY8_8Oq6JerWqsKdAPxn&index=7)


## [Strapi Crash Course (with React & GraphQL) #8 - GraphQL Plugin & Overview](https://www.youtube.com/watch?v=3x-DeIbuNLc&list=PL4cUxeGkcC9h6OY8_8Oq6JerWqsKdAPxn&index=8)

Strapi, Marketplace, GraphQL

## [Strapi Crash Course (with React & GraphQL) #9 - Apollo Client Setup](https://www.youtube.com/watch?v=Y5iDq-suzCA&list=PL4cUxeGkcC9h6OY8_8Oq6JerWqsKdAPxn&index=9)

## [Strapi Crash Course (with React & GraphQL) #10 - The useQuery Hook](https://www.youtube.com/watch?v=qUiox_rkdvw&list=PL4cUxeGkcC9h6OY8_8Oq6JerWqsKdAPxn&index=10)


## [Strapi Crash Course (with React & GraphQL) #11 - Query Variables](https://www.youtube.com/watch?v=94ygizaXG38&list=PL4cUxeGkcC9h6OY8_8Oq6JerWqsKdAPxn&index=11)

## [Strapi Crash Course (with React & GraphQL) #12 - Relational Data](https://www.youtube.com/watch?v=OF-GZ8j60cI&list=PL4cUxeGkcC9h6OY8_8Oq6JerWqsKdAPxn&index=12)

Strapi, Content Type Builder, ...

## [Strapi Crash Course (with React & GraphQL) #13 - Fetching Related Data](https://www.youtube.com/watch?v=Ym-UBtxril4&list=PL4cUxeGkcC9h6OY8_8Oq6JerWqsKdAPxn&index=13)

## [Strapi Crash Course (with React & GraphQL) #14 - Rich Text Content](https://www.youtube.com/watch?v=mHuUASWQij4&list=PL4cUxeGkcC9h6OY8_8Oq6JerWqsKdAPxn&index=14)

Strapi uses Markdown, so the frontend needs to convert the markdown into html.

react-markdown is a project that convert the markdown into html.

`npm install react-markdown`

`import ReactMarkdown from 'react-markdown'`

Anything wrapped in the ReactMarkdown element.

`<ReactMarkdown>{data.reviews.body}</ReactMarkdown>`

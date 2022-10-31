# playground-strapi
A place to learn more about Strapi, and try things.

## [Strapi Crash Course (with React & GraphQL) #1 - Intro & Setup](https://www.youtube.com/watch?v=4Ntd414raYc&list=PL4cUxeGkcC9h6OY8_8Oq6JerWqsKdAPxn&index=1)

Strapi

Headless CMS

without a frontend template
such as a theme.

Strapi, only deals with backend content management and provides an api

frontend
react

backend
Strapi

GraphQL, alt to a Rest API

Before you start

- Basic understanding of React & React Hooks
- GraphQL
- Node.JS

https://github.com/iamshaunjp/Strapi-Crash-Course
frontend

## [Strapi Crash Course (with React & GraphQL) #2 - Create a Strapi App](https://www.youtube.com/watch?v=vG4M5f2wKK0&list=PL4cUxeGkcC9h6OY8_8Oq6JerWqsKdAPxn&index=2)

mkdir ninja-reviews

cd ninja-reviews

npx create-strapi-app backend

Quickstart (recommended)

Template: N

npm run develop

## [Strapi Crash Course (with React & GraphQL) #3 - Content Types & Endpoints](https://www.youtube.com/watch?v=TVwW01BqYQQ&list=PL4cUxeGkcC9h6OY8_8Oq6JerWqsKdAPxn&index=3)


Content-Types Builder

Collecion Types

blogs..

---

Display name: review (singlur, because strapi pluralises it automaticly)

Continue

Select Field Types

Text field

Base/Advanced Settings

Add another field etc..

Finish

Add

Save

Publish

---

Single Type

page..

Components

Collection of fields for Type(s)


api folder > Type folder > Config folder > routes.json
 
routes.json contains the routes to the end points for the api to interact with.

# [Strapi Crash Course (with React & GraphQL) #4 - Permissions & Auth Requests](https://www.youtube.com/watch?v=N4JpylgjRK0&list=PL4cUxeGkcC9h6OY8_8Oq6JerWqsKdAPxn&index=4)

postman


New 

HTTPRequest

GET

Enter Endpoint localhost/reviews/

Send

Error forbidden,



Strapi, protects data.

Settings, Roles, Public

find
findone



New 

HTTPRequest

GET

Enter Endpoint localhost/reviews/2

Send



New 

HTTPRequest

DELETE

Enter Endpoint localhost/reviews/2

Send

Error forbidden,


Settings, Roles, Authenticated

Select all


User, create


New 

HTTPRequest

POST

Enter Endpoint localhost/auth/local

Body

raw, JSON

{
	"identifier": "yoshi",
	"password": "Test1234",
}

Send

creates a jwt
copy jwt


New 

HTTPRequest

DELETE

Enter Endpoint localhost/reviews/2

Auth

Bearer Token

Paste jwt into token field

Send

No errors.



# [Strapi Crash Course (with React & GraphQL) #5 - Creating a React App](https://www.youtube.com/watch?v=8IVQahYX-mc&list=PL4cUxeGkcC9h6OY8_8Oq6JerWqsKdAPxn&index=5)

npx create-react-app frontend

cd frontend

remove alot of the default content.

components
SiteHeader.js

pages
Homepage.js
Category.js
ReviewDetails.js


ES7 React/Redux/GraphQL/React-Native snippets
VS plugin

npm install react-router-dom

...

## [Strapi Crash Course (with React & GraphQL) #6 - Fetching Strapi Data](https://www.youtube.com/watch?v=cOE_hF2xjpM&list=PL4cUxeGkcC9h6OY8_8Oq6JerWqsKdAPxn&index=6)

Rest Api

src/hooks/

useFetch.js

import { useEffect, useState } from "react"

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


Homepage.js

import useFetch from '../hooks/useFetch'

const { loading, error, data } = useFetch('http://localhost:13337/reviews')

if (loading) return <p>Loading...</p>
if (Error) return <p>Error...</p>

console.log(data);

return ( 



<p>Continue..</p>
{data.map(review => (

{review.rating}
{review.title}
{review.body.substring(0, 200)}...

<Link to={'details/${review.id}'}>Read More</Link>

))}


)


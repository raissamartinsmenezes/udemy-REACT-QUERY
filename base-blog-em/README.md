# Blog-em Ipsum

### A React App for the Udemy course "React Query: Server State Management for React"

## Installation

Run `npm install`

## Running the App

Run `npm start`. The app will be found at [http://localhost:3000]

## Server

This app uses the [JSON Placeholder](https://jsonplaceholder.typicode.com/) server.

## Study Notes

### isFetching x isLoading

**isFetching**: the async query function hasn't yet resolved yet

**isLoading**: we are in a fetching state, our query function hasn't resolved yet, but we also have no cached data. we've never made this query before and so we are both fetching and we have no cached data to display

-> pagination example

-> 3 refetches default before showing the error 

-> refetching when we refocus the widow

-> the error callback

### process.env.NODE_ENV === 'development'

create react app only sets this node env environment variable to be production. when you actually run a build `npm run build`, otherwise it's development or testing. so basically between create react app and the dev tools, we get it built in that when we're developing we get to see the dev tools, but in production they won't show




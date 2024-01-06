# udemy-REACT-QUERY

Code to support the Udemy course [React Query: Server State Management in React](https://www.udemy.com/course/learn-react-query/?couponCode=REACT-QUERY-GITHUB)

## Study Notes
- [ ] adicionar os links das docs da documentação
- [ ] separar os conteúdos sobre o update do react-query 
- [ ] voltar para a explicação sobre o **flow** do `useInfiniteQuery`

### isFetching x isLoading

**isFetching**: the async query function hasn't yet resolved yet (isFetching contains isLoading)

**isLoading**: we are in a fetching state, our query function hasn't resolved yet, but we also have no cached data. we've never made this query before and so we are both fetching and we have no cached data to display

-> pagination example

-> 3 refetches default before showing the error 

-> refetching when we refocus the widow

-> the error callback

### process.env.NODE_ENV === 'development'

create react app only sets this node env environment variable to be production. when you actually run a build `npm run build`, otherwise it's development or testing. so basically between create react app and the dev tools, we get it built in that when we're developing we get to see the dev tools, but in production they won't show

### staleTime x cacheTime

**staleTime**: is for re-fetching

**cacheTime**: is for data that might be re-used later, it is backup data to display while fetching 

- query goes into "cold storage" if there's no active useQuery
- cache data expires after cacheTime (default: five minutes) -> "how long it's been since the last active useQuery"
- after the cache expires, the data is garbage collected

### prefetching

- adds data to the cache
- is automatically stale
- while the data is refetching, react query will be able to hand us the data that's in the cache and we can display that until the refetch has refreshed the data

### mutations

similar to `useQuery` but:
- returns mutate function
- doesn't need query key
- `isLoading` but no `isFetching` because we don't have cached data
- by default, there's no retries (but this is configurable)

### useInfiniteQuery

- shape of the result `data` is different than `useQuery`
- object with two properties:
    - pages -> array of objects for each page of data
    - pageParams -> rarely used, but is a parameter passed to the queryFn
- every query has its own element in the pages array 
- `pageParams` tracks the keys of queries that have been retrieved 

```js
useInfiniteQuery('sw-people', ({ pageParam = defaultUrl}) => fetchUrl(pageParam))
```
- current value of pageParam is maintained by react-query
- options:
    - getNextPageParam: (lastPage, allPages) -> updates pageParam
- `fetchNextPage` -> function to call when the user needs more data
- `hasNextPage`: 
    - based on return value of getNextPageParam
    - if `undefined`, no more data is returned
- `isFetchingNextPage` 



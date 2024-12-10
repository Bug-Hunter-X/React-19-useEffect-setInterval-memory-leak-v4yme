# React 19 useEffect setInterval Memory Leak

This repository demonstrates a common error in React 19 applications involving the `useEffect` hook and `setInterval`.  Improper use of `setInterval` within `useEffect` can lead to memory leaks if a cleanup function isn't provided to clear the interval when the component unmounts.

## Bug
The `bug.js` file contains a component that uses `setInterval` to update a counter every second.  However, it lacks a cleanup function to stop the interval when the component is unmounted.  This results in a memory leak as the interval continues running indefinitely, even after the component has been removed from the DOM.

## Solution
The `bugSolution.js` file demonstrates the correct usage of `setInterval` within `useEffect`.  A cleanup function is returned from the `useEffect` callback, which is responsible for clearing the interval using `clearInterval` before the component is unmounted. This prevents the memory leak.

## How to reproduce
1. Clone this repository.
2. Navigate to the directory.
3. Run `npm install` to install dependencies.
4. Run `npm start` to start the development server.
5. Observe the counter behavior. In the buggy version, it will continue to increment even if the component is unmounted or the page is refreshed. The corrected version will show the normal counter increment until the component is unmounted.
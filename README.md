# React useEffect setInterval Cleanup Issue

This repository demonstrates a common error in React's `useEffect` hook when using `setInterval`.  The problem arises from incorrectly defining the `setInterval` function *inside* the `useEffect` causing a memory leak and unexpected behavior.

## Problem

The provided `MyComponent` uses `setInterval` to increment a counter every second. However, because the `setInterval` function is created anew on every render, the cleanup function (`clearInterval`) is ineffective. The old interval keeps running. 

## Solution

The solution involves moving the definition of the `setInterval` function outside of the `useEffect` hook. This ensures that a single `setInterval` ID is used, correctly managed by the cleanup function.
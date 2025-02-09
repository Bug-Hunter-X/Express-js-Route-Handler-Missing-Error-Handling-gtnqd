# Express.js Route Handler Missing Error Handling

This repository demonstrates a common error in Express.js route handlers: missing error handling for invalid input.  The example shows a route that fetches a user by ID.  If the ID is not a valid number, the code crashes because `parseInt` returns `NaN`, leading to an error when comparing to a number.

The `bug.js` file contains the buggy code. The `bugSolution.js` file shows the corrected code with proper error handling.

## Bug
The bug lies in the lack of error handling around the `parseInt` function and the subsequent user lookup.  If the `userId` cannot be parsed as an integer (e.g., it's a string like 'abc'),  `parseInt(userId)` will return `NaN`, and the comparison `user.id === NaN` will always be false, resulting in a 404 error even if the ID is completely wrong. More seriously, if `userId` is not provided, accessing `req.params.id` might throw an error.

## Solution
The solution adds input validation and more robust error handling to prevent crashes and provide informative error messages to the client.
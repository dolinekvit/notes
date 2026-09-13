# AI instructions, tips, etc.

Couple of useful tips regarding to AI usage targeting Playwright code. There is a Playwright MCP as well as [Playwright skill](https://github.com/testdino-hq/playwright-skill/tree/main). Though the skill is third-party, I would be cautious about using it (just to be sure).

## Instructions for `AGENTS.md` file

### Use web-specific matchers
Generic matches like `toEqual`, `toContain` or `toBeTruthy` do not wait until a specific condition is met.
Instead, use web-specific matchers such as `await expect(page.getByTestId('status')).toHaveText('Submitted');` which will wait until the condition is met or until the timeout is reached.
```
// Example of manual assertion -- Bad practice
expect(await page.getByText('welcome').isVisible()).toBe(true);
```

```
// Example of web-first assertion -- Best practice
await expect(page.getByText('welcome')).toBeVisible();
```

### Use locators
Use locators to locate an element, prioritize in this order:
```
1. page.getByRole('button', { name: /some text/i })
2. page.getByText(/some text/i)
3. page.getByLabel(/some text/i)
4. page.getByPlaceholder(/some placeholder text/i)
5. page.getByAltText(/some image description/i)
6. page.getByTitle(/some title/i)
7. page.getByTestId(/some id/i)
```
Use a CSS or XPath locators as the last resort. If the usage is necessary, put a comment in code why.

Prefer RegExp values instead of string values in selectors:
```
// Bad example
page.getByRole('button', { name: 'Some Text' })
```

```
// Good example
page.getByRole('button', { name: /some text/i })
```

### Test isolation
Isolate every test, do not share state between tests, no execution-order dependency.

Prefer `const` over `let`. Do not declare mutable variables in the outer test scope. Keep test-specific variables inside individual tests to ensure test isolation.

### Do not use `page.waitForTimeout()`
It is forbidden to use `page.waitForTimeout` as it can make the test flaky. Use `expect(locator).toBeVisible()` or `page.waitForURL()`.

### Fixtures over globals
If need be, share state via `test.extend()` and not module level variables.

### One behavior per test
Always test only one behavior per one test, using multiple `expect` calls is fine.

### Mock external services only
Never mock your own app, mock third-party APIs, gateways, and such.

Follow official Playwright [documentation](https://playwright.dev/docs/intro) while generating, refactoring, or reviewing code.

If you are unsure of anything, ask for clarification.

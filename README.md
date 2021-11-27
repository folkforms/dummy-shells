# dummy-shells

Dummy versions of shelljs for testing.

- `dummyShellJs`: Commands do nothing. Can query dummyShellJs.execList for calls to shelljs.exec, etc.
- `dryRunShellJs`: Exec and other commands will print to console.
- `failingShellJs`: Exec and other commands will return 1 for failure.

## Using jest.mock

If you don't want to use `dummyShellJs` you can mock it like so:

    beforeEach(() => {
      jest.mock("shelljs", () => {
        return {
          exec: jest.fn(() => ({ code: 0 })),
          echo: jest.fn(),
        }
      })
      shelljs = require("shelljs");

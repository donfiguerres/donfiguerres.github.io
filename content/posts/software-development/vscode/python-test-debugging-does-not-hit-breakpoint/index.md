---
title: "VS Code Python Test Debugging Does Not Hit Breakpoint"
description: "Breakpoint is not hit when debugging Python tests in VS Code"
date: 2022-07-26T00:00:00+08:00
hero: images/pytest-nocov-vscode.png
menu:
  sidebar:
    name: "Python Test Debugging Does Not Hit Breakpoint"
    identifier: python-test-debugging-does-not-hit-breakpoint
    parent: vscode
---

I had this problem in Python development environment wherein a breakpoint is not
hit while trying to debug tests. It turns out that this is a known issue and a
work around is available via the launch.json file.

```json
{
    "version": "0.2.0",
    "configurations": [
        {
            "name": "Debug Tests",
            "type": "python",
            "request": "launch",
            "purpose": [
                "debug-test"
            ],
            "console": "integratedTerminal",
            "justMyCode": false,
            "env": {
                "PYTEST_ADDOPTS": "--no-cov"
            }
        }
    ]
}
```

Below is the explanation form Microsoft.

> ***NOTE:*** If you have the pytest-cov coverage module installed, VS Code
doesn't stop at breakpoints while debugging because pytest-cov is using the same
technique to access the source code being run. To prevent this behavior, include
`--no-cov` in pytestArgs when debugging tests, for example by adding
`"env": {"PYTEST_ADDOPTS": "--no-cov"}` to your debug configuration.

Microsoft documentation: [link](https://code.visualstudio.com/docs/python/testing#_pytest-configuration-settings)

Found the solution from this stackoverflow [post](https://stackoverflow.com/a/67185092/4097451).

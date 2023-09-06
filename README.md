# KiCad Plugin Template

|         |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| ---     | ---                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| CI/CD   | [![CI - Main](https://github.com/adamws/kicad-plugin-template/actions/workflows/main.yml/badge.svg)](https://github.com/adamws/kicad-plugin-template/actions/workflows/main.yml) ![KiCad v6](https://img.shields.io/badge/kicad-v6-green) ![KiCad v7](https://img.shields.io/badge/kicad-v7-green)
| Meta    | [![Hatch project](https://img.shields.io/badge/%F0%9F%A5%9A-Hatch-4051b5.svg)](https://github.com/pypa/hatch) [![linting - Ruff](https://img.shields.io/endpoint?url=https://raw.githubusercontent.com/charliermarsh/ruff/main/assets/badge/v2.json)](https://github.com/astral-sh/ruff) [![code style - Black](https://img.shields.io/badge/code%20style-black-000000.svg)](https://github.com/psf/black) [![types - Mypy](https://img.shields.io/badge/types-Mypy-blue.svg)](https://github.com/python/mypy) [![License - MIT](https://img.shields.io/badge/license-MIT-9400d3.svg)](https://spdx.org/licenses/) |

-----

Project template for **[KiCad](https://www.kicad.org/)** [action plugins](https://dev-docs.kicad.org/en/python/pcbnew/).

**Table of Contents**

- [Key Features](#key-features)
- [How to use](#how-to-use)
  - [First build](#first-build)
  - [Hatch project manager](#hatch-project-manager)
  - [Testing](#testing)
  - [Github Actions](#github-actions)
- [License](#license)

## Key Features

[todo]

## How to use

This is **template repository**.
You can create your own repository from that template using [this guide](https://docs.github.com/en/repositories/creating-and-managing-repositories/creating-a-repository-from-a-template).
Alternatively, clone/download this repository and use it as a starting point for your plugin.

### First build

After your plugin directory is ready, run:

```shell
hatch build --target kicad-package
```

After a while you should get output similar to this:

```shell
[kicad-package]
package details:
{
  "download_sha256": "6d9aa77cea16b5edee478e4eb36c4e2c2a1c012201240767329363f116563312",
  "download_size": 7961,
  "install_size": 9259
}
dist/kicad_plugin_template-0.1.0.zip
```

Build result is located in `dist/` directory. You can install it with KiCad's `Plugin and Content Manager` using `Install From File...` option:

![install-from-file](resources/install-from-file.png)

|                                                                                                                            |                                                                                                               |
| ---                                                                                                                        | ---                                                                                                           |
| To check if it is working, open `PCB Editor`. Plugin icon should be on the toolbar ![on-toolbar](resources/on-toolbar.png) | If everything is ok, clicking it will result in following window ![gui-window](resources/gui-window.png)      |


And that's it! Your plugin template is ready for development.

### Hatch project manager

This template is using [hatch](https://hatch.pypa.io/latest) with [hatch-kicad](https://github.com/adamws/hatch-kicad) plugin.
Thanks to this build system it is possible to create KiCad compatible package file with single command.
All settings used in this process are located in `pyproject.toml` file.

At this stage you should start customizing project defaults. Open `pyproject.toml` and modify `kicad-package` section:

```toml
[tool.hatch.build.targets.kicad-package]
name = "Template"
# ...remaining options
```

These options controls plugin content and metadata. Metadata values will become important
when publishing to KiCad's plugin repository. To learn more about `kicad-package` builder see [this](https://github.com/adamws/hatch-kicad#builder).

Hatch is also used for running development tools in isolated environment.
For example, to get linting results using `ruff`, `black` and `mypy`, run:

```shell
hatch run lint:all
```

To run code formatting run:

```shell
hatch run lint:fmt
```

## Testing

Testing environment is not isolated (unlike `tool.hatch.envs.lint`) because it requires `pcbnew` package
which is installed and managed by KiCad. [todo: more details]

To execute tests run `pytest` command.

## Github Actions

[todo]

## License

This project is distributed under the terms of the [MIT](https://spdx.org/licenses/MIT.html) license.

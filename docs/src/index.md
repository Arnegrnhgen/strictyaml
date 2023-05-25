{% if readme -%}
# StrictYAML
{%- else -%}
---
title: StrictYAML
---

{% raw %}
<img alt="GitHub Repo stars" src="https://img.shields.io/github/stars/crdoconnor/strictyaml?style=social"> 
<img alt="PyPI - Downloads" src="https://img.shields.io/pypi/dm/strictyaml">
{% endraw %}
{% endif %}

StrictYAML is a [type-safe](https://en.wikipedia.org/wiki/Type_safety) YAML parser that parses and validates a [restricted subset](features-removed) of the [YAML](what-is-yaml)
specification.

Priorities:

- Beautiful API
- Refusing to parse [the ugly, hard to read and insecure features of YAML](features-removed) like [the Norway problem](why/implicit-typing-removed).
- Strict validation of markup and straightforward type casting.
- Clear, readable exceptions with **code snippets** and **line numbers**.
- Acting as a near-drop in replacement for pyyaml, ruamel.yaml or poyo.
- Ability to read in YAML, make changes and write it out again with comments preserved.
- [Not speed](why/speed-not-a-priority), currently.

I built it largely so I could [write integration tests with it](https://github.com/hitchdev/hitchstory).

{% for story in quickstart %}
{{ story.name }}:
{% if 'yaml_snippet' in story.data['given'] %}
```yaml
{{ story.given['yaml_snippet'] }}
```
{% endif %}
{% if 'setup' in story.data['given'] %}
```python
{{ story.given['setup'] }}
```
{% endif %}


{% for variation in story.variations %}

{{ variation.child_name }}:

{% with step = variation.steps[0] %}{% include "step.jinja2" %}{% endwith %}
{% endfor %}
{% endfor %}


## Install

```sh
$ pip install strictyaml
```


## Why StrictYAML?

There are a number of formats and approaches that can achieve more or
less the same purpose as StrictYAML. I've tried to make it the best one.
Below is a series of documented justifications:

{% for dirfile in (subdir("why-not").ext("md") - subdir("why-not").named("index.md"))|sort() -%}
- [{{ title(dirfile) }}](why-not/{{ dirfile.name.splitext()[0] }})
{% endfor %}


## Using StrictYAML

How to:

{% for dirfile in (subdir("using/alpha/howto/").ext("md") - subdir("using/alpha/howto/").named("index.md"))|sort() -%}
- [{{ title(dirfile) }}](using/alpha/howto/{{ dirfile.name.splitext()[0] }})
{% endfor %}

Compound validators:

{% for dirfile in (subdir("using/alpha/compound/").ext("md") - subdir("using/alpha/compound/").named("index.md"))|sort() -%}
- [{{ title(dirfile) }}](using/alpha/compound/{{ dirfile.name.splitext()[0] }})
{% endfor %}

Scalar validators:

{% for dirfile in (subdir("using/alpha/scalar/").ext("md") - subdir("using/alpha/scalar/").named("index.md"))|sort() -%}
- [{{ title(dirfile) }}](using/alpha/scalar/{{ dirfile.name.splitext()[0] }})
{% endfor %}

Restrictions:

{% for dirfile in (subdir("using/alpha/restrictions/").ext("md") - subdir("using/alpha/restrictions/").named("index.md"))|sort() -%}
- [{{ title(dirfile) }}](using/alpha/restrictions/{{ dirfile.name.splitext()[0] }})
{% endfor %}


## Design justifications

There are some design decisions in StrictYAML which are controversial
and/or not obvious. Those are documented here:

{% for dirfile in (subdir("why").ext("md") - subdir("why").named("index.md"))|sort() -%}
- [{{ title(dirfile) }}](why/{{ dirfile.name.splitext()[0] }})
{% endfor %}


## Star Contributors

- @wwoods
- @chrisburr
- @jnichols0

## Other Contributors

- @eulores
- @WaltWoods
- @ChristopherGS
- @gvx
- @AlexandreDecan
- @lots0logs
- @tobbez
- @jaredsampson
- @BoboTIG

StrictYAML also includes code from [ruamel.yaml](https://yaml.readthedocs.io/en/latest/), Copyright Anthon van der Neut.

## Contributing

- Before writing any code, please read the tutorial on [contributing to hitchdev libraries](https://hitchdev.com/approach/contributing-to-hitch-libraries/).
- Before writing any code, if you're proposing a new feature, please raise it on github. If it's an existing feature / bug, please comment and briefly describe how you're going to implement it.
- All code needs to come accompanied with a story that exercises it or a modification to an existing story. This is used both to test the code and build the documentation.

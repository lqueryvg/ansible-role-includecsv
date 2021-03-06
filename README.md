# Ansible Role: include_csv

This role contains no tasks, but provides ``include_csv`` module which loads variables from a CSV file.

Ansible Galaxy Page: https://galaxy.ansible.com/detail#/role/6589

## include_csv module

This module will load variables from a CSV file.

Example task::

```yaml
- include_csv: src=path/to/fruits.csv
```

The first line it will be read as the name of the parameter.
It will read the subsequent second line as data.::

```csv
id,name,price
0,apple,100
1,banana,200
2,cherry,300
3,durian,400
```

The variables named using file name without the extention.
To use variable as follow

```yaml
- debug: msg="{{ fruits }}"
```

```python
ok: [localhost] => {
  "msg": "[{u'price': u'100', u'id': u'0', u'name': u'apple'}, {u'price': u'200', u'id': u'1', u'name': u'banana'}, {u'price': u'300', u'id': u'2', u'name': u'cherry'}, {u'price': u'400', u'id': u'3', u'name': u'durian'}]"
  }
```

## Options

| parameter | required | default | choices | comments                                                                                                                                      |
|:----------|:---------|:--------|:--------|:----------------------------------------------------------------------------------------------------------------------------------------------|
| src       | yes      |         |         | Speficy CSV file path. The path must be a absolute path or a relative path. (Not support detecting file name under roles/foo/files directory. |
| delimiter | no       | '       |         | a one-character string to use as the field separator.                                                                                         |
| quotechar | no       | "       |         | a one-character string to use as the quoting character.                                                                                       |

## Examples

Use as like ``include_vars``.

```yaml
- include_csv: src=foo.csv
```

```yaml
- include_csv: src=bar.csv delimiter="|" quotechar="'"
```

### Load locally

Appends ``connection`` and ``sudo``.

```yaml
- include:csv: src=bar.csv
  connection: local
  sudo: no
```

## Requirements

None.

## Role variables

None.

## Dependencies

None.

## License

GPLv3

## Author Information

[Kouhei Maeda](https://github.com/mkouhei)


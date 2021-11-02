# OpenFisca

[OpenFisca](https://openfisca.org) is a fast and approachable framework for specifying rules as code, separate from the code used to handle their application. An OpenFisca country package specifies the laws of a country, and some inputs, and [OpenFisca-Core](https://github.com/OpenFisca/OpenFisca-Core) handles the calculation of variables over time and management of entities and data structures.

PolicyEngine manages two country packages: [OpenFisca-UK](https://github.com/PolicyEngine/OpenFisca-UK), which has coverage of all major UK taxes and benefits, and [OpenFisca-US](https://github.com/PolicyEngine/OpenFisca-US), which is currently under development.

## How to contribute

Any contributions are welcome- this could invole:
* Filing an issue to report a bug, or request a feature
* Filing a PR with a bug fix, or implementation of a tax-benefit rule

## Adding parameters

Parameters are data tracking specific tax-benefit values over time- for example, the values of tax thresholds, or benefit elements. These are specified in YAML format, with the following general structure:

```yaml
description: A description of the parameter.
values:
  2015-04-06: 0.50 # The value when introduced on 6th April, 2015
  2021-04-06: 0.65 # The value when changed on 6th April, 2021
metadata:
  period: year # The time period this parameter refers to
  unit: currency-GBP # The unit of the values
  reference:
    - title: The first reference
      href: https://a-country.gov/the-source-of-the-values
```

## Adding variables

Variables are specific properties of some entity, that can be calculated from a formula or input manually, and can change over time. These are added by adding a new class inheriting from `Variable` to one of the Python descendent files under the `variables/` folder of a country package (in which file doesn't affect the variable). This follows the following pattern:

```python
class some_tax(Variable):
    entity = Person # The entity this belongs to
    definition_period = YEAR # How frequently the variable is calculated
    label = "Some tax" # A short (max 3 words) name for the variable
    documentation = "An extended description of the variable."

    def formula(person, period, parameters):
        another_variable = person("variable_class_name", period)
        current_parameter_value = parameters(period).subfolder.subfolder.filename
        return another_variable * current_parameter_value
```


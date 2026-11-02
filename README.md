# enterocyte-modules

A modular model of glucose and ion transport across an enterocyte (lumen → enterocyte → capillary).
It is a test repository for the PhLynx module template, and its config and parameter files follow the
[circulatory-autogen-modules](https://github.com/physiomelinks/circulatory-autogen-modules) formats.

The model has six math definitions (module types) and nine instances:

| Module type | Instances |
|---|---|
| `compartment` | `lumen`, `enterocyte`, `capillary` |
| `GLUT2` | `GLUT2_api` (apical), `GLUT2_bas` (basolateral) |
| `SGLT1` | `SGLT1` |
| `NKA` | `NKA` |
| `Kir` | `Kir` |
| `membrane` | `Membrane` |

## Layout

```
math/            <module_type>.cellml                  one CellML 2.0 model per module type: its units, then its one component
annotations/     <module_type>.ttl                     RDF annotations of that math, keyed by the CellML variable ids
configurations/  <module_type>_<instance>_modules_config.json
                                                       one config per instance (module_subtype = instance name):
                                                       its ports, its variables and their types, the math file
                                                       it uses, and its default parameterisation
parameters/      <instance>_parameters.json           each instance's values as nested parameters JSON, its
                                                       global constants under "global"
units/           Modular_Enterocyte_261015_units.cellml   every units definition the math uses
```

Instances of one module type share its math and annotations. They differ in their ports, which depend on
which compartments they connect, and in their parameters. That is why there are six math files but nine
configs and parameter sets.

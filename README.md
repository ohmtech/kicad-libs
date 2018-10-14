# kicad-libs

Kicad libraries (symbols, footprints) used in ohmtech projects.

Symbols are used for schematic when the symbol is not already available in KiCad.

Footprints are used for routing when the footprint is not already available in KiCad,
or when the manufacturer gives slightly different dimensions than the one in KiCad.

## Usage

The following assumes that using project specific libraries is prefered over using global libraries.
That allows to minimise set-up work for a collaborator joining the project or when switching between branches.

### Add as submodule

This repository shall first be cloned as a submodule of the project using it.

    git submodule add git@github.com:ohmtech/kicad-libs.git

### Add symbols paths

From the schematic editor `eechema`, go to `Preferences > Manage Symbol Libraries`.
Then choose the tab `Project Specific Libraries`.
Click `Browse Libraries...` and select the libraries needed for the project.
Make the path relative by using the environment variable `KIPRJMOD`.

This will generate a `sym-lib-table` S-expression file which content would typically look like the following:

```
(sym_lib_table
  (lib (name Cirrus)(type Legacy)(uri ${KIPRJMOD}/../submodules/kicad-libs/symbols/Cirrus.lib)(options "")(descr ""))
  (lib (name Switchcraft)(type Legacy)(uri ${KIPRJMOD}/../submodules/kicad-libs/symbols/Switchcraft.lib)(options "")(descr ""))
  (lib (name TexasInstruments)(type Legacy)(uri ${KIPRJMOD}/../submodules/kicad-libs/symbols/TexasInstruments.lib)(options "")(descr ""))
)
```

### Add footprints paths

From the schematic editor `pcbnew`, go to `Preferences > Manage Footprint Libraries`.
Then choose the tab `Project Specific Libraries`.
Click `Browse Libraries...` and select the libraries needed for the project.
Make the path relative by using the environment variable `KIPRJMOD`.

This will generate a `fp-lib-table` S-expression file which content would typically look like the following:

```
(fp_lib_table
  (lib (name Connector_Neutrik)(type KiCad)(uri ${KIPRJMOD}/../submodules/kicad-libs/footprints/Connector_Neutrik.pretty)(options "")(descr ""))
  (lib (name Connector_Switchcraft)(type KiCad)(uri ${KIPRJMOD}/../submodules/kicad-libs/footprints/Connector_Switchcraft.pretty)(options "")(descr ""))
  (lib (name Connector_Thonk)(type KiCad)(uri ${KIPRJMOD}/../submodules/kicad-libs/footprints/Connector_Thonk.pretty)(options "")(descr ""))
  (lib (name Package_TexasInstruments)(type KiCad)(uri ${KIPRJMOD}/../submodules/kicad-libs/footprints/Package_TexasInstruments.pretty)(options "")(descr ""))
)
```

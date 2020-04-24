# kicad_ci_test

![CI](https://github.com/INTI-CMNB/kicad_ci_test/workflows/CI/badge.svg)

Test for Continuous Integration using KiCad.

This is an example of how to test and generate documentation for a KiCad project automatically every time you commit a change to the schematic and/or PCB.

In this example we use a [docker image](https://github.com/INTI-CMNB/kicad_auto) containing KiCad, [KiPlot](https://github.com/INTI-CMNB/kiplot) and all the supporting tools.

The [kicad_ci_test.kiplot.yaml](https://github.com/INTI-CMNB/kicad_ci_test/blob/master/kicad_ci_test.kiplot.yaml) configures KiPlot and says what's available.

The [.github/workflows/test1.yml](https://github.com/INTI-CMNB/kicad_ci_test/blob/master/.github/workflows/test1.yml) configures what GitHub makes.

In this file we:

* Instruct GitHub to run the tasks every time a change in the pertinent files is detected:

```
on:
  push:
    branches: [ master ]
    paths:
      - '**.sch'
      - '**.kicad_pcb'
  pull_request:
    branches: [ master ]
    paths:
      - '**.sch'
      - '**.kicad_pcb'
```

* Define actions for ERC, DRC, schematic documentation generation and PCB documentation generation.
* Each action takes the repo content as input using:

```
- uses: actions/checkout@v2
```

* The actions are executed by KiPlot and stored in the *Fabrication* directory

* The resulting files are stored as *artifacts* using:

```
 - name: Recuperar resultados
      uses: actions/upload-artifact@v1
      with:
        name: ERC_Output
        path: Fabrication
```

For more information about the GitHub configuration read the [Workflow syntax for GitHub Actions](https://help.github.com/en/actions/reference/workflow-syntax-for-github-actions) page.


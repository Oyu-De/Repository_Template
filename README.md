# Replace **PROJECT** with name or aircraft
## make.py
- project = "@hatchet_PROJECT"
- key_name = "hatchet_PROJECT"
- prefix = "hatchet_PROJECT"
- pbo_name_prefix = "hatchet_PROJECT_"
- MAINPREFIX = "z"
- PREFIX = "hatchet_PROJECT_"
## make.cfg
- project = @hatchet_PROJECT
- prefix = z\hatchet_PROJECT\addons
- module_root = P:\z\hatchet_PROJECT\addons
- optionals_root = P:\z\hatchet_PROJECT\optionals
- P:\z\hatchet_PROJECT\release
- pbo_name_prefix = PROJECT_
- -zipPrefix = hatchet_PROJECT
- build_tool = pboproject

## Setup.py
MAINDIR = "z"

PROJECTDIR = "hatchet_PROJECT"

CBA = "P:\\x\\CBA_A3"

ACE = "P:\\x\\ACE3"


# Documenting the workflow folder
 1. You need to go through workflow file
 2. change **PROJECT** in each file all in **lower case** and no special char's ie @$%&* only
    1. release_dev.yml hatchet_PROJECT_dev
    2. release_main.yml hatchet_PROJECT_main
    3. release_rc.yml hatchet_PROJECT_rc

## **What does everything do**

## **1. build.yml 1st to run**
  1. runs when pull requests to main branch
  2. it does a lint check
     1. Checkout the source code
     2. Validate SQF
     3. Validate Config
     4. Validate Stringtables
        1. We currently don't have
     5. Validate Return Types
     6. Check for BOM ?
        1. No one knows what this means
  3. builds the project
     1. Build with HEMTT
     2. Releases zip file

## **2. release_dev.yml**
1. on push to main branch
2. builds addons with HEMTT
3. Extracts the mods zip
4. Uploads to steam workshop
5. Only available to friends of the steam page


## **3. release_rc.yml**
1. Build triggered by tag rc-v0.0.0
2. uploads public test version to the steam workshop

## **4. release_main.yml**
1. Build triggered by tag v0.0.0
2. builds stable version and uploads to steam

## **5.release-drafter.yml**
1. Updates the change log
2. Based on Labels
3. Labels description's tell what part the tags update
4. Read the issue labels
5. relies on a config file located in the root folder called my-config.yml

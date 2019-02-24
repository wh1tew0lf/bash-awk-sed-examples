BASH examples
=============

First of all you need to add to your script file "*.sh" shabang:
```
#!/bin/bash
# OR
#!/usr/bin/env bash
```
differrence between this two variants is described next:
 * first bin/bash will open binary at specified place
 * second env - will search bash at PATH folder, so it can be some local bash binary

# ThoughtsAboutTheIdealUIFramework
## Problem: 

Non of the existing UI frameworks/philosophies - MVC, MVVM, MVU etc. - fulfills all of the following requirements:
* allow creation/maintenance of the actual UI by a non-programmer completely
* separate properly between code that serves only UI specifics (for example, expanding/collapsing a treenode or a panel, or defining what selection means in a given context) from code that has to do with the domain directly or indirectly (eg, calls to a server)


## Elements
### model outputs
data the model exposes; can be bound from the UI, never changed; if it updates in the model, it updates in the UI automatically
### UI variables
declared in the UI; written only by other UI declarations; read only by other UI declarations; serve for stuff like "selectedItem(s)"
### commands and arguments
commands are exposed by model only; are async by default; may have parameters; never have a return value; UI can call a command and pass in arguments referring to UI variables (or constants)
### actions
declared in the UI and invoked from the UI only

# License
Use of the contents of this repository is governed by the [Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International Public License](License.txt).
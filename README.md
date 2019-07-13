# ThoughtsAboutTheIdealUIFramework
## Problem: 

Non of the existing UI frameworks/philosophies - MVC, MVVM, MVU etc. - fulfills all of the following requirements:
* allow creation/maintenance of the actual UI by a non-programmer completely
* separate properly between code that serves only UI specifics (for example, expanding/collapsing a treenode or a panel, or defining what selection means in a given context) from code that has to do with the domain directly or indirectly (eg, calls to a server)

## Enable process
### Roles
Two roles (may be assumed by the same person, or each by multiple, does not matter):
* `UX`: a designer who knows HTML, CSS and has a little bit of understanding for declarative scripting
* `DEV`: a programmer/Developer

### New Project Flow
assumption: user stories/specs are given and clear to everyone involved

0. `DEV` und `UX` agree which `output`s and COMMANDs the model will expose. After this step, they will each work completely separately and independently.
1. `DEV` works on the model, exposing `output`s and COMMANDs; `UX` creates HTML/CSS, with all the moveable parts
2. once both are done, the whole thing works

### Existing Project Flow
Typical scenarios:
* a form should be split into a wizard/step by step thing: doable completely by `UX`
* a list should be made client-side pageable: doable completely by `UX`
* a textbox for input of tags should offer client-side auto-completion: `DEV` adjusts model to expose an `output` "AllAvailableTags"; `UX` can do all the rest
* a list which so far allowed only single selections and certain actions on the selected item, should switch to multiple selection: `DEV` adjusts all COMMANDs to take list arguments instead of single arguments; `UX` can do all the rest


## Model `output`s
data the model exposes; can be bound from the UI, never changed; if it updates in the model, it updates in the UI automatically
## UI `variable`s
declared in the UI; written only by other UI declarations; read only by other UI declarations; serve for stuff like "selectedItem(s)"
## `command`s and arguments
`command`s are exposed by model only; are async by default/always; may have parameters; never have a return value; UI can call a `command` and pass in arguments referring to UI `variable`s (or constants)
## `actions`
declared in the UI and invoked from the UI only
## general properties
* SPA always
* `UX` never interacts with JS or any other programming language; only with declarative syntax, DSL for them
* `DEV` can choose whatever language they want: JS, TS, WebAssembly (C#, F#, whatever); if language-specific adapters are necessary to enable support, so be it
* UI declarations must be completely doable by `UX`
* all UI logic (`output`s, `variable`s, `action`s, calling of `command`s) is hot-reloadable (and, of course, CSS, too), so `UX` can work the way they usually like to
* UI components: have no model, are written by `DEV`, used only by `UX`; add new declaration elements usable by `UX`
* template components: have no model, encapsulate a combination of existing HTML, CSS, declaration elements, are written and used by `UX` only
* ability to easily create `mock model` for `UX`: ideally, doable by somewhat more advanced `UX`
* debugging support for `UX`
    * easily switch to `mock model` -> try if problem still present? -> no: problem is in model implementation, forward issue to `DEV`
    * enable debug output that writes to console what is happening in terms of declaration calls
* `UX` can define client-side routes, pages without `DEV` support
* out-of-the-box `command`s for calling APIs, for OAuth authentication, for passing OAuth tokens with API calls
* ability to wrap existing UI components from 3rd-party for use by `UX`

    
## Examples
* Todo App
* single selection vs multiple selection
* tag auto-completion client-side 
* tag auto-completion server-side
* paging
* trigger commands via keyboard shortcuts, alternatively to buttons
* split one view/page into multiple 
* login/logout flow with protected views/pages
* ?how to wrap existing datetimepicker?


# License
Use of the contents of this repository is governed by the [Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International Public License](License.txt).
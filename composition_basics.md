# Composition API

Composition API is a new addition to VueJS 3.

It works different than the options API where we have to declare everything (methods, computed...) in the body setup(){} within the script tag.

The variables we declare are not directly available in the template tag. We have to declare them in the return body so they can be available.

The reactivity is also different. We have to declare the reactive variables explicitly.

For most part, the template 
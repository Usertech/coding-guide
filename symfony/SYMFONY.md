# Symfony structure
## Images & favicons
```
+-- public/
    +-- favicons/
        +-- favicon.ico
        +-- ...
    +-- img/
        +-- example.png
        +-- ...      
```
## Frontend
```  
+-- src/
    +-- resources/
        +-- stylesheet/
            +-- fonts/
                +-- FontName/
                    +-- FontName.*
            +-- libs/
                +-- lib.sass
                +-- anotherLib.sass
            +-- mixins/
                +-- mixin.sass
                +-- anotherMixin.sass 
            +-- variables/
                +-- variable.sass 
                +-- anotherVariable.sass 
            +-- index.sass     
        +-- templates/
            +-- components/
                +-- component/
                    +-- index.js
                    +-- index.html.twig
                    +-- index.sass
            +-- pages/
                +-- page.html.twig
                +-- anotherPage.html.twig
            +-- sections/
                +-- Section.html.twig
                +-- AnotherSection.html.twig
        +-- index.js
```
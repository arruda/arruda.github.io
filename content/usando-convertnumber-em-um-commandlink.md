Title: Usando ConvertNumber em um CommandLink
Date: 2011-06-08 12:27
Author: arruda
Category: Java, programação, Web
Tags: commandlink, convertNumber, instance, Java, jsf, outputtext, Parent, richfaces, ValueHolder, web
Slug: usando-convertnumber-em-um-commandlink
Status: published

"... commandLink -Parent not an instance of ValueHolder"
--------------------------------------------------------

Para quem já bateu de cara com essa exception do JSF e pensou: *"Meu deus e agora? Como coloco esse link com uma formatação de numero? Isso é impossível?"* A resposta é: **É possível sim!**

Exemplo:  
Ao invés de usar:

``` {lang="Java" line="1"}

        
```

Utilize da seguinte forma:

``` {lang="Java" line="1"}

    
        
                                                     
```

Isso por que ao colocar o **OutputText** como responsável pelo **"value"** do **CommandLink**, você pode usar normalmente dentro do mesmo a tag **ConvertNumber**.

Essa mesma solução serve para o **RichFaces**, no lugar de **"h:commandLink"**, você teria **"a4j:commandLink"**.

Abraços a todos.

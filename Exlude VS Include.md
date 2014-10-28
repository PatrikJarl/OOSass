Why use @extend instead of @include?

Well, why? Both of them does the same thing, right? They ”import” code into a class. Well, that might be true, but if you’re really concerned about how DRY your CSS is you really have no choice. Let me explain with a couple examples.

First of the @extend.

The first thing to do here is to declare a placeholder selector. These are similar to the class selector (.) but instead begins with a percent character (%). Also, it has the great propery to not be shown in the generated CSS.

Example:

%button {
    margin: 0 10px; 
}

.error-button {
    @extend %button;
    /* error-button specific styles */ 
}

.success-button {
    @extend %button; 
    /* success-button specific styles */ 
}
This will generate the following CSS

.error-button, .success-button {
    margin: 0 10px; 
}

.error-button {
    /* error-button specific styles */ 
}

.success-button {
    /* success-button specific styles */ 
}
Notice the absence of the .button class! DRY CSS FTW!

@include then

First of. The @include-property is the import function for mixing.

@mixin button {
    margin: 0 10px; 
}

.error-button {
    @include button; 
    /* error-button specific styles */ 
}

.success-button {
    @include button; 
    /* success-button specific styles */ 
}
Well. So far no bigger difference between the two. But the generated CSS tell us a different story.

.error-button {
    margin: 0 10px; 
    /* error-button specific styles */ 
}

.success-button {
    margin: 0 10px; 
    /* success-button specific styles */ 
}
The bundling that happened in our previous example is gone and the era of repeated CSS is here.

Why care about repeated code?

Since the preprocessor made an entry to the stage of CSS we nowadays doesn’t operate in the CSS files anymore. Soo.. why care about what code we generate?

There are several reasons

The size of the css file
Optimising the sites speed
We still maintain css…

<h2>Why use @extend instead of @include?</h2>

<p>Well, why? Both of them does the same thing, right? They ”import” code into a class. Well, that might be true, but if you’re really concerned about how DRY your CSS is you really have no choice. Let me explain with a couple examples. </p>

<h2>First of the @extend.</h2>

<p>The first thing to do here is to declare a placeholder selector. These are similar to the class selector (.) but instead begins with a percent character (%). Also, it has the great propery to not be shown in the generated CSS.</p>

<p>Example: </p>

<pre><code>%button {
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
</code></pre>

<p>This will generate the following CSS </p>

<pre><code>.error-button, .success-button {
    margin: 0 10px; 
}

.error-button {
    /* error-button specific styles */ 
}

.success-button {
    /* success-button specific styles */ 
}
</code></pre>

<p>Notice the absence of the .button class! DRY CSS FTW! </p>

<h2>@include then</h2>

<p>First of. The @include-property is the import function for mixing.</p>

<pre><code>@mixin button {
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
</code></pre>

<p>Well. So far no bigger difference between the two. But the generated CSS tell us a different story. </p>

<pre><code>.error-button {
    margin: 0 10px; 
    /* error-button specific styles */ 
}

.success-button {
    margin: 0 10px; 
    /* success-button specific styles */ 
}
</code></pre>

<p>The bundling that happened in our previous example is gone and the era of repeated CSS is here. </p>

<h2>Why care about repeated code?</h2>

<p>Since the preprocessor made an entry to the stage of CSS we nowadays doesn’t operate in the CSS files anymore. Soo.. why care about what code we generate? </p>

<p>There are several reasons</p>

<ul>
<li>The size of the css file</li>
<li>Optimising the sites speed</li>
<li>We still maintain css…</li>
</ul>

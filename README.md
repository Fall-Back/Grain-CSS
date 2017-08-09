Grain-CSS
=========

Grain-CSS is a collection of Tachyon-esque mixins design to help with building CSS quickly.


By itself the main SCSS file does nothing. It's used by Grain-Classes file to generate a CSS file containing many useful granular classes.
It's intented to allow for quick prototyping in the browser - simply adding the classes to elements as needed.

If you want to use this methodology in production, then that's great.
However, it doesn't stop there.
Once you're happy with how things are looking and behaving, you can start to include the mixins inside whatever selectors you choose; if you include all the mixins as you did classes on the elements, then you'll end up with same result.

Note Grain-CSS is designed to sit on top of Start-CSS so some classes and overrides you see here are because of that.

So take for example a simple single column, sticy-footer page layout:

~~~
<body class="flex-container  flex-container--column  padding-0">

    <header class="padding(m)  margin(0)">
        ...
    </header>
    
        
    <main class="flex-grow(1)  padding(m)">
        ...
    </main>
    
    <footer class="margin(0)">
        ...
    </footer>
    
</body>
~~~

Then, if you wanted to take a component-based approach to your CSS, you might restructure your HTML to this:

~~~
<body class="page">

    <header class="page__banner">
        ...
    </header>
    
        
    <main class="page__main">
        ...
    </main>
    
    <footer class="page__footer">
        ...
    </footer>
    
</body>
~~~

And your SCSS file would look something like this:

~~~
.page {
    @include flex-container();
    @include flex-container--column();
    @include padding(0);
}

    .page__banner {
        @include flex-grow(1);
        @include margin(0);
    }
    
    .page__main {
        @include padding(m);
        @include margin(0);
    }
    
    .page__footer {
        @include margin(0);
    }
~~~

If you wanted to a purley elemental approach, you amy have this instead:

~~~
<body>

    <header>
        ...
    </header>
    
        
    <main>
        ...
    </main>
    
    <footer>
        ...
    </footer>
    
</body>
~~~

And your SCSS file would then look something like this:

~~~
body {
    @include flex-container();
    @include flex-container--column();
    @include padding(0);
}

    body > header {
        @include flex-grow(1);
        @include margin(0);
    }
    
    body > main {
        @include padding(m);
        @include margin(0);
    }
    
    body > footer {
        @include margin(0);
    }
~~~
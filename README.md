[![build status](https://secure.travis-ci.org/kaleb/ck.png)](http://travis-ci.org/kaleb/ck)
a smaller, faster [coffeekup](https://github.com/mauricemach/coffeekup)

    $ cake bench
    ck: 268ms
    ck (format): 316ms
    coffeekup: 301ms
    coffeekup (format): 974ms

#subtractions

* no cache; manage it on your own.
* must compile templates before rendering them
* no support for browsers, frameworks
* no cli tools
* no `scope` option (use context instead)

#additions

compileFile:

    template = ck.compileFile './template.coffee'
    html = template context: user: {}
    console.log html

correctly handle booleans:

    template = -> input autocomplete: off
    console.log ck.compile(template)() #<input>
    console.log coffeekup.render template #<input autocomplete="false" />

IE conditionals:

    ie 'lt IE8', ->
      link href: 'ie.css', rel: 'stylesheet'

#other

ck doesn't add slashes to self closing tags. I'm not actually sure what's right, see [this](http://stackoverflow.com/questions/348736/xhtml-is-writing-self-closing-tags-for-elements-not-traditionally-empty-bad-pra) for some reading....

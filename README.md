# fixpack

A package.json file scrubber for the truly insane.

It will re-write your package.json file as follows:

- name first
- description second
- version third
- author fourth
- all other keys in alphabetical order
- dependencies and devDependencies sorted alphabetically
- newline at the end of the file

It will warn you if any of these are missing:

- description
- author
- repository
- keywords
- main
- bugs
- homepage
- license'

Fix all indenting to 2 spaces.

Oh, and it will tolerate improperly quoted and comma'd JSON thanks to [ALCE](https://npmjs.org/package/alce).

## Usage

1. install it globally

```
npm i -g fixpack
```

2. run it in the same directory as your package.json, that's it.

```
fixpack
```

## What you might do if you're clever

```
npm i cool_package --save && fixpack
```

## Configuration

It's configurable. You can create a `.fixpackrc` file in your project or anywhere up the tree to your `$HOME` directory. Or overwrite options via CLI arguments.

Uses the [rc](https://www.npmjs.com/package/rc) module to do this. So you can pass all these as CLI args too.

The available options and their defaults shown below: 

```js

{
    // will put these first in this order if present
    sortToTop: [
        'name',
        'description',
        'version',
        'author'
    ],
    // will error if these not present
    required: [
        'name',
        'version'
    ],
    // will warn if these not present
    warn: [
        'description',
        'author',
        'repository',
        'keywords',
        'main',
        'bugs',
        'homepage',
        'license'
    ],
    // if `private: true` in package.json will use the next two lists instead
    requiredOnPrivate: [],
    warnOnPrivate: ['name', 'version', 'description', 'main'],
    // sub items to sort by default
    sortedSubItems: [
        'dependencies',
        'devDependencies',
        'jshintConfig',
        'scripts',
        'keywords'
    ],
    // if you set quiet to true it won't do output anything to the console
    quiet: false   
}

```

## Changelog

- 1.3.0 - configurable via `.fixpackrc` 
- x.x.x - unknown miscellaneous madness and poor version tracking
- 0.0.2 [diff](https://github.com/HenrikJoreteg/fixpack/compare/v0.0.1...v0.0.2) - EOF newline
- 0.0.1 - initial release

## Credits

This embarrassing display of insanity,
type-A-ness, and OCD brought to you by [@HenrikJoreteg](http://twitter.com/henrikjoreteg).

## License

MIT

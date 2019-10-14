# password

This generator uses [wordgenie](https://www.npmjs.com/package/wordgenie) to generate a password of `N` words
and Dropbox's [zxcvbn](https://github.com/dropbox/zxcvbn) to test that password's strength.

I use this generator when I need a password that I cannot store in a password
manager (e.g. a new master password for 1Password, LastPass, Dashlane, etc.)

I'll soon add options to change the source pool of words, the number of
words to be generated and a custom separator (i.e. `%`, `|` instead of `-`)

Be safe out there 🖖

----

## TODO

- Maybe swap out `wordgenie` for [instagrammar](https://www.npmjs.com/package/instagrammar), since its grammar
syntatic rules would allow us to generate more memorable passwords in the form of
```
[noun]-[verb]-[adjective]-[noun]
```

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Run your unit tests
```
npm run test:unit
```

### Lints and fixes files
```
npm run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).

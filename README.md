# Emoji Dictionary
http://emoji-dict.com

A dictionary of [emoji](http://en.wikipedia.org/wiki/Emoji) slangs.

## Contribution

* Add a file to the [dict folder](https://github.com/emoji-dict/emoji-dict.github.io/tree/master/dict) with name in the format of `<EMOJI_SLANG>.json`.
The schema looks like this:

```json
{
  "emoji": <EMOJI_SLANG>,
  "def": <EMOJI_DEFINITION>
}
```

There's a `Rake` task to automate the generation:

```sh
$ bundle install
$ rake new EMOJI=<EMOJI_SLANG> DEF=<EMOJI_DEFINITION>
```

* Create a pull request

## Deployment

[emoji-dict.com](http://emoji-dict.com) is hosted as a static page on [GitHub Pages](https://pages.github.com/).
To regenerate the site, you need to run

```sh
$ bundle install
$ rake build # `jekyll serve -w` to serve page on localhost:4000
```

And then push all generated files to GitHub.

## License

See
[LICENSE.md](https://github.com/emoji-dict/emoji-dict.github.io/blob/master/LICENSE.md).

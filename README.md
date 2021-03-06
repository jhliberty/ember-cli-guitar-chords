# Ember-cli-guitar-chords

A simple ember component wrapper for <a href='http://chordography.blogspot.co.uk/'>Chordography</a> and <a href='https://github.com/keithwhor/audiosynth'>AudioSynth</a> for easily displaying
guitar chord diagrams with optional audio.

Turns this:

```html
   {{guitar-chords title='Amaj7#11' fret='5,x,7,6,4,4' label='2,x,4,3,1,1'}}
```

into this:

![ScreenShot](http://i.imgur.com/NAvrmef.png)

## Using with an Ember CLI project

`npm install --save ember-cli-guitar-chords`

Then you can use the `{{guitar-chords}}` component.

The component takes 5 attributes: title, fret, label, music, and button-class.
The `fret` attr is used to make a computed property `id` and is required to
be present and unique for the image to render. Unfortunately, this means that
you cannot display the same chord twice on one page for the moment :(.

The `music` attr is a boolean, `default true`, that shows a `Play!` button.

The chord chart and play button are each wrapped in `div` to style as needed. The
`button-class` attr is so you can add css framework classes to the button.

Bootstrap example:
```html
{{guitar-chords button-class='btn btn-primary' title='Amaj7#11' fret='5,x,7,6,4,4' label='2,x,4,3,1,1'}}
```

```
<div class='guitar-chords guitar-tab'>
  <svg class='chordChart' {{bind-attr id=id title=title fret=fret label=label footer=footer music=music}} class="chordChart"></svg>
</div>

{{#if music}}
  <div class='guitar-chords guitar-music'>
    <button {{bind-attr class=button-class}} {{action 'playMusic'}}>Play!</button>
  </div>
{{/if}}
```

## Contributing

Do it!

## Installation

* `git clone` this repository
* `npm install`
* `bower install`

## Running

* `ember server`
* Visit your app at http://localhost:4200.

## Running Tests

* `ember test`
* `ember test --server`

## Building

* `ember build`

For more information on using ember-cli, visit [http://www.ember-cli.com/](http://www.ember-cli.com/).

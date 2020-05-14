# Boiled Page progress component

Progress SCSS component for Boiled Page frontend framework. It is intended to create progress bars.

## Install

Place `_progress.scss` file to `/assets/css/components` directory, and add its path to components block in `assets/css/app.scss` file.

## Usage

### Classes

Class name | Description | Example
---------- | ----------- | -------
`progress` | Applies a progress. | `<progress class="progress"></progress>`

### Examples

#### Example 1

The following example shows a progress.

```html
<progress class="progress" value="70" max="100">70%</progress>
```

### Extension ideas

#### Small progress

```scss
/* Progress component extensions */
progress.progress {

  // Small progress
  &.progress--small {
    height: 0.5em;
  }
}
```

#### Large progress

```scss
/* Progress component extensions */
progress.progress {

  // Large progress
  &.progress--large {
    height: 1em;
  }
}
```

#### Scheme colored progress

Add `generate-progress` to each scheme in SCSS variables with the value of true or false. Then you can use progresses in colors of enabled schemes.

```scss
/* Progress component extensions */
progress.progress {

  // Scheme colored progresses
  @each $scheme in map-keys($schemes) {
    @if (map-val($schemes, $scheme, generate-progress)) {
      &.progress--#{$scheme} {

        &::-webkit-progress-value {
          background: map-val($schemes, $scheme, bg-color);
        }

        &::-moz-progress-bar {
          background: map-val($schemes, $scheme, bg-color);
        }

        &::-ms-fill {
          background: map-val($schemes, $scheme, bg-color);
        }
      }
    }
  }
}
```
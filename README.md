# Svelte-preview-card

Basic card presenting a title, sub-text, and background image ideally for a grid layout. Also has an event emitter for when it has been clicked.

Demo: http://linkcube.github.io/

## Styling

This part is going to be fairly rough until I figure out a standard for themeing across my components, but for now it exposes raw color values for the text and background states.

## Usage

```
let src = "my picture";
<PreviewCard
    background_source={src}
    primary_text="Title"
    sub_text="My Picture"
></PreviewCard>
```


Exposed Events:

Event | Description
-- | --
`on:open` | When the card is clicked

Optional settings:

Param | Description | Type
--- | --- | ---
`background_source` | Source for the card's image, defaults to none | String
`primary_text` `sub_text` | Displayed text values, if these are not used the image max-height is increased. | String
`alt_text` | Alt text for the image | String
`disabled` | Whether to disable the card from being clicked | Boolean
`background_color` `primary_text_color` `sub_text_color` | Basic color values | String
`active_color` | Background color of the card when the mouse is held down on it | String
`focus_color` | Background color of the card if clicked | String

## Links

[Github](https://github.com/Linkcube/svelte-preview-card)

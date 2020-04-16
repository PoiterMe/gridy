# gridy
SCSS bundle for building a minimal flexible Grid. Not like "Bootstrap" and other frameworks it will deliver a minimum of functionality. 
Define the Grid once and later on u can easily extend it. 

1) after downloading, move to the file "gridy/index.scss" and edit this config file to fit ur needs
```scss
// $GRID_TILES - 100%/$GRID_TILES
$GRID_TILES: 12;

// $GRID_CONTAINER_SELECTOR - grid container selector
$GRID_CONTAINER_SELECTOR: ".container";

// $GRID_ITEM_SELECTOR - grid item selector
$GRID_ITEM_SELECTOR: ".col";

// $GRID_WRAPPPER_SELECTOR - selector of the wrapping container
$GRID_WRAPPPER_SELECTOR: ".row";

// $GRID_SPACING - spacing for ur items
$GRID_SPACING: 1rem;

// $GRID_UNIT - choose a which unit you want to use
$GRID_UNIT: "px";

/*
  $GRID_BREAKPOINTS is a list with a variable number of values, each represent a breakpoint
  @example
  --------------------
  $GRID_BREAKPOINTS : (400, 1170);
  generated breakpoints :  0-400; 400-1170; 1170-(∞)

  $GRID_BREAKPOINTS : (544, 768, 992, 1200);
  generated breakpoints :  0-544; 544-768; 768-992; 992-1200 1200-(∞)
*/
$GRID_BREAKPOINTS: (544, 768, 992, 1200);

$GRID_ITEMS: (
                ($GRID_TILES, full),
                (6, half),
                (6, 4, 4, 4, 4, gal),
                (6, 6, 4, 4, 4, card),
                (12, 5, 4, 3, 3, side),
                (12, 7, 8, 9, 9, content),
                (12, 12, 6, 6, 6, footer)
);
@mixin GRID_ROW_STYLES {
}

@mixin GRID_TILE_STYLES {
  box-shadow: 0 0 0 1px black inset;
}

@mixin GRID_TILE_INNER_STYLES {
}

@import "../gridy/flexFunctions";
@import "../gridy/flexQueryMixin";
@import "../gridy/_flexGrid";
```
2) import the file "gridy/index.scss" in ur allready exicting SCSS Project.

```scss
@import "gridy/index.scss"
```

3) Build SCSS with the Compiler of ur choice and enjoy


```html
 <div class="container">
        <div class="row">
            <div class="col">Lorem ipsum dolor sit amet, consectetur adipisicing elit. Accusamus aliquam assumenda
                beatae, consectetur dolorum eius eum explicabo fugiat iusto laborum, odio perferendis quae qui quis
                ratione repudiandae temporibus totam ullam?
            </div>
            <div class="col_content">Aliquam aliquid animi aperiam dolor, molestiae nemo, neque non numquam odit possimus quia
                soluta. Aperiam dignissimos eligendi et id illum nostrum, nulla placeat, possimus quas, qui quidem
                sapiente suscipit veritatis.
            </div>
            <div class="col">Dolor eum fuga iure nihil nisi placeat quas tempora, tempore? Dolore eos hic nostrum quos
                sint tempore, vitae? Autem dignissimos esse explicabo ipsum minima mollitia odio praesentium rerum ullam
                vitae.
            </div>
        </div>
        <div class="row">
            <div class="col_side">Lorem ipsum dolor sit amet, consectetur adipisicing elit. Accusamus aliquam assumenda
                beatae, consectetur dolorum eius eum explicabo fugiat iusto laborum, odio perferendis quae qui quis
                ratione repudiandae temporibus totam ullam?
            </div>
            <div class="col_content">Aliquam aliquid animi aperiam dolor, molestiae nemo, neque non numquam odit possimus quia
                soluta. Aperiam dignissimos eligendi et id illum nostrum, nulla placeat, possimus quas, qui quidem
                sapiente suscipit veritatis.
            </div>
        </div>
    </div>
```


**the result:**
```css
@charset "UTF-8";
.container {
  width: 100%;
  padding-right: 1rem;
  padding-left: 1rem;
  margin-right: auto;
  margin-left: auto; }
  .container, .container * {
    box-sizing: border-box; }

.row {
  margin-left: -1rem;
  margin-right: -1rem;
  display: flex;
  flex-wrap: wrap;
  justify-content: flex-start; }
  .row .bottomSpace {
    margin-bottom: 2rem; }

.col {
  flex-grow: 1;
  max-width: 100%;
  -ms-flex-preferred-size: 0;
  flex-basis: 0;
  -webkit-box-flex: 1;
  -ms-flex-positive: 1; }

[class*="col_"]:not(.no_grow) {
  flex-grow: 1; }

[class*="col_"], .col {
  padding: 1rem;
  box-shadow: 0 0 0 1px black inset; }

.col_full {
  width: 100%; }

.col_half {
  width: 50%; }

@media (max-width: 544px) {
  .col_gal {
    width: 50%; }
  .col_card {
    width: 50%; }
  .col_side {
    width: 100%; }
  .col_content {
    width: 100%; }
  .col_footer {
    width: 100%; } }

@media (min-width: 544px) and (max-width: 768px) {
  .col_gal {
    width: 33.33333%; }
  .col_card {
    width: 50%; }
  .col_side {
    width: 41.66667%; }
  .col_content {
    width: 58.33333%; }
  .col_footer {
    width: 100%; } }

@media (min-width: 768px) and (max-width: 992px) {
  .col_gal {
    width: 33.33333%; }
  .col_card {
    width: 33.33333%; }
  .col_side {
    width: 33.33333%; }
  .col_content {
    width: 66.66667%; }
  .col_footer {
    width: 50%; } }

@media (min-width: 992px) and (max-width: 1200px) {
  .col_gal {
    width: 33.33333%; }
  .col_card {
    width: 33.33333%; }
  .col_side {
    width: 25%; }
  .col_content {
    width: 75%; }
  .col_footer {
    width: 50%; } }

@media (min-width: 1200px) {
  .col_gal {
    width: 33.33333%; }
  .col_card {
    width: 33.33333%; }
  .col_side {
    width: 25%; }
  .col_content {
    width: 75%; }
  .col_footer {
    width: 50%; } }

.row .no-gutters {
  margin-right: 0;
  margin-left: 0; }

.row.flex-direction_row {
  flex-direction: row; }

.row.flex-direction_row-reverse {
  flex-direction: row-reverse; }

.row.flex-direction_column {
  flex-direction: column; }

.row.flex-direction_column-reverse {
  flex-direction: column-reverse; }

.row.flex-wrap_nowrap {
  flex-wrap: nowrap; }

.row.flex-wrap_wrap {
  flex-wrap: wrap; }

.row.flex-wrap_wrap-reverse {
  flex-wrap: wrap-reverse; }

.row.justify-content_flex-start {
  justify-content: flex-start; }

.row.justify-content_flex-end {
  justify-content: flex-end; }

.row.justify-content_center {
  justify-content: center; }

.row.justify-content_space-between {
  justify-content: space-between; }

.row.justify-content_space-around {
  justify-content: space-around; }

.row.align-items_flex-start {
  align-items: flex-start; }

.row.align-items_flex-end {
  align-items: flex-end; }

.row.align-items_center {
  align-items: center; }

.row.align-items_baseline {
  align-items: baseline; }

.row.align-items_stretch {
  align-items: stretch; }

.row.align-content_flex-start {
  align-content: flex-start; }

.row.align-content_flex-end {
  align-content: flex-end; }

.row.align-content_center {
  align-content: center; }

.row.align-content_space-between {
  align-content: space-between; }

.row.align-content_space-around {
  align-content: space-around; }

.row.align-content_stretch {
  align-content: stretch; }

.no-gutters [class*="col_"], .no-gutters .col {
  padding-right: 0;
  padding-left: 0; }

[class*="col_"].align_self-start, .col.align_self-start {
  align-self: flex-start !important; }

[class*="col_"].align_self-center, .col.align_self-center {
  align-self: center !important; }

[class*="col_"].align_self-end, .col.align_self-end {
  align-self: flex-end !important; }

```





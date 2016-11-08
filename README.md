# gridy
SCSS bundle for building a minimal flexible Grid. Not like "Bootstrap" and other frameworks it will deliver a minimum of functionality. 
Define the Grid once and later on u can easily extend it. 

1) after downloading, move to the file "gridy/index.scss" and edit this config file to fit ur needs
```scss
$GRID_TILES: 12;
$GRID_ITEM_SELECTOR_PREFIX: "tile";
$GRID_WRAPPPER_SELECTOR: ".row";

$GRID_SPACING: .5em;
$GRID_UNIT: "px";

/*
  0 <-> $GRID_BREAKPOINTS[1]+$GRID_UNIT
  $GRID_BREAKPOINTS[1]+$GRID_UNIT <-> $GRID_BREAKPOINTS[2]+$GRID_UNIT
  [..]
  $GRID_BREAKPOINTS[x-1]+$GRID_UNIT <-> $GRID_BREAKPOINTS[x]+$GRID_UNIT
  $GRID_BREAKPOINTS[x]+$GRID_UNIT <-> (∞)

  @example
  --------------------
  $GRID_BREAKPOINTS : (400, 1170);
  generated breakpoints :  0-400; 400-1170; 1170-(∞)
  $GRID_BREAKPOINTS : (400, 700, 1170);
  generated breakpoints :  0-400; 400-700; 700-1170; 1170-(∞)
*/
$GRID_BREAKPOINTS: (544, 768, 992, 1200);

$GRID_ITEMS: (
    ($GRID_TILES, full),
    ($GRID_TILES, $GRID_TILES/2, $GRID_TILES/2, $GRID_TILES/4, $GRID_TILES/6, standard)
);

@mixin GRID_ROW_STYLES {
}
@mixin GRID_TILE_STYLES {
}
@mixin GRID_TILE_INNER_STYLES {
  background: #eee;
}

@import "flexFunctions";
@import "flexQueryMixin";
@import "flexGrid";

```
2) import the file "gridy/index.scss" in ur allready exicting SCSS Project.

```scss
@import "gridy/index.scss"
```

3) Build SCSS with the Compiler of ur choice and enjoy


```html
<!-- 
This will break like u defined in ur gridy/index.scss 
0-544 : 1
544-768 : 1/2
768-992 : 1/2
992-1200 : 1/3
1200-∞ : 1/4
-->
<div class="row">
    <div class="tile_standard">
        <div class="inner">Lorem ipsum dolor sit amet, ..</div>
    </div>
</div>
```


**the result:**
```css
.row .bottomSpace {
  margin-bottom: 1em; }

.row {
  display: flex;
  flex-wrap: wrap;
  justify-content: flex-start; }
  .row:after {
    content: ".";
    clear: both;
    display: block;
    visibility: hidden;
    height: 0px; }
  .row, .row * {
    box-sizing: border-box;
    -moz-box-sizing: border-box;
    -webkit-box-sizing: border-box; }
  .row.d_row {
    flex-direction: row; }
  .row.d_row-reverse {
    flex-direction: row-reverse; }
  .row.d_column {
    flex-direction: column; }
  .row.d_column-reverse {
    flex-direction: column-reverse; }
  .row.fW_nowrap {
    flex-wrap: nowrap; }
  .row.fW_wrap {
    flex-wrap: wrap; }
  .row.fW_wrap-reverse {
    flex-wrap: wrap-reverse; }
  .row.jC_flex-start {
    justify-content: flex-start; }
  .row.jC_flex-end {
    justify-content: flex-end; }
  .row.jC_center {
    justify-content: center; }
  .row.jC_space-between {
    justify-content: space-between; }
  .row.jC_space-around {
    justify-content: space-around; }
  .row.aI_flex-start {
    align-items: flex-start; }
  .row.aI_flex-end {
    align-items: flex-end; }
  .row.aI_center {
    align-items: center; }
  .row.aI_baseline {
    align-items: baseline; }
  .row.aI_stretch {
    align-items: stretch; }
  .row.aC_flex-start {
    align-content: flex-start; }
  .row.aC_flex-end {
    align-content: flex-end; }
  .row.aC_center {
    align-content: center; }
  .row.aC_space-between {
    align-content: space-between; }
  .row.aC_space-around {
    align-content: space-around; }
  .row.aC_stretch {
    align-content: stretch; }
  .row [class^="tile"] {
    float: left;
    display: flex;
    align-items: stretch;
    flex-grow: 1;
    padding: 0.5em; }
    .row [class^="tile"] .inner {
      width: 100%;
      padding: 0.5em;
      background: #eee; }
  .row .tile_full {
    width: 100%; }
  @media (max-width: 544px) {
    .row .tile_standard {
      width: 100%; } }
  @media (min-width: 544px) and (max-width: 768px) {
    .row .tile_standard {
      width: 50%; } }
  @media (min-width: 768px) and (max-width: 992px) {
    .row .tile_standard {
      width: 50%; } }
  @media (min-width: 992px) and (max-width: 1200px) {
    .row .tile_standard {
      width: 25%; } }
  @media (min-width: 1200px) {
    .row .tile_standard {
      width: 16.66667%; } }

/*# sourceMappingURL=bundle.css.map */
```





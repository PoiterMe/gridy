# gridy
SCSS bundle for building a minimal flexible Grid

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




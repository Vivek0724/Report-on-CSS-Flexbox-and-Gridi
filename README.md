# Report on CSS Flexbox and Grid with Code Samples

## CSS FLEXBOX

     _Flexbox is a layout mode in CSS3. It’s a more proficient approach to designing, aligning, and disseminating space between items in a container to control their arrangement.

With Flexbox, we can arrange items left to right, right to left, top to bottom, or bottom to top and, at the same time, control the spacing, alignment, and order of items in the container._

## GRID
      _CSS Grid Layout, is a two-dimensional grid-based layout system with rows and columns, making it easier to design web pages without having to use floats and positioning. Like tables, grid layout allow us to align elements into columns and rows.
To get started you have to define a container element as a grid with display: grid, set the column and row sizes with grid-template-columns and grid-template-rows, and then place its child elements into the grid with grid-column and grid-row._

##UNIQUENESS IN GRID AND FLEXBOX:

**One Vs Two Dimension:**

    -Grid is made for two-dimensional layout while Flexbox is for one. This means Flexbox can work on either row or columns at a time, but Grids can work on both.
    -Flexbox, gives you more flexibility while working on either element (row or column). HTML markup and CSS will be easy to manage in this type of scenario.

**Content-First vs Layout-First:**

   - Major Uniqueness between Flexbox and Grids is that the former works on content while the latter is based on the layout.
   -The Flexbox layout is best suited to application components and small-scale layouts, while the Grid layout is designed for larger-scale layouts that are not linear in design.
##DIFFERENCE BETWEEN GRID AND FLEXBOX :
     
  **1. Dimensionality and Flexibility :**
      
        -Flexbox offers greater control over alignment and space distribution between items. Being one-dimensional, Flexbox only deals with either columns or rows.
        -Grid has two-dimension layout capabilities which allow flexible widths as a unit of length. This compensates for the limitations in Flex.

**2. Aligenment:**
          
        -Flex Direction allows developers to align elements vertically or horizontally, which is used when developers create and reverse rows or columns.
        -CSS Grid deploys fractional measure units for grid fluidity and auto-keyword functionality to automatically adjust columns or rows.

**3. Item Management:
      
       - Flex Container is the parent element while Flex Item represents the children. The Flex Container can ensure balanced representation by adjusting item dimensions. This allows developers to design for fluctuating screen sizes.
       -Grid supports both implicit and explicit content placement. Its inbuilt automation allows it to automatically extend line items and copy values into the new creation from the preceding item.

  |PROPERTY|  |GRID|  |FLEXBOX|
  |---|  |---|  |---|
  |Dimension|  |Two-Dimensional|  |One-Dimensional|
  |Features|  |Can flex combination of items through space-occupying Features|  |Can push content element to extreme alignment|
  |Support type|  |Layout first|  |content first|
 
## FLEXGRID.CSS CODE :

```
  
.row {
    display: flex;
    width: 100%;
    flex-flow: row;
    flex-direction:row; 
    flex-wrap: wrap;
    justify-content: space-around;
    box-sizing: border-box;
}

.col-12 {
    flex-basis: 100%;
    max-width: 100%;
}

.col-6 {
    flex-basis: 50%;
    max-width: 50%;
}

.col-4 {
    flex-basis: 33%;
    max-width: 33%;
}

.col-4 {
    flex-basis: 33%;
    max-width: 33%;
}


.col-1 {
    flex-basis: 8.33%;
    max-width: 8.33%;
} 

```
![Flex-Grid](https://raw.githubusercontent.com/ritwickdey/sample-css-flex-grid/master/img/Flex-Grid.png)

## CONCLUSION 
   
   - CSS Grids helps you create the outer layout of the webpage. You can build complex as well responsive design with this. This is why it is called ‘layout first’.
   - Flexbox mostly helps align content & move blocks.
   -CSS grids are for 2D layouts. It works with both rows and columns.
   -Flexbox works better in one dimension only (either rows OR columns).
   -It will be more time saving and helpful if you use both at the same time.

**REFERENCE LINKS 
  
 -[Basic concepts of flexbox](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Flexible_Box_Layout/Basic_Concepts_of_Flexbox)
 
 -[complete guide grid](https://css-tricks.com/snippets/css/complete-guide-grid/)

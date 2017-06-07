# Dynamik Recipe LaTeX-Class
`recipes.sty` is a LaTeX2e-class for typesetting recipes with dynamik
calculation of the needed amount based on the coded proportions.
In practice: One easily typesets the recipe with proportions as found
(e.g. on the internet) with the help of the given commands. This then
will compile to a form which accepts any other number of portions and
directly calculates and shows the needed amounts of ingredients.

**Warnings:**
1. Dynamic properties are by the time only available in
  * Browsers (tested with Chromium)
  * Acrobat Reader
2. Be aware that you need the package `insdljs` out of the `acrotex`
   collection (not contained in standard TeXLive-distribution)

## Provided Commands/Environments
This package provides commands to start a recipe block,
specify steps and annotate the needed ingredients.

Comments (meaning text not within an ingredient-commad) are better
only inserted between steps, not between ingredients. Though possible,
it will be written over the complete text-width and thus fit badly
into the layout.

The commands `recipe.sty` provides are:

### Environment `recipe`
Usage:
```latex
\begin{recipe}%
	{<title/name of the recipe>}%
	{<default no. of portions>}[<opt. portion descr. (e.g. pieces)>]%
	{<total preparation time>}
	…
\end{recipe}
```
### Environment `step`
Only to be used within `recipe` environment;
Usage:
```latex
\begin{step}{<description>}…\end{step}
```

### Command `\ingredient`
Only to be used within `step` environment;
Usage:
```latex
\ingredient%
	{<amount>}[<unit, e.g. liter,pcs …>]%
	{<ingredient description, e.g. eggs>}
```

### Command `\Ingredient`
Only to be used within `step` environment; 
same as `\ingredient` but without amount & unit;
Usage:
```latex
\Ingredient{<just the description, %
	e.g. "as much chocolate as you have"}
```

### Adjustable Lengths, `\renewlength`, `\resetlengths`
To change block lengths locally, please use
```latex
\renewlength{<lengthname>}{<dimension>}
```
Available legth names are (usage as the names suggest):
- `amountwidth`
- `unitwidth`
- `descriptionwidth`
- `ingredienttextskip`

You can reset to default with `\resetlengths`.

## Compilation
As mentioned before, make shure the class `insdljs` out of the
`acrotex` collection is available in the TeX-tree. Then call
```latex
pdflatex <file.tex>
```

## Layout and Examples
### On the Layout
For each recipe you will get a minimalistic layout with steps on the
right and necessary (new) ingredients & amounts as comments to the
left.
Many experiments with my favorite recipes yielded this as best
arrangement for combining overview, shopping list and to-do list. 

### Examples
To get an impression what is possible an how (even crazy) arrangements
look like with the commands/environments from above, see
`test_recipe.tex` (and `.pdf`).
To see how a recipe actually could look like, have a look at
`chocolate_cookies.tex` (and `.pdf`).

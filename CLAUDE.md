# Project Memory: Handbook of Mathematical Psychology

## User Learning Style

When creating educational demos (Quarto documents), follow these principles:

### 1. Concrete Before Abstract
- Start with specific numerical examples before general formulas
- Use 2D/matrix examples to show variables explicitly (not 1D simplifications)
- Show actual numbers: "If threshold = 0.005, then sensitivity = 200"

### 2. Split Complex Into Small Steps
- Break long code chunks into small, focused pieces
- Each chunk should do ONE thing
- Add explanatory text between chunks

### 3. Visual/Graphical Explanations
- Draw plots to explain algebraic concepts
- Use 3D surface plots (persp()) when helpful
- Show contour plots for 2D relationships
- Visualize matrices as heatmaps or grids

### 4. Explicit Code Over Abstractions
- Prefer `for` loops over `apply()` family
- Show each step explicitly, even if verbose
- Avoid clever one-liners that hide logic

### 5. Explain Every Function
- When introducing a new function, explain:
  - What it does
  - What each argument means
  - What it returns
- Examples: `rpois()`, `dpois()`, `dmvnorm()`, `optim()`

### 6. Ask "Why" At Each Step
- Anticipate "why" questions and answer them proactively
- "Why log?" → numerical stability, spans orders of magnitude
- "Why transpose?" → matrix dimensions must match
- "Why sum?" → dot product computation

### 7. Connect Math to Real-World
- Always show how abstract concepts connect to actual experiments
- Example: "Each sensitivity value = ~100 behavioral trials"
- Show the full pipeline: behavior → threshold → sensitivity → CSF

### 8. Show the Process, Not Just Results
- Visualize optimization steps (walking downhill)
- Show iteration-by-iteration progress
- Don't just show final answer, show how we got there

### 9. Use Tables for Summaries
- Parameter summary tables work well
- "What each parameter controls" tables
- Before/after comparison tables

### 10. Callout Boxes for Key Concepts
- `::: {.callout-note}` for explanations
- `::: {.callout-tip}` for summaries
- `::: {.callout-important}` for must-know facts
- `::: {.callout-warning}` for common pitfalls

## Code Style for Demos

```r
# GOOD: Explicit for loop
for (i in 1:nrow(grid)) {
  x1 <- grid$x1[i]
  x2 <- grid$x2[i]
  point <- c(x1, x2)
  density <- dmvnorm(point, mu, Sigma)
  grid$density[i] <- density
}

# AVOID: Abstract apply (harder to understand)
grid$density <- apply(grid, 1, function(row) dmvnorm(as.numeric(row), mu, Sigma))
```

## Chunk Naming Convention

Use descriptive, hierarchical names:
- `gaussian-prior-setup`
- `gaussian-prior-params`
- `gaussian-prior-2d`
- `gaussian-prior-3d`

## Project Structure

- `demos/` - Quarto educational documents
- `pdf/` - Source PDFs and section splits
- `pdf/*/sections/` - Markdown summaries of PDF sections

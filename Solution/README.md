# Blazor Puzzle #10

## Stop The Rendering

YouTube Video: https://youtu.be/I5sZWpOvmdE

BlazorPuzzle Home Page: https://blazorpuzzle.com

### The Challenge:

Why does this child component keep rendering? How can we stop it?

### The Solution:

To prevent the Label, or any component, from rendering, you can override the `ShouldRender` method:

*Label.razor*

```c#
<p role="status">@ChildContent</p>

@code {

	[Parameter]
	public RenderFragment ChildContent { get; set; }

	protected override void OnAfterRender(bool first)
	{
		Console.WriteLine($"{DateTime.Now.ToLongTimeString()} - Rendered");
		base.OnAfterRender(first);
	}

	protected override bool ShouldRender()
	{
		return false;
	}
}
```


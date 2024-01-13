# Laravel Blade Implode and Link Model Collection

A Laravel and Blade component to show a linked list of models.

Given a collection of models the default component will produce the following HTML.

```html
<span>
  <a href="link1" title="View the PHP page">PHP</a>,
  <a href="link2" title="View the CSS page">CSS</a>,
  <a href="link3" title="View the HTML page">HTML</a> and 
  <a href="link4" title="View the Python page">PHP</a> 
</span>
```

## Usage

```blade
  <x-implode-and-link-model-collection :models="$project->skills" />
```

### Define a custom name

By default the `$mode->name` attribute will be used. You can pass a string to use a different attribute on the mode 

```blade
  <x-implode-and-link-model-collection
    :models="$project->skills"
    nameAttribute="fullName"
  />
```

Or you can pass a Closure to define you own name string using the passed in model.

```blade
  <x-implode-and-link-model-collection
    :models="$project->skills"
    :nameAttribute="fn($model) => sprintf('%s %s', $model->firstname, $model->surname)"
  />
```

### Define a custom route

By default the component will use the `routeUrl` attribute on the model as the URL. You can pass any attribute as a string or a Closure to define you own routing.

```blade
  <x-implode-and-link-model-collection
    :models="$project->skills"
    :routeAttribute="fn($mode) => route('skills.show', $model)"
  />
```

### Adding classes to the <a> tag

```blade
  <x-implode-and-link-model-collection
    :models="$project->skills"
    a-class="text-primary-600 hover:text-secondary-700"
  />
```

### Adding extra attributes to the A tag

Any attributes passed that are prefixed with a- will be merged into the <a> attribute list.

Example using wire:click instead of href.

```blade
  <x-implode-and-link-model-collection
    :models="$project->skills"
    a-class="text-primary-600 hover:text-secondary-700"
    a-wire:click="fn($model) => sprintf('doClick(%d)', $model->id)"
  />
```

### Custom Seperators

xxxx

## Considerations

Remember to load your relationships before calling them in views.


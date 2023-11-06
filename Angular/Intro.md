# What is Angular

Is a development plataform that includes:

- A components based framework
- A collection of integrated libs
- A suite of dev tools to develop, build, test and update code.

> COMPONENTS

Components are building blocks that compose an app. Includes:

- html template
- Styles
- css selector
- typescrypt class for behavior

Components have a @Component() selector where the html template, style and selector of your component is defined:

```
@Component({
  selector: 'hello-world',
  templateUrl: './hello-world-bindings.component.html'
})
```
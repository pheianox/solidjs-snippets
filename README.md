![logo (3)](https://user-images.githubusercontent.com/77569421/208286821-41429336-d5b3-479f-8dfa-170a1c34c5f4.png)


# solidjs-snippets

> VSCode extension. Typescript first support

Automatic typed boilplates for fat and lazy devs 

* [Signal](#signal)
* [Store](#store)
* [Context](#context)
* [Component](#component)


## Signal
`si` - Signal

```ts
const [signal, setSignal] = createSignal()
```

## Store

`st` - Store

```ts
const [store, setStore] = createStore({})
```

`sti` - Store+Interface

```ts
interface Config {}

const [config, setConfig] = createStore<Config>({})
```

`sta` - Store+Actions

Ready to be used state management system

```ts
import { createStore } from 'solid-js/store'

interface AppState {}

interface AppActions {}

const [state, setState] = createStore<AppState>({})
const actions: AppActions = {}

export default { state, actions }
```

## Context

`ctx` - Context

Context with provider and custom hook

```ts
import { Component, createContext, JSXElement, useContext } from 'solid-js'

interface AppContext {}

interface AppContextProviderProps {
  children: JSXElement
}

const AppContext = createContext<AppContext>()

export function useAppContext() {
  const context = useContext(AppContext)
  if (!context) throw new Error(`Context 'AppContext' is null. Did you use <AppContextProvider>?`)
  return context
}

export const AppContextProvider: Component<AppContextProviderProps> = props => {
  const context: AppContext= {}
  return <AppContext.Provider value={context}>{props.children}</AppContext.Provider>
}
```

`ctxsta` - Context+Store+Actions

Ready to be useed state management system with its own context

```ts
import { Component, createContext, JSXElement, useContext } from 'solid-js'
import { createStore } from 'solid-js/store'

interface AppState {}

interface AppActions {}

interface AppProviderProps {
  children: JSXElement
}

const App = createContext<[AppState, AppActions]>()

export function useApp() {
  const context = useContext(App)
  if (!context) throw new Error(`Context 'App' is null. Did you use <AppProvider>?`)
  return context
}

export const AppProvider: Component<AppProviderProps> = props => {
  const [state, setState] = createStore<AppState>({})
  const actions: AppActions = {}
  return <App.Provider value={[state, actions]}>{props.children}</App.Provider>
}
```

## Component

`c` - Component

```ts
const Navbar: Component = () => {
  return (
    <div>Navbar</div>
  )
}
```

`cp` - Component+Props

```ts
interface NavbarProps {}

const Navbar: Component<NavbarProps> = props => {
  return (
    <div>Navbar</div>
  )
}
```

`ice` - Import Component Export

```ts
import { Component } from "solid-js"

const Navbar: Component = () => {
  return (
    <div>Navbar</div>
  )
}

export default Navbar
```

`icpe` - Import Component+Props Export

```ts
import { Component } from "solid-js"

interface NavbarProps {}

const Navbar: Component<NavbarProps> = props => {
  return (
    <div>Navbar</div>
  )
}

export default Navbar
```

`iec` - Import Export Component

```ts
import { Component } from "solid-js"

export const Navbar: Component = () => {
  return (
    <div>Navbar</div>
  )
}
```

`iecp` - Import Export Component+Props

```ts
import { Component } from "solid-js"

interface NavbarProps {}

export const Navbar: Component<NavbarProps> = props => {
  return (
    <div>Navbar</div>
  )
}
```

`f` - SolidJS For Component

```ts
...
  <For each={array}>
    {item => <Item item={item}}
  </For>
...
```

[Give a star on Github](https://github.com/pheianox/solidjs-snippets) if these snippets were useful

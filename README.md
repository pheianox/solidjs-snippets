# solidjs-snippets

Snippet pack for SolidJS


* [Signal](#signal)
* [Store](#store)
* [Context](#context)
* [Mixed](#mixed)
* [Component](#component)

<br />

## Signal
`si` - Signal
```ts
const [signal, setSignal] = createSignal()
```

<br />

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

<br />

## Context
`ctx` - Context
```ts
import { Component, createContext, JSXElement, useContext } from 'solid-js'

interface AppContext {}

interface AppContextProviderProps {
  children: JSXElement
}

const AppContext = createContext<AppContext>()

export function useAppContext() {
  const context = useContext(AppContext)
  if (!context) throw new Error(`Context 'AppContext' is null. Assure usage of <AppContextProvider>`)
  return context
}

export const AppContextProvider: Component<AppContextProviderProps> = props => {
  const context: AppContext= {}
  return <AppContext.Provider value={context}>{props.children}</AppContext.Provider>
}
```

<br />

## Mixed
`csa` - Context+State+Actions
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

<br />

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

const Navbar: Component = () => {
  return (
    <div>Navbar</div>
  )
}

export default Navbar
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

<br />

[Give a star on Github](https://github.com/pheianox/solidjs-snippets) if these snippets were useful
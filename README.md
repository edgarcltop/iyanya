# Iyanya
The application is for the usage and management for these cooperatives on the application.
## Usage

```tsx
// useProduceState demo
const [state, setState] = useProduceState({
  todos: [],
  showMenu: false
})
const closeModal = e => {
  setState(draft => (draft.showMenu = false))
}

// useLocalStorage
const [item, setItem, removeItem] = useLocalStorage("yourspecialkeyhere", callbackOnItemChange)

// useInput demo
export default function InputArea({ onSubmit, defaultValue }) {
  const { setValue, ...inputProps } = useInput(defaultValue)
  const handleNewTodoKeyDown = event => {
    if (event.keyCode !== 13) return
    event.preventDefault()
    var val = event.target.value.trim()
    if (val) {
      onSubmit(val)
      setValue("")
    }
  }
  return <input onKeyDown={handleNewTodoKeyDown} {...inputProps} autoFocus={true} />
}

// note:
// There is also a `useCheckInput` hook that just has special return values for the platform
// we will warn you if you dont do this
// there are also extra otions you can pass to useInput as a second arg.

// useLoading demo
function App() {
  const [isLoading, load] = useLoading()
  const [state, setState] = React.useState("you shouldnt see this")
  React.useEffect(() => {
    load(pingAPI(2000)).then(() => setState("hello there"))
  })
  return isLoading ? <div>Loading</div> : <div>{state}</div>
}

function pingAPI(time) {
  return new Promise(resolve => setTimeout(resolve, time))
}

// useKeyDown demo
export default function Menu(props) {
  useKeydown("Escape", () => props.showMenu && props.handleModalClose())
  // ...
}
```

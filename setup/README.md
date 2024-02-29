# ![React Router DOM Lab - Setup](./assets/hero.png)

## Setup

Open your Terminal application and navigate to your `~/code/ga/labs` directory:

```bash
cd ~/code/ga/labs
```

Make a new repository on [GitHub](https://github.com/) named `react-router-dom-lab`.

Clone a copy of your remote repo locally by using the `git clone` command:

```bash
git clone https://github.com/<your-username>/react-router-dom-lab.git
```

> 📚 Note: In the link above, where it says `<your-username>`, you should see the username from your GitHub account.

Next, `cd` into your new cloned directory, `react-router-dom-lab`:

```bash
cd react-router-dom-lab
```

Open the project's folder in your code editor:

```bash
code .
```

Run the following command to install `react-router-dom`:

```bash
npm i react-router-dom
```

Create a directory called `components` within `src`:

```bash
mkdir src/components
```

And finally, replace the contents of `src/App.jsx` with the following:

```jsx
// src/App.jsx
const App = () => {
  return (
    <>
    </>
  )
}

export default App
```
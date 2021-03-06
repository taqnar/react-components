# Hamburger Icon

Demo

![hamburger](./screenshots/hamburger.gif)

# How to use

Create these component in the project.

```txt
- Hamburger.js
- hamburger.module.scss
```

Call where you need it,

Say, we need in **Header Component**

```js
import { useState } from 'react'
import Hamburger from './Hamburger'

... // Other imports

export default function Header() {

      const [hamburger, setHamburger] = useState(false)

      ... // Other states

      return(
          <>
                ... // Other Components or something else

                // We need hamburger down here
                  <Hamburger hamburger={hamburger} setHamburger={setHamburger} />

                 ... // Other Components or something else

          </>

      )
}
```

#### Hamburger.js

```js
import styles from './hamburger.module.scss';

export default function Hamburger({ hamburger, setHamburger }) {
    return (
        <div
            className={
                hamburger
                    ? `${styles.hamburger} ${styles.open}`
                    : styles.hamburger
            }
            onClick={() => setHamburger((ham) => !ham)}
        >
            <span></span>
            <span></span>
            <span></span>
            <span></span>
            <span></span>
            <span></span>
        </div>
    );
}
```

#### hamburger.module.scss

```scss
.hamburger {
    width: 40px;
    height: 28px;
    position: relative;
    -webkit-transform: rotate(0deg);
    -moz-transform: rotate(0deg);
    -o-transform: rotate(0deg);
    transform: rotate(0deg);
    -webkit-transition: 0.5s ease-in-out;
    -moz-transition: 0.5s ease-in-out;
    -o-transition: 0.5s ease-in-out;
    transition: 0.5s ease-in-out;
    cursor: pointer;

    > span {
        display: block;
        position: absolute;
        height: 5px;
        width: 50%;
        background: #494d57;
        opacity: 1;
        -webkit-transform: rotate(0deg);
        -moz-transform: rotate(0deg);
        -o-transform: rotate(0deg);
        transform: rotate(0deg);
        -webkit-transition: 0.25s ease-in-out;
        -moz-transition: 0.25s ease-in-out;
        -o-transition: 0.25s ease-in-out;
        transition: 0.25s ease-in-out;

        &:nth-child(even) {
            left: 50%;
            border-radius: 0 9px 9px 0;
        }

        &:nth-child(odd) {
            left: 0px;
            border-radius: 9px 0 0 9px;
        }

        &:nth-child(1),
        &:nth-child(2) {
            top: 0px;
        }

        &:nth-child(3),
        &:nth-child(4) {
            top: 11px;
        }

        &:nth-child(5),
        &:nth-child(6) {
            top: 22px;
        }
    }
}
.open {
    > span {
        &:nth-child(1),
        &:nth-child(6) {
            -webkit-transform: rotate(45deg);
            -moz-transform: rotate(45deg);
            -o-transform: rotate(45deg);
            transform: rotate(45deg);
        }

        &:nth-child(2),
        &:nth-child(5) {
            -webkit-transform: rotate(-45deg);
            -moz-transform: rotate(-45deg);
            -o-transform: rotate(-45deg);
            transform: rotate(-45deg);
        }

        &:nth-child(1) {
            left: 3px;
            top: 4px;
        }
        &:nth-child(2) {
            left: calc(50% - 3px);
            top: 4px;
        }
        &:nth-child(3) {
            left: -50%;
            opacity: 0;
        }
        &:nth-child(4) {
            left: 100%;
            opacity: 0;
        }
        &:nth-child(5) {
            left: 3px;
            top: 18px;
        }
        &:nth-child(6) {
            left: calc(50% - 3px);
            top: 18px;
        }
    }
}
```

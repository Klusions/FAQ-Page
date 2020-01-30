<p align="center">
    <img width="350" height="350" src="https://timslab.de/timslab.png" alt="TimsLab Round">
    <br>
    <br>
    <br>
</p>

<p align="center">
    <a href="https://github.com/TimsLab">Github</a>&nbsp;&nbsp;&nbsp;
    <a href="https://twitter.com/TimsLabs">Twitter</a>&nbsp;&nbsp;&nbsp;
    <a href="https://discordapp.com/users/216297826081046528">Discord</a>&nbsp;&nbsp;&nbsp;
</p>

<br>

<br>

<p align="center">
  <sub>Built with ❤︎ by <a href="https://twitter.com/TimsLab">TimsLab</a></sub>
</p>
<br>

# TimsLab [![MIT license](https://img.shields.io/badge/License-MIT-blue.svg)](https://lbesson.mit-license.org/)


# 📜 Why do you need FAQ ?

Here you can answer frequently asked questions

# 💥 Demopage
https://timslab.com/github/FAQ-Page

## Example
```js
class TogglePanel extends HTMLElement {
    constructor() {
        super();
        
        this.state = {
            panel: 'collapsed'
        };
        
        this.attachShadow({mode: 'open'});
    }
    
    connectedCallback() {
		
        this.render();

        this.trigger = this.shadowRoot.querySelector('.trigger');
        this.button = this.trigger.querySelector('button');
        this.panel = this.shadowRoot.querySelector('.panel');

        this.bindEvents();
    }
    
    bindEvents() {
        this.trigger.addEventListener('click', evt => this.toggle(evt));
    }
    
    toggle() {
        const self = this;
        
        switch(this.state.panel) {
                
            case 'collapsed':
            default:
                
                this.button.setAttribute('aria-expanded', 'true');
                this.panel.classList.add('open');
                this.state.panel = 'open';
                break;
            case 'open':
                
                this.button.setAttribute('aria-expanded', 'false');
                this.panel.classList.remove('open');
                this.state.panel = 'closed';
                break;
        }
    }
    
    render() {
        const markup = `
            <style>
            .trigger {
                position: relative;
            }
            .panel {
                overflow: hidden;
                transition: all 200ms ease;
                max-height: 0px;
                padding: 0 2rem;
            }
            .panel.open {
                max-height: 35rem;
            }
            button {
                width: 100%;
                padding: 1rem 2rem;
                background: transparent;
                border: 1px solid #ccc;
                text-align: left;
                font-family: inherit;
                border-radius: 10px;
                cursor: pointer;
                color: currentColor;
                transition: all 200ms ease;
            }
            button:hover,
            button:focus {
                background: #0084ff;
                color: #f3f3f3;
                outline: none;
            }
            
            button:hover + svg,
            button:focus + svg {
                color: #f3f3f3;
            }
            svg {
                width: 1rem;
                height: 1rem;
                position: absolute;
                top: 50%;
                right: 2rem;
                margin-top: -0.5rem;
                fill: currentColor;
                transition: transform 200ms linear;
            }
            button[aria-expanded="true"] + svg {
                transform: rotate(180deg);
            }
            </style>
            <h2 class="trigger">
                <button aria-expanded="false">
                    <slot name="trigger"></slot>
                </button>
                <svg viewBox="0 0 512 512" aria-hidden="true">
                    <path d="M60 99.333l196 196 196-196 60 60-256 256-256-256z"></path>
                </svg>
            </h2>
            <div class="panel">
                <slot name="panel"></slot>
            </div> 
        `;
        
        this.shadowRoot.innerHTML = markup;
    }
}

if('customElements' in window) {
    customElements.define('toggle-panel', TogglePanel);
}
```

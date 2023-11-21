# Tab Component

A simple tab component for creating tabbed content with smooth transitions.

## Features

- Smooth tab transitions
- Easily customize content and styles

## Usage

1. **HTML Structure:**

   ```html
   <div class="tab-lists">
        <button class="tab-header" data-target="tab1">Tab 1</button>
        <button class="tab-header" data-target="tab2">Tab 2</button>
    </div>
    <div class="tab-items">
        <div id="tab1" class="tab-body open">Content 1</div>
        <div id="tab2" class="tab-body">Content 2</div>
    </div>
   
2. **CSS Styles:**

   Include the provided CSS styles in your stylesheet for proper tab styling.
    
   ```css
   .tab-body {
            display: none;
            opacity: 0;
            transform: translateY(5px);
            transition: all .3s;
        }

        .tab-body.open {
            display: flex;
            opacity: 1;
            transform: translateY(0);
        }

3. **JavaScript:**

   The JavaScript code handles the tab functionality with a fade effect. It utilizes event delegation for efficient handling of clicks.

   ```javascript
   // Function to toggle tab visibility
const fade = (element, open) => {
    element.style.display = "flex";

    element.offsetHeight;

    const removeStyle = () => element.removeAttribute('style');

    element.addEventListener('transitionend', removeStyle);

    element.classList.toggle('open', open);
};

// Handle click event on tab headers
const handleClick = (event) => {
    const trigger = event.target.closest(".tab-header");
    if (!trigger) return;

    const selectedTabId = trigger.getAttribute("data-target");
    const selectedTab = document.getElementById(selectedTabId);
    const activeTab = document.querySelector(".tab-body.open");

    if (!selectedTab || !activeTab || selectedTab === activeTab) {
        return;
    }

    // Hide the active tab.
    fade(activeTab, false);

    // Show the selected tab after transitionend of active tab
    activeTab.addEventListener('transitionend', () => {
        fade(selectedTab, true);
    }, { once: true });
};

// Event delegation
document.body.addEventListener("click", handleClick);
   
## Customization

**HTML Structure:**

- Create tab headers using `<button>` elements with the class `tab-header`.
- Set the `data-target` attribute to link a button to a specific tab.

**Styling:**

- Customize the appearance of tabs by adjusting the provided CSS styles.

**JavaScript Functionality:**

- Adjust the JavaScript code to fit your specific requirements.
- Feel free to enhance the functionality or add additional features.

Integrate, modify, and enhance this tab component according to your project's needs.

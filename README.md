# Caymland React Editor
## Installation

The easiest way to use React Email Editor is to install it from NPM and include it in your own React build process.

```
npm install caymland-react-editor --save
```
or

```
yarn add caymland-react-editor
```


## Usage

Require the EmailEditor component and render it with JSX:

```javascript
import React, { useRef } from 'react';
import { render } from 'react-dom';

import EmailEditor from 'caymland-react-editor';

const App = (props) => {
  const emailEditorRef = useRef(null);

  const exportHtml = () => {
    emailEditorRef.current.editor.exportHtml((data) => {
      const { design, html } = data;
      console.log('exportHtml', html);
    });
  };

  const onReady = () => {
    // editor is ready
    // you can load your template here;
    // const templateJson = {};
    // emailEditorRef.current.editor.loadDesign(templateJson);
  };

  return (
    <div>
      <div>
        <button onClick={exportHtml}>Export HTML</button>
      </div>

      <EmailEditor displayMode="email" ref={emailEditorRef} onReady={onReady} />
    </div>
  );
};

render(<App />, document.getElementById('app'));
```

### Methods

| method          | params              | description                                             |
|-----------------|---------------------|---------------------------------------------------------|
| **loadDesign**  | `Object data`       | Takes the design JSON and loads it in the editor        |
| **saveDesign**  | `Function callback` | Returns the design JSON in a callback function          |
| **exportHtml**  | `Function callback` | Returns the design HTML and JSON in a callback function |

See the [example source](https://github.com/unlayer/react-email-editor/blob/master/demo/index.tsx) for a reference implementation.

### Properties

- `editorId` `String` HTML div id of the container where the editor will be embedded (optional)
- `displayMode` `String` style object for the editor container (required 'email' | 'web' | 'popup')
- `style` `Object` style object for the editor container (default {})
- `minHeight` `String` minimum height to initialize the editor with (default 500px)
- `onLoad` `Function` called when the editor instance is created
- `onReady` `Function` called when the editor has finished loading
- `options` `Object` options passed to the Unlayer editor instance (default {})
- `tools` `Object` configuration for the built-in and custom tools (default {})
- `appearance` `Object` configuration for appearance and theme (default {})
- `projectId` `Integer` Unlayer project ID (optional)

See the [Unlayer Docs](https://docs.unlayer.com/) for all available options.

## Custom Tools

Custom tools can help you add your own content blocks to the editor. Every application is different and needs different tools to reach it's full potential. [Learn More](https://docs.unlayer.com/docs/custom-tools)

[![Custom Tools](https://unroll-assets.s3.amazonaws.com/custom_tools.png)](https://docs.unlayer.com/docs/custom-tools)

### License

Copyright (c) 2023 Unlayer. [MIT](LICENSE) Licensed.

# Vue2-Brace-Editor


A Vue components for Ace / Brace

## Install

`npm install vue2-brace-editor`

## Basic Usage

```javascript

<template>
  // Full editor component
  <AceEditor
    :fontSize="14"
    :showPrintMargin="true"
    :showGutter="true"
    :highlightActiveLine="true"
    mode="javascript"
    theme="monokai"
    :onChange="onChange"
    name="editor"
    :editorProps="{$blockScrolling: true}"
  />

  // Split editor component
   <SplitEditor
    mode="javascript"
    theme="monokai"
    :splits="2"
    orientation="beside"
    name="editor"
    :editorProps="{$blockScrolling: true}"
  />
</template>

<script>
  import Vue from 'vue';
  import brace from 'brace';
  import { Ace as AceEditor, Split as SplitEditor } from 'vue2-brace-editor';

  import 'brace/mode/javascript';
  import 'brace/theme/monokai';

  export default {
    components: {
      AceEditor,
      SplitEditor,
    },
    $el: 'root',
    methods: {
      onChange(newValue) {
        console.log('change',newValue);
      }
    }
  }
</script>

```

# Ace Editor - Full

This is the main component of Vue2-brace. It creates an instance of the Ace Editor.

## Available Props

|Prop|Default|Type|Description|
|-----|------|-----|-----|
|name| 'brace-editor'| String |Unique Id to be used for the editor|
|mode| ''| String |Language for parsing and code highlighting|
|theme| ''| String |theme to use|
|value | ''| String | value you want to populate in the code highlighter|
|defaultValue | ''| String |Default value of the editor|
|height| '500px'| String |CSS value for height|
|width| '500px'| String |CSS value for width|
|className| | String |custom className|
|fontSize| 12| Number |pixel value for font-size|
|showGutter| true| Boolean | show gutter |
|showPrintMargin| true| Boolean| show print margin |
|highlightActiveLine| true| Boolean| highlight active line|
|focus| false| Boolean| whether to focus
|cursorStart| 1| Number| the location of the cursor
|wrapEnabled| false| Boolean | Wrapping lines|
|readOnly| false| Boolean| make the editor read only |
|minLines| | Number |Minimum number of lines to be displayed|
|maxLines| | Number |Maximum number of lines to be displayed|
|enableBasicAutocompletion| false| Boolean | Enable basic autocompletion|
|enableLiveAutocompletion| false| Boolean | Enable live autocompletion|
|tabSize| 4|  Number| tabSize|
|debounceChangePeriod| null|  Number| A debounce delay period for the onChange event|
|onLoad| | Function | called on editor load. The first argument is the instance of the editor |
|onBeforeLoad| | Function | called before editor load. the first argument is an instance of `ace`|
|onChange| | Function |  occurs on document change it has 2 arguments the value and the event.|
|onCopy| | Function | triggered  by editor `copy` event, and passes text as argument|
|onPaste| | Function | Triggered by editor `paste` event, and passes text as argument|
|onSelectionChange| | Function | triggered by editor `selectionChange` event, and passes a [Selection](https://ace.c9.io/#nav=api&api=selection) as it's first argument and the event as the second|
|onCursorChange| | Function | triggered by editor `changeCursor` event, and passes a [Selection](https://ace.c9.io/#nav=api&api=selection) as it's first argument and the event as the second|
|onFocus| | Function | triggered by editor `focus` event|
|onBlur| | Function | triggered by editor `blur` event.It has two arguments event and editor|
|onInput| | Function | triggered by editor `input` event|
|onScroll| | Function | triggered by editor `scroll` event|
|onValidate| | Function | triggered, when annotations are changed|
|editorProps| | Object | properties to apply directly to the Ace editor instance|
|setOptions| | Object | [options](https://github.com/ajaxorg/ace/wiki/Configuring-Ace) to apply directly to the Ace editor instance|
|keyboardHandler| | String | corresponding to the keybinding mode to set (such as vim or emacs)|
|commands| | Array | new commands to add to the editor
|annotations| | Array | annotations to show in the editor i.e. `[{ row: 0, column: 2, type: 'error', text: 'Some error.'}]`, displayed in the gutter|
|markers| | Array | [markers](https://ace.c9.io/api/edit_session.html#EditSession.addMarker) to show in the editor, i.e. `[{ startRow: 0, startCol: 2, endRow: 1, endCol: 20, className: 'error-marker', type: 'background' }]`|
|style| | Object  | camelCased properties |

# Split Editor

This allows for a split editor which can create multiple linked instances of the Ace editor. Each instance shares a theme and other properties while having their own value.

## Available Props

|Prop|Default|Type|Description|
|-----|------|-----|-----|
|name| 'brace-editor'| String |Unique Id to be used for the editor|
|mode| ''| String |Language for parsing and code highlighting|
|splits| 2 | Number | Number of views to have |
|orientation| 'beside' | String | The orientation of the splits either `beside` or `below` |
|theme| ''| String |theme to use|
|value | ''| Array of Strings | value you want to populate in each code editor|
|defaultValue | ''| Array of Strings |Default value for each editor|
|height| '500px'| String |CSS value for height|
|width| '500px'| String |CSS value for width|
|className| | String |custom className|
|fontSize| 12| Number |pixel value for font-size|
|showGutter| true| Boolean | show gutter |
|showPrintMargin| true| Boolean| show print margin |
|highlightActiveLine| true| Boolean| highlight active line|
|focus| false| Boolean| whether to focus
|cursorStart| 1| Number| the location of the cursor
|wrapEnabled| false| Boolean | Wrapping lines|
|readOnly| false| Boolean| make the editor read only |
|minLines| | Number |Minimum number of lines to be displayed|
|maxLines| | Number |Maximum number of lines to be displayed|
|enableBasicAutocompletion| false| Boolean | Enable basic autocompletion|
|enableLiveAutocompletion| false| Boolean | Enable live autocompletion|
|tabSize| 4|  Number| tabSize|
|onLoad| | Function | called on editor load. The first argument is the instance of the editor |
|onBeforeLoad| | Function | called before editor load. the first argument is an instance of `ace`|
|onChange| | Function |  occurs on document change it has 2 arguments the value of each editor and the event.|
|onCopy| | Function | triggered  by editor `copy` event, and passes text as argument|
|onPaste| | Function | Triggered by editor `paste` event, and passes text as argument|
|onSelectionChange| | Function | triggered by editor `selectionChange` event, and passes a [Selection](https://ace.c9.io/#nav=api&api=selection) as it's first argument and the event as the second|
|onCursorChange| | Function | triggered by editor `changeCursor` event, and passes a [Selection](https://ace.c9.io/#nav=api&api=selection) as it's first argument and the event as the second|
|onFocus| | Function | triggered by editor `focus` event|
|onBlur| | Function | triggered by editor `blur` event|
|onInput| | Function | triggered by editor `input` event|
|onScroll| | Function | triggered by editor `scroll` event|
|editorProps| | Object | properties to apply directly to the Ace editor instance|
|setOptions| | Object | [options](https://github.com/ajaxorg/ace/wiki/Configuring-Ace) to apply directly to the Ace editor instance|
|keyboardHandler| | String | corresponding to the keybinding mode to set (such as vim or emacs)|
|commands| | Array | new commands to add to the editor
|annotations| | Array of Arrays | annotations to show in the editor i.e. `[{ row: 0, column: 2, type: 'error', text: 'Some error.'}]`, displayed in the gutter|
|markers| | Array of Arrays | [markers](https://ace.c9.io/api/edit_session.html#EditSession.addMarker) to show in the editor, i.e. `[{ startRow: 0, startCol: 2, endRow: 1, endCol: 20, className: 'error-marker', type: 'background' }]`|
|style| | Object  | camelCased properties |
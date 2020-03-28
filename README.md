# ckeditor-angular-plugins

Clone the original repo:
git clone https://github.com/ckeditor/ckeditor5-build-classic.git

Install dependencies
```bash
npm install
```
Install necessary plugin itself
```bash
npm install --save @wiris/mathtype-ckeditor5
```
Open src/ckeditor.js and new plugin to the editor:
```javascript
...
import MathType from '@wiris/mathtype-ckeditor5';
...

ClassicEditor.builtinPlugins = [
   ...
   MathType
];

ClassicEditor.defaultConfig = {
    toolbar: {
        items: [
            ...
            'MathType',
            ...
        ]
    },
    ...
};

```
Then build the editor (you maybe need to install yarn)
yarn run build

After that copy everything from build folder to your project. For instance
```bash
src/assets/js/ck-editor-math-type/
   -> translations
      -> ...
   -> ckeditor.js
```
Add ckeditor code to package.json
```javascript
"dependencies": {
   ...
   "@ckeditor/ckeditor5-angular": "^1.1.2",
   ...
}


Import CKEditor to your component:
import * as ClassicEditor from '../../assets/js/ck-editor-math-type/ckeditor.js';

...
export class CkeditComponent implements OnInit {

    public Editor = ClassicEditor;

    public model = {
        editorData: '<p>Hello, world!</p>'
    };
}

```
Add it too your template.html
<ckeditor [(ngModel)]="model.editorData" [editor]="Editor"></ckeditor>
Hope this help you.

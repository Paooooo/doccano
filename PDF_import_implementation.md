# PDF import for text classification projects
The aim of this document is to explain how is implemented the PDF import feature for text classification projects.
This feature allows users to import pdf files for their text classfication projects and to visualize it in a preview panel in order to label it.

## Upload (backend)

When a user tries to upload some textual data on doccano, an instance of the `TextUploadAPI` class is called. The role of this class is to check the document format, parse it and save it. 
This is done with the `post()` function that takes a `resquest` as parameter. Inside of the `post()` method, the `save_file()` method is called. 
It returns the appropriate parser according to the input file format. In case of a pdf file, the `PDFParser()` class is called. 
The parsing function of this class returns the pdf file name as the text data and the upload location as a meta attribute.

#### Example of PDF data parsed
```json
"text" : "sample.pdf",
"meta" : {"file_path" : "frontend/static/pdf/sample.pdf"}
```

The pdf file is stored is a dedicated folder : `doccano/frontend/static/pdf/`.

## Viewer Panel (frontend)

Once the pdf file is uploaded on doccano, the user can acces a viewer panel for his pdf file when annotating documents. 
This is done by adding a Vue.js component `ViewerPane.vue` which is displayed if the document is a pdf file.


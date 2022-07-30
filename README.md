# Analysing Malicous PDFs 📁

PDFs are sometimes tricky to analyse. Malware Author can use this for Phishing, Implement Droppers & Downloaders.

Like in this Sample (MD5: eecde7b70136e606adcd3e56452aca2a)

It has almost no detectiopn in VT, Got undetected by many AVs.
<img width="660" alt="Capture" src="https://user-images.githubusercontent.com/107531426/181920551-61279933-d703-4a38-b058-344001baebca.PNG">

As well as in Sandboxes

<img width="654" alt="Capture" src="https://user-images.githubusercontent.com/107531426/181920753-36b6a58a-973f-4712-a20d-e09fb6ebb818.PNG">

But this sample is malicious, that we'll see later. First we'll learn about some basics of PDFs.

# PDF File Format 💌

1. PDF header: Contains info about the version of the PDF such as %PDF-1.6

2. Body:

Streams: a sequence of bytes such as images or data, which comes in encoded data.

Objects: How to render documanets which can include text or javascript.

Others such as names, dictionaries, strings, and arrays.

Dictionary entry is an item between « » and starts with slash / such as /Root which is the first object will be processed after loading the PDF file, /Root could be found in the Trailer section.

3. Cross-reference table: contains the offsets of file’s objects.

4. Trailer: contains the offset of xref table, and number of objects, /Root.

👉 Some usefull keywords after parsing:

/Js, /JavaScript: To execute embedded javascript

/Launch, /EmbeddedFiles: To launch exeternal or embedded files

/URI: To interact with URLs

/OpenAction, /AA: To open an action

/FlateDecode: uses the zlib/deflate decompression method.

A comment in PDF starts with %

(Learn more: https://resources.infosecinstitute.com/topic/pdf-file-format-basic-structure/)

And Use pdfid.py, peepdf.py and pdf-parser.py to extract strings, URLs, Embedded Files, Flate decode and content of objects of PDFs


<img width="460" alt="Capture" src="https://user-images.githubusercontent.com/107531426/181880046-1436296e-1070-4409-a32b-c481a3ef6e05.PNG">
<img width="660" alt="Capture" src="https://user-images.githubusercontent.com/107531426/181880051-2e92c585-cfb7-43b6-b572-8800a73b6476.PNG">
<img width="660" alt="Capture" src="https://user-images.githubusercontent.com/107531426/181880055-baf66f4e-3224-4cdf-a044-832f2a423d3d.PNG">

After parsing we can see the PDF has a URL which is malicious
<img width="739" alt="nrl4" src="https://user-images.githubusercontent.com/107531426/181880057-8fd92e48-a637-4c0c-b542-0e2a9029523b.PNG">

And when you open the malicious PDF, it will redirect you to above malicious URL and here we can see the malicious network activity too. 
<img width="469" alt="Captureg" src="https://user-images.githubusercontent.com/107531426/181925758-b743128f-13ca-4149-a6e6-74993e99b9bb.PNG">
<img width="610" alt="Capture1" src="https://user-images.githubusercontent.com/107531426/181925239-10ec90dd-8893-443a-973f-b735325f9713.PNG">






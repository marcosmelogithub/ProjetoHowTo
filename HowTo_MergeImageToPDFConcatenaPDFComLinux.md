
# Como converter e concatenar vários arquivos em um único arquivo PDF usando linha de comando do Linux Quick Guide

---


1. ##### Instalar as ferramentas "img2pdf" e "poppler-utils"
    ```sudo apt update```
    ```sudo apt install img2pdf poppler-utils```

----
2. ##### Converter as imagens para PDF
    ```img2pdf *.jpeg --output imagens.pdf```

----

3. ##### Concatenar arquivos PDF's
    ```pdfunite arqpdf1.pdf arqpdf2.pdf.pdf ... [nome-arquivo-saida].pdf```
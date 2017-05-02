---
title: "ubound-Methode (VBArray) (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "ubound"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "ubound-Methode"
ms.assetid: 761811c5-9a3d-4cb3-bfe0-0a8749f34496
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# ubound-Methode (VBArray) (JavaScript)
Gibt den höchsten Indexwert zurück, der in der angegebenen Dimension im VBArray verwendet wird  
  
## Syntax  
  
```  
  
safeArray.ubound(dimension)  
```  
  
## Parameter  
 *safeArray*  
 Erforderlich. Ein VBArray\-Objekt.  
  
 `dimension`  
 Optional. Die Dimension des VBArray, für die der obere Indexwert bestimmt werden soll. Wenn nicht angegeben, verhält sich `ubound` wie bei der Übergabe von 1.  
  
## Hinweise  
 Ist das VBArray leer, gibt die `ubound`\-Methode „nicht definiert“ zurück. Wenn `dim` größer als die Anzahl der Dimensionen im VBArray oder negativ ist, generiert die Methode einen Fehler „Index außerhalb des definierten Bereichs“.  
  
## Beispiel  
 Das folgende Beispiel besteht aus drei Teilen. Der erste Teil ist VBScript\-Code zum Erstellen eines sicheren Visual Basic\-Arrays. Der zweite Teil ist [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]\-Code, der die Anzahl der Dimensionen im sicheren Array und die obere Grenze jeder Dimension bestimmt. Beide Teile gehören in den \<HEAD\>\-Abschnitt einer HTML\-Seite. Der dritte Teil ist der [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]\-Code, der in den \<BODY\>\-Abschnitt eingeführt wird, um die anderen beiden Teile auszuführen.  
  
```javascript  
<head>  
<script type="text/vbscript">  
<!--  
Function CreateVBArray()  
   Dim i, j, k  
   Dim a(2, 2)  
   k = 1  
   For i = 0 To 2  
      For j = 0 To 2  
         a(j, i) = k  
         k = k + 1  
      Next  
   Next  
   CreateVBArray = a  
End Function  
-->  
</script>  
  
<script type="text/javascript">  
<!--  
function VBArrayTest(vba)  
{  
   var i;  
   var a = new VBArray(vba);  
   var s = "";  
   for (i = 1; i <= a.dimensions(); i++)  
   {  
      s += "The upper bound of dimension ";  
      s += i + " is ";  
      s += a.ubound(i);  
      s += ".<br />";  
   }  
   return (s);  
}  
-->  
</script>  
</head>  
  
<body>  
<script type="text/javascript">  
   document.write(VBArrayTest(CreateVBArray()));  
</script>  
</body>  
```  
  
## Anforderungen  
 Wird in den folgenden Dokumentmodi unterstützt: Quirksmodus, Internet Explorer 6\-Standardmodus, Internet Explorer 7\-Standardmodus, Internet Explorer 8\-Standardmodus, Internet Explorer 9\-Standardmodus und Internet Explorer 10\-Standardmodus. Wird in [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]\-Apps nicht unterstützt. Siehe [Versionsinformationen](../../javascript/reference/javascript-version-information.md).  
  
 **Gilt für**: [VBArray\-Objekt](../../javascript/reference/vbarray-object-javascript.md)  
  
## Siehe auch  
 [dimensions\-Methode \(VBArray\)](../../javascript/reference/dimensions-method-vbarray-javascript.md)   
 [getItem\-Methode \(VBArray\)](../../javascript/reference/getitem-method-vbarray-javascript.md)   
 [lbound\-Methode \(VBArray\)](../../javascript/reference/lbound-method-vbarray-javascript.md)   
 [toArray\-Methode \(VBArray\)](../../javascript/reference/toarray-method-vbarray-javascript.md)
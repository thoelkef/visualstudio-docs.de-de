---
title: "lbound-Methode (VBArray) (JavaScript) | Microsoft Docs"
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
  - "lbound"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "lbound-Methode"
ms.assetid: 30ff5e8a-8165-494b-bce8-0a562ec2eec3
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# lbound-Methode (VBArray) (JavaScript)
Gibt den niedrigsten Indexwert zurück, der in der angegebenen Dimension eines VBArrays verwendet wird.  
  
## Syntax  
  
```  
  
safeArray.lbound(dimension)   
```  
  
## Parameter  
 *safeArray*  
 Erforderlich.  Ein VBArray\-Objekt.  
  
 `dimension`  
 Dies ist optional.  Die Dimension des VBArrays, deren kleinster Indexwert bestimmt werden soll.  Erfolgt keine Dimensionsangabe, verhält sich `lbound` wie bei der Übergabe von 1.  
  
## Hinweise  
 Ist das VBArray leer, gibt die `lbound`\-Methode "undefined" zurück.  Ist `dimension` größer als die Anzahl der Dimensionen im VBArray oder negativ, generiert die Methode den Fehler "Index außerhalb des definierten Bereichs".  
  
## Beispiel  
 Das folgende Beispiel besteht aus drei Teilen.  Der erste Teil ist VBScript\-Code zum Erstellen eines Visual Basic\-SafeArrays.  Der zweite Teil besteht aus [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]\-Code, der die Anzahl der Dimensionen des SafeArrays und die untere Grenze der einzelnen Dimensionen bestimmt.  Da das SafeArray in VBScript und nicht in Visual Basic erstellt wird, ist die untere Grenze immer gleich Null.  Beide Teile gehören in den \<HEAD\>\-Abschnitt einer HTML\-Seite.  Der dritte Teil ist [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]\-Code, der vom \<BODY\>\-Abschnitt aus die Ausführung der beiden anderen Teile bewirkt.  
  
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
function VBArrayTest(vba){  
   var i;  
   var a = new VBArray(vba);  
   var s = "";  
   for (i = 1; i <= a.dimensions(); i++)  
   {  
      s += "The lower bound of dimension ";  
      s += i + " is ";  
      s += a.lbound(i);  
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
 Wird in den folgenden Dokumentmodi unterstützt: Quirksmodus, Internet Explorer 6 \(Standardmodus\), Internet Explorer 7 \(Standardmodus\), Internet Explorer 8 \(Standardmodus\), Internet Explorer 9 \(Standardmodus\) und Internet Explorer 10 \(Standardmodus\).  Wird in [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]\-Apps nicht unterstützt.  Weitere Informationen finden Sie unter [Versionsinformationen](../../javascript/reference/javascript-version-information.md).  
  
 **Gilt für**: [VBArray\-Objekt](../../javascript/reference/vbarray-object-javascript.md)  
  
## Siehe auch  
 [dimensions\-Methode \(VBArray\)](../../javascript/reference/dimensions-method-vbarray-javascript.md)   
 [getItem\-Methode \(VBArray\)](../../javascript/reference/getitem-method-vbarray-javascript.md)   
 [toArray\-Methode \(VBArray\)](../../javascript/reference/toarray-method-vbarray-javascript.md)   
 [ubound\-Methode \(VBArray\)](../../javascript/reference/ubound-method-vbarray-javascript.md)
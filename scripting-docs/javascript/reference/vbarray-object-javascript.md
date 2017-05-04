---
title: "VBArray-Objekt (JavaScript) | Microsoft Docs"
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
  - "VBArray"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "VBArray-Objektkonstante"
ms.assetid: f0b767f1-ea8a-4726-962b-2708d4742518
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# VBArray-Objekt (JavaScript)
Bietet Zugriff auf sichere Visual Basic\-Arrays.  
  
> [!WARNING]
>  Dieses Objekt wird nur in Internet Explorer unterstützt, nicht in [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]\-Apps.  
  
## Syntax  
  
```  
  
varName = new VBArray(safeArray)  
```  
  
## Parameter  
 `varName`  
 Erforderlich. Der Variablenname, dem das VBArray zugewiesen wird.  
  
 *safeArray*  
 Erforderlich. Ein VBArray\-Wert.  
  
## Hinweise  
 VBArrays sind schreibgeschützt und können nicht direkt erstellt werden. Das *safeArray*\-Argument muss einen VBArray\-Wert abgerufen haben, bevor es an den VBArray\-Konstruktor übergeben wird. Dies kann nur durch Abrufen des Werts aus einem vorhandenen ActiveX oder einem anderen Objekt erfolgen.  
  
 VBArrays können über mehrere Dimensionen verfügen. Die Indizes der einzelnen Dimensionen können unterschiedlich sein. Die **dimensions**\-Methode ruft die Anzahl der Dimensionen im Array ab; die `lbound`\- und `ubound`\-Methoden rufen den von jeder Dimension verwendeten Indexbereich ab.  
  
## Beispiel  
 Das folgende Beispiel besteht aus drei Teilen. Der erste Teil ist VBScript\-Code zum Erstellen eines sicheren Visual Basic\-Arrays. Der zweite Teil ist [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]\-Code, der das sichere Visual Basic\-Array in ein [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]\-Array konvertiert. Beide Teile gehören in den \<HEAD\>\-Abschnitt einer HTML\-Seite. Der dritte Teil ist der [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]\-Code, der in den \<BODY\>\-Abschnitt eingeführt wird, um die anderen beiden Teile auszuführen.  
  
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
         document.writeln(k)  
         k = k + 1  
      Next  
      document.writeln("<br />")  
   Next  
   CreateVBArray = a  
End Function  
-->  
</script>  
  
<script type="text/javascript">  
<!--  
function VBArrayTest(vbarray){  
   var a = new VBArray(vbarray);  
   var b = a.toArray();  
   var i;  
   for (i = 0; i < 9; i++)   
   {  
      document.writeln(b[i]);  
   }  
}  
-->  
</script>  
</head>  
  
<body>  
<script type="text/javascript">  
<!--  
   VBArrayTest(CreateVBArray());  
-->  
</script>  
</body>  
```  
  
## Eigenschaften  
 Das `VBArray`\-Objekt hat keine Eigenschaften.  
  
## Methoden  
 [dimensions\-Methode](../../javascript/reference/dimensions-method-vbarray-javascript.md) &#124; [getItem\-Methode](../../javascript/reference/getitem-method-vbarray-javascript.md) &#124; [lbound\-Methode](../../javascript/reference/lbound-method-vbarray-javascript.md) &#124; [toArray\-Methode](../../javascript/reference/toarray-method-vbarray-javascript.md) &#124; [ubound\-Methode](../../javascript/reference/ubound-method-vbarray-javascript.md)  
  
## Anforderungen  
 Wird in den folgenden Dokumentmodi unterstützt: Quirksmodus, Internet Explorer 6\-Standardmodus, Internet Explorer 7\-Standardmodus, Internet Explorer 8\-Standardmodus, Internet Explorer 9\-Standardmodus und Internet Explorer 10\-Standardmodus. Wird in [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]\-Apps nicht unterstützt. Siehe [Versionsinformationen](../../javascript/reference/javascript-version-information.md).  
  
## Siehe auch  
 [Array\-Objekt](../../javascript/reference/array-object-javascript.md)
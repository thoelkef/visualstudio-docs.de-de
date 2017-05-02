---
title: "Typisierte Arrays (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: fa82c562-0ebf-4559-aecc-166e59f7fb64
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# Typisierte Arrays (JavaScript)
Mit typisierten Arrays können Sie Binärdaten aus Quellen wie Netzwerkprotokollen, Binärdateiformaten und Rohdaten\-Grafikpuffern bearbeiten.  Sie können typisierte Arrays auch verwenden, um speicherinterne Binärdaten mit bekannten Bytelayouts zu verwalten.  
  
## Beispiel  
 Im folgenden Code wird gezeigt, wie ein [ArrayBuffer\-Objekt](../../javascript/reference/arraybuffer-object.md) als Antwort einer [XMLHttpRequest](http://msdn.microsoft.com/library/ie/ms535874\(v=vs.85\).aspx) verwendet wird.  Sie können die Bytes in der Antwort bearbeiten, indem Sie die verschiedenen Methoden des [DataView\-Objekt](../../javascript/reference/dataview-object.md) verwenden oder die Bytes in das entsprechende typisierte Array kopieren.  
  
> [!TIP]
>  Weitere Informationen zur Verwendung verschiedener Antworttypen mit einer `XmlHttpRequest` finden Sie unter [XMLHttpRequest.responseType](http://msdn.microsoft.com/de-de/8d7738d1-4bfd-4cf1-8015-174def089556), [XMLHttpRequest\-Erweiterungen](http://msdn.microsoft.com/de-de/be09137c-6546-441b-b953-dcbf72b77069) und [Herunterladen verschiedener Typen von Inhalten \(Windows Store\-Apps\)](http://msdn.microsoft.com/de-de/c0006bbd-17f9-4c6a-af81-2acaf109111d).  
  
```javascript  
...  
<div id="xhrDiv"></div>  
...  
var name = "http://www.microsoft.com";  
var xhrDiv = document.getElementById("xhrDiv");  
  
var req = new XMLHttpRequest();  
req.open("GET", name, true);  
req.responseType = "arraybuffer";  
req.onreadystatechange = function () {  
if (req.readyState == req.DONE) {  
    var arrayResponse = req.response;  
    var dataView = new DataView(arrayResponse);  
    var ints = new Uint32Array(dataView.byteLength / 4);  
  
    xhrDiv.style.backgroundColor = "#00FF00";  
    xhrDiv.innerText = "Array is " + ints.length + "uints long";  
    }  
}  
req.send();  
```  
  
## ArrayBuffer  
 Ein [ArrayBuffer\-Objekt](../../javascript/reference/arraybuffer-object.md) stellt einen Puffer mit Rohdaten dar, der verwendet wird, um Daten für die verschiedenen typisierten Arrays zu speichern.  Das `ArrayBuffer`\-Objekt ist lese\- und schreibgeschützt, aber Sie können es an ein typisiertes Array oder ein [DataView\-Objekt](../../javascript/reference/dataview-object.md)\-Objekt übergeben, um den Rohdatenpuffer zu interpretieren.  In einem `ArrayBuffer`\-Objekt können Sie beliebige Daten \(oder unterschiedliche Typen von Daten\) speichern.  
  
## DataView  
 Sie können ein [DataView\-Objekt](../../javascript/reference/dataview-object.md) verwenden, um die verschiedenen Arten von Binärdaten an einem beliebigen Speicherort im `ArrayBuffer` zu lesen und zu schreiben.  
  
## Typisierte Arrays  
 Die typisierten Arraytypen stellen Ansichten eines [ArrayBuffer\-Objekt](../../javascript/reference/arraybuffer-object.md) dar, das indiziert und bearbeitet werden kann.  Alle Arraytypen weisen eine feste Länge auf.  
  
||||  
|-|-|-|  
|Name|Größe \(in Bytes\)|Beschreibung|  
|[Int8Array\-Objekt](../../javascript/reference/int8array-object.md)|1|8\-Bit\-Zweierkomplement\-Ganzzahl mit Vorzeichen|  
|[Uint8Array\-Objekt](../../javascript/reference/uint8array-object.md)|1|8\-Bit\-Ganzzahl ohne Vorzeichen|  
|[Int16Array\-Objekt](../../javascript/reference/int16array-object.md)|2|16\-Bit\-Zweierkomplement\-Ganzzahl mit Vorzeichen|  
|[Uint16Array\-Objekt](../../javascript/reference/uint16array-object.md)|2|16\-Bit\-Ganzzahl ohne Vorzeichen|  
|[Int32Array\-Objekt](../../javascript/reference/int32array-object.md)|4|32\-Bit\-Zweierkomplement\-Ganzzahl mit Vorzeichen|  
|[Uint32Array\-Objekt](../../javascript/reference/uint32array-object.md)|4|32\-Bit\-Ganzzahl ohne Vorzeichen|  
|[Float32Array\-Objekt](../../javascript/reference/float32array-object.md)|4|32\-Bit\-IEEE\-Gleitkomma|  
|[Float64Array\-Objekt](../../javascript/reference/float64array-object.md)|8|64\-Bit\-IEEE\-Gleitkomma|
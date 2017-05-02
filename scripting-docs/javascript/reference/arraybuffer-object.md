---
title: "ArrayBuffer-Objekt | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 9fda1261-f450-493b-b3db-ecfa9ca93cd7
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# ArrayBuffer-Objekt
Stellt einen unformatierten Puffer von Binärdaten dar, der zum Speichern von Daten für die verschiedenen typisierten Arrays verwendet wird.  `ArrayBuffers` können nicht direkt gelesen oder geschrieben werden, können jedoch an ein typisiertes Array oder eine [DataView\-Objekt](../../javascript/reference/dataview-object.md) übergeben werden, um den unformatierten Puffer bei Bedarf zu interpretieren.  
  
 Weitere Informationen zu typisierten Arrays finden Sie unter [Typisierte Arrays](../../javascript/advanced/typed-arrays-javascript.md).  
  
## Syntax  
  
```javascript  
  
arrayBuffer = new ArrayBuffer(length);  
```  
  
## Parameter  
 `arrayBuffer`  
 Erforderlich.  Der Variablenname, dem das `ArrayBuffer`\-Objekt zugewiesen wird.  
  
 `length`  
 Die Länge des Puffers.  Der Inhalt des ArrayBuffer\-Objekts wird mit 0 initialisiert.  Wenn die angeforderte Anzahl von Bytes nicht zugeordnet werden kann, wird eine Ausnahme ausgelöst.  
  
## Eigenschaften  
 In der folgenden Tabelle werden die Eigenschaften des `ArrayBuffer`\-Objekts aufgelistet.  
  
|Eigenschaft|Beschreibung|  
|-----------------|------------------|  
|[byteLength\-Eigenschaft](../../javascript/reference/bytelength-property-arraybuffer.md)|Schreibgeschützt.  Die Länge des ArrayBuffer\-Objekts in Bytes.|  
  
## Funktionen  
 In der folgenden Tabelle werden die Funktionen des `ArrayBuffer`\-Objekts aufgelistet.  
  
|Eigenschaft|Beschreibung|  
|-----------------|------------------|  
|[ArrayBuffer.isView\-Function](../../javascript/reference/arraybuffer-isview-function-arraybuffer.md)|Bestimmt, ob ob ein Objekt eine Ansicht des Puffers bereitstellt.|  
  
## Methoden  
 In der folgenden Tabelle werden die Methoden des `ArrayBuffer`\-Objekts aufgelistet.  
  
|Eigenschaft|Beschreibung|  
|-----------------|------------------|  
|[slice\-Methode](../../javascript/reference/slice-method-arraybuffer.md)|Gibt einen Abschnitt eines `ArrayBuffer` zurück.|  
  
## Beispiel  
 Im folgenden Beispiel wird gezeigt, wie ein ArrayBuffer\-Objekt verwendet wird, um die von einer [XMLHttpRequest](http://msdn.microsoft.com/library/ie/ms535874\(v=vs.85\).aspx) abgerufenen Binärdaten zu verarbeiten.  Sie können [DataView\-Objekt](../../javascript/reference/dataview-object.md) verwenden, um die einzelnen Werte abzurufen.  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataview = new DataView(buffer);  
            var ints = new Int32Array(buffer.byteLength / 4);  
            for (var i = 0; i < ints.length; i++) {  
                ints[i] = dataview.getInt32(i * 4);  
            }  
        alert(ints[10]);  
        }  
    }  
  
```  
  
## Hinweise  
 Weitere Informationen zur Verwendung von `XmlHttpRequest` finden Sie unter [XMLHttpRequest enhancements](http://msdn.microsoft.com/de-de/be09137c-6546-441b-b953-dcbf72b77069).  
  
## Anforderungen  
 [!INCLUDE[jsv10](../../includes/jsv10-md.md)]
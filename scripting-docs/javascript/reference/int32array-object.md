---
title: "Int32Array-Objekt | Microsoft Docs"
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
ms.assetid: 48696299-e41e-4590-b1b5-26fe19f68139
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# Int32Array-Objekt
Ein typisiertes Array von ganzzahligen 32\-Bit\-Werten.  Der Inhalt wird mit 0 initialisiert.  Wenn die angeforderte Anzahl von Bytes nicht zugeordnet werden kann, wird eine Ausnahme ausgelöst.  
  
## Syntax  
  
```  
  
      int32Array = new Int32Array( length );  
int32Array = new Int32Array( array );  
int32Array = new Int32Array( buffer, byteOffset, length);  
```  
  
## Parameter  
 `int32Array`  
 Erforderlich.  Der Variablenname, dem das **Int32Array**\-Objekt zugewiesen ist.  
  
 `length`  
 Gibt die Anzahl der Elemente im Array an.  
  
 `array`  
 Das Array \(oder typisierte Array\), das in diesem Array enthalten ist.  Der Inhalt wird mit dem Inhalt des angegebenen Arrays oder des typisierten Arrays initialisiert, wobei jedes Element in den Int32\-Typ konvertiert wird.  
  
 `buffer`  
 Das ArrayBuffer\-Objekt, das das Int32Array darstellt.  
  
 `byteOffset`  
 Optional.  Gibt den Offset in Bytes vom Beginn des Puffers an, bei dem das Int32Array beginnen soll.  
  
 `length`  
 Die Anzahl der Elemente im Array.  
  
## Konstanten  
 In der folgenden Tabelle werden die Konstanten des `Int32Array`\-Objekts aufgelistet.  
  
|Konstante|Beschreibung|  
|---------------|------------------|  
|[BYTES\_PER\_ELEMENT\-Konstante](../../javascript/reference/bytes-per-element-constant-int32array.md)|Die Größe jedes Elements im Array in Bytes.|  
  
## Eigenschaften  
 In der folgenden Tabelle werden die Konstanten des `Int32Array`\-Objekts aufgelistet.  
  
|Eigenschaft|Beschreibung|  
|-----------------|------------------|  
|[Puffereigenschaft](../../javascript/reference/buffer-property-int32array.md)|Schreibgeschützt.  Ruft den ArrayBuffer ab, auf den durch dieses Array verwiesen wird.|  
|[byteLength\-Eigenschaft](../../javascript/reference/bytelength-property-int32array.md)|Schreibgeschützt.  Die Länge dieses Arrays vom Beginn des ArrayBuffers in Bytes, so wie während der Konstruktionszeit festgelegt.|  
|[byteOffset\-Eigenschaft](../../javascript/reference/byteoffset-property-int32array.md)|Schreibgeschützt.  Der Offset dieses Arrays vom Beginn des ArrayBuffers in Bytes, so wie während der Konstruktionszeit festgelegt.|  
|[Längeneigenschaft](../../javascript/reference/length-property-int32array.md)|Die Länge des Arrays.|  
  
## Methoden  
 In der folgenden Tabelle werden die Methoden des `Int32Array`\-Objekts aufgelistet.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[Set\-Methode \(Int32Array\)](../../javascript/reference/set-method-int32array.md)|Legt einen Wert oder ein Wertearray fest.|  
|[subarray\-Methode \(Int32Array\)](../../javascript/reference/subarray-method-int32array.md)|Ruft eine neue Int32Array\-Ansicht des ArrayBuffer\-Speichers für dieses Array ab.|  
  
## Beispiel  
 Im folgenden Beispiel wird gezeigt, wie ein Int32Array\-Objekt verwendet wird, um die von XmlHttpRequest abgerufenen Binärdaten zu verarbeiten.  
  
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
  
## Anforderungen  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]
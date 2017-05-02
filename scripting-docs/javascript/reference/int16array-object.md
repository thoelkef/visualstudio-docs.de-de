---
title: "Int16Array-Objekt | Microsoft Docs"
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
ms.assetid: b87f36b4-4e38-4f32-b258-654c4ad2c615
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# Int16Array-Objekt
Ein typisiertes Array von ganzzahligen 16\-Bit\-Werten.  Der Inhalt wird mit 0 initialisiert.  Wenn die angeforderte Anzahl von Bytes nicht zugeordnet werden kann, wird eine Ausnahme ausgelöst.  
  
## Syntax  
  
```  
  
      int16Array = new Int16Array( length );  
int16Array = new Int16Array( array );  
int16Array = new Int16Array( buffer, byteOffset, length);  
```  
  
## Parameter  
 `int16Array`  
 Erforderlich.  Der Variablenname, dem das **Int16Array**\-Objekt zugewiesen ist.  
  
 `length`  
 Gibt die Anzahl der Elemente im Array an.  
  
 `array`  
 Das Array \(oder typisierte Array\), das in diesem Array enthalten ist.  Der Inhalt wird mit dem Inhalt des angegebenen Arrays oder des typisierten Arrays initialisiert, wobei jedes Element in den Int16\-Typ konvertiert wird.  
  
 `buffer`  
 Das ArrayBuffer\-Objekt, das das Int16Array darstellt.  
  
 `byteOffset`  
 Optional.  Gibt den Offset in Bytes vom Beginn des Puffers an, bei dem das Int16Array beginnen soll.  
  
 `length`  
 Die Anzahl der Elemente im Array.  
  
## Konstanten  
 In der folgenden Tabelle werden die Konstanten des `Int16Array`\-Objekts aufgelistet.  
  
|Konstante|Beschreibung|  
|---------------|------------------|  
|[BYTES\_PER\_ELEMENT\-Konstante](../../javascript/reference/bytes-per-element-constant-int16array.md)|Die Größe jedes Elements im Array in Bytes.|  
  
## Eigenschaften  
 In der folgenden Tabelle werden die Konstanten des `Int16Array`\-Objekts aufgelistet.  
  
|Eigenschaft|Beschreibung|  
|-----------------|------------------|  
|[Puffereigenschaft](../../javascript/reference/buffer-property-int16array.md)|Schreibgeschützt.  Ruft den ArrayBuffer ab, auf den durch dieses Array verwiesen wird.|  
|[byteLength\-Eigenschaft](../../javascript/reference/byteoffset-property-int16array.md)|Schreibgeschützt.  Die Länge dieses Arrays vom Beginn des ArrayBuffers in Bytes, so wie während der Konstruktionszeit festgelegt.|  
|[byteOffset\-Eigenschaft](../../javascript/reference/byteoffset-property-int16array.md)|Schreibgeschützt.  Der Offset dieses Arrays vom Beginn des ArrayBuffers in Bytes, so wie während der Konstruktionszeit festgelegt.|  
|[Längeneigenschaft](../../javascript/reference/length-property-int16array.md)|Die Länge des Arrays.|  
  
## Methoden  
 In der folgenden Tabelle werden die Methoden des `Int16Array`\-Objekts aufgelistet.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[Set\-Methode \(Int16Array\)](../../javascript/reference/set-method-int16array.md)|Legt einen Wert oder ein Wertearray fest.|  
|[subarray\-Methode \(Int16Array\)](../../javascript/reference/subarray-method-int16array.md)|Ruft eine neue Int16Array\-Ansicht des ArrayBuffer\-Speichers für dieses Array ab.|  
  
## Beispiel  
 Im folgenden Beispiel wird gezeigt, wie ein Int16Array\-Objekt verwendet wird, um die von XmlHttpRequest abgerufenen Binärdaten zu verarbeiten.  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataview = new DataView(buffer);  
            var ints = new Int16Array(buffer.byteLength / 2);  
            for (var i = 0; i < ints.length; i++) {  
                ints[i] = dataview.getInt16(i * 2);  
            }  
        alert(ints[10]);  
        }  
    }  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv10](../../includes/jsv10-md.md)]
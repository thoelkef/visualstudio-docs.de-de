---
title: "Uint8ClampedArray-Objekt (JavaScript) | Microsoft Docs"
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
ms.assetid: 0c5537f7-00b4-487a-8fba-ef032e67e7bd
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Uint8ClampedArray-Objekt (JavaScript)
Ein typisiertes Array von 8\-Bit\-Ganzzahlen ohne Vorzeichen, wobei die Werte an den Bereich von 0 bis 255 gebunden sind.  Der Inhalt wird mit 0 initialisiert.  Wenn die angeforderte Anzahl von Bytes nicht zugeordnet werden kann, wird eine Ausnahme ausgelöst.  
  
## Syntax  
  
```  
  
uint8ClampedArray = new Uint8ClampedArray( length ); uint8ClampedArray = new Uint8ClampedArray( array ); uint8ClampedArray = new Uint8ClampedArray( buffer, byteOffset, length);  
```  
  
## Parameter  
 `uint8ClampedArray`  
 Erforderlich.  Der Variablenname, dem das `Uint8ClampedArray`\-Objekt zugewiesen wird.  
  
 `length`  
 Dies ist optional.  Die Anzahl der Elemente im Array.  
  
 `array`  
 Dies ist optional.  Das Array \(oder typisierte Array\), das in diesem Array enthalten ist.  Der Inhalt wird mit dem Inhalt des angegebenen Arrays oder des typisierten Arrays initialisiert, wobei jedes Element in den `Uint8`\-Typ konvertiert wird.  
  
 `buffer`  
 Dies ist optional.  Der [ArrayBuffer](../../javascript/reference/arraybuffer-object.md), den das `Uint8ClampedArray` darstellt.  
  
 `byteOffset`  
 Dies ist optional.  Der Offset in Bytes vom Beginn des Puffers an, bei dem das `Uint8ClampedArray` beginnen soll.  
  
 `length`  
 Dies ist optional.  Die Anzahl der Elemente im Array.  
  
## Hinweise  
 Die in einem `Uint8ClampedArray`\-Objekt gespeicherten Werte liegen zwischen 0 und 255.  Wenn Sie einen negativen Wert für einen Arraymember angeben, wird 0 als Wert festgelegt.  Wenn Sie einen Wert größer 255 angeben, wird 255 als Wert festgelegt.  
  
 Die Werte in einem `Uint8ClampedArray`\-Objekt werden auf den nächsten geraden Wert gerundet; dies wird als unverzerrte Rundung \(Banker's Rounding\) bezeichnet.  
  
## Konstanten  
 In der folgenden Tabelle werden die Konstanten des `Uint8ClampedArray`\-Objekts aufgelistet.  
  
|Konstante|Beschreibung|  
|---------------|------------------|  
|[BYTES\_PER\_ELEMENT\-Konstante](../../javascript/reference/bytes-per-element-constant-uint8clampedarray.md)|Die Größe jedes Elements im Array in Bytes.|  
  
## Eigenschaften  
 In der folgenden Tabelle werden die Konstanten des `Uint8ClampedArray`\-Objekts aufgelistet.  
  
|Eigenschaft|Beschreibung|  
|-----------------|------------------|  
|[Puffereigenschaft](../../javascript/reference/buffer-property-uint8clampedarray.md)|Schreibgeschützt.  Ruft den [ArrayBuffer](../../javascript/reference/arraybuffer-object.md) ab, auf den durch dieses Array verwiesen wird.|  
|[byteLength\-Eigenschaft](../../javascript/reference/bytelength-property-uint8clampedarray.md)|Schreibgeschützt.  Die Länge dieses Arrays vom Beginn des [ArrayBuffers](../../javascript/reference/arraybuffer-object.md) in Bytes, so wie bei der Konstruktion festgelegt.|  
|[byteOffset\-Eigenschaft](../../javascript/reference/byteoffset-property-uint8clampedarray.md)|Schreibgeschützt.  Der Offset dieses Arrays vom Beginn des [ArrayBuffers](../../javascript/reference/arraybuffer-object.md) in Bytes, so wie bei der Konstruktion festgelegt.|  
|[Längeneigenschaft](../../javascript/reference/length-property-uint8clampedarray.md)|Die Länge des Arrays.|  
  
## Methoden  
 In der folgenden Tabelle werden die Methoden des `Uint8ClampedArray`\-Objekts aufgelistet.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[set\-Methode](../../javascript/reference/set-method-uint8clampedarray.md)|Legt einen Wert oder ein Wertearray fest.|  
|[subarray\-Methode](../../javascript/reference/subarray-method-uint8clampedarray.md)|Ruft eine neue `Uint8ClampedArray`\-Ansicht des [ArrayBuffer](../../javascript/reference/arraybuffer-object.md)\-Speichers für dieses Array ab und gibt die ersten und letzten Elemente des Unterarrays an.|  
  
## Beispiel  
 Im folgenden Beispiel wird gezeigt, wie ein `Uint8ClampedArray`\-Objekt verwendet wird, um die von einer `XmlHttpRequest` abgerufenen Binärdaten zu verarbeiten:  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataview = new DataView(buffer);  
            var ints = new Uint8ClampedArray(buffer.byteLength);  
            for (var i = 0; i < ints.length; i++) {  
                ints[i] = dataview.getUint8(i);  
            }  
        alert(ints[10]);  
        }  
    }  
  
```  
  
## Beispiel  
 Das folgende Beispiel zeigt, wie Werte in einem `Uint8ClampedArray` eingeschränkt werden.  
  
```javascript  
var ints = new Uint8ClampedArray(2);  
ints[0] = -1;  // 0 will be assigned.  
ints[1] = 256; // 255 will be assigned.  
  
```  
  
## Beispiel  
 Das folgende Beispiel zeigt, wie Werte in einem `Uint8ClampedArray` gerundet werden.  
  
```  
var ints = new Uint8ClampedArray(4);  
ints[0] = 11.3; // 11 will be assigned (same as Int8Array).  
ints[1] = 11.8; // 11 will be assigned (same as Int8Array).  
ints[2] = 10.5; // 10 will be assigned (rounded to the nearest   
                // even value).  
ints[3] = 11.5; // 12 will be assigned (rounded to the nearest   
                // even value).  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv11_winonly](../../javascript/reference/includes/jsv11-winonly-md.md)]  
  
## Siehe auch  
 [Uint8Array\-Objekt](../../javascript/reference/uint8array-object.md)   
 [ArrayBuffer\-Objekt](../../javascript/reference/arraybuffer-object.md)
---
title: "Uint32Array-Objekt | Microsoft Docs"
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
ms.assetid: c4bf5409-2d4b-4660-9f4b-a45d7a02b47e
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# Uint32Array-Objekt
Ein typisiertes Array von ganzzahligen 32\-Bit\-Werten ohne Vorzeichen.  Der Inhalt wird mit 0 initialisiert.  Wenn die angeforderte Anzahl von Bytes nicht zugeordnet werden kann, wird eine Ausnahme ausgelöst.  
  
## Syntax  
  
```  
  
      uint32Array = new Uint32Array( length );  
uint32Array = new Uint32Array( array );  
uint32Array = new Uint32Array( buffer, byteOffset, length);  
```  
  
## Parameter  
 `uint32Array`  
 Erforderlich.  Der Variablenname, dem das **Uint32Array**\-Objekt zugewiesen ist.  
  
 `length`  
 Gibt die Anzahl der Elemente im Array an.  
  
 `array`  
 Das Array \(oder typisierte Array\), das in diesem Array enthalten ist.  Der Inhalt wird mit dem Inhalt des angegebenen Arrays oder des typisierten Arrays initialisiert, wobei jedes Element in den Uint32\-Typ konvertiert wird.  
  
 `buffer`  
 Das ArrayBuffer\-Objekt, das das Uint32Array darstellt.  
  
 `byteOffset`  
 Optional.  Gibt den Offset in Bytes vom Beginn des Puffers an, bei dem das Uint32Array beginnen soll.  
  
 `length`  
 Die Anzahl der Elemente im Array.  
  
## Konstanten  
 In der folgenden Tabelle werden die Konstanten des `Uint32Array`\-Objekts aufgelistet.  
  
|Konstante|Beschreibung|  
|---------------|------------------|  
|[BYTES\_PER\_ELEMENT\-Konstante](../../javascript/reference/bytes-per-element-constant-uint32array.md)|Die Größe jedes Elements im Array in Bytes.|  
  
## Eigenschaften  
 In der folgenden Tabelle werden die Konstanten des `Uint32Array`\-Objekts aufgelistet.  
  
|Eigenschaft|Beschreibung|  
|-----------------|------------------|  
|[Puffereigenschaft](../../javascript/reference/buffer-property-uint32array.md)|Schreibgeschützt.  Ruft den ArrayBuffer ab, auf den durch dieses Array verwiesen wird.|  
|[byteLength\-Eigenschaft](../../javascript/reference/bytelength-property-uint32array.md)|Schreibgeschützt.  Die Länge dieses Arrays vom Beginn des ArrayBuffers in Bytes, so wie während der Konstruktionszeit festgelegt.|  
|[byteOffset\-Eigenschaft](../../javascript/reference/byteoffset-property-uint32array.md)|Schreibgeschützt.  Der Offset dieses Arrays vom Beginn des ArrayBuffers in Bytes, so wie während der Konstruktionszeit festgelegt.|  
|[Längeneigenschaft](../../javascript/reference/length-property-uint32array.md)|Die Länge des Arrays.|  
  
## Methoden  
 In der folgenden Tabelle werden die Methoden des `Uint32Array`\-Objekts aufgelistet.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[Set\-Methode \(Uint32Array\)](../../javascript/reference/set-method-uint32array.md)|Legt einen Wert oder ein Wertearray fest.|  
|[subarray\-Methode \(Uint32Array\)](../../javascript/reference/subarray-method-uint32array.md)|Ruft eine neue Uint32Array\-Ansicht des ArrayBuffer\-Speichers für dieses Array ab.|  
  
## Beispiel  
 Im folgenden Beispiel wird gezeigt, wie ein Uint32Array\-Objekt verwendet wird, um die von XMLHttpRequest abgerufenen Binärdaten zu verarbeiten:  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataview = new DataView(buffer);  
            var ints = new Uint32Array(buffer.byteLength / 4);  
            for (var i = 0; i < ints.length; i++) {  
                ints[i] = dataview.getUint32(i * 4);  
            }  
        alert(ints[10]);  
        }  
    }  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]
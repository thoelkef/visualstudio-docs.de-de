---
title: Uint16Array-Objekt | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: e684647d-04d0-41a9-9089-16612e18ec7d
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 447c0509a29f1696e0204d6f37ff88d3c0bdecae
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641700"
---
# <a name="uint16array-object"></a>Uint16Array-Objekt
Ein typisiertes Array von 16-Bit-Ganzzahlwerte ohne Vorzeichen. Der Inhalt wird mit 0 initialisiert. Wenn die angeforderte Anzahl von Bytes nicht zugeordnet werden kann, wird eine Ausnahme ausgelöst.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
      uint16Array = new Uint16Array( length );  
uint16Array = new Uint16Array( array );  
uint16Array = new Uint16Array( buffer, byteOffset, length );  
```  
  
## <a name="parameters"></a>Parameter  
 `uint16Array`  
 Erforderlich. Der Variablenname, dem die **Uint16Array** -Objekt zugewiesen ist.  
  
 `length`  
 Gibt die Anzahl der Elemente im Array an.  
  
 `array`  
 Das Array (oder typisierte Array), das in diesem Array enthalten ist. Der Inhalt wird mit dem Inhalt des angegebenen Arrays oder des typisierten Arrays initialisiert, wobei jedes Element in den Uint16-Typ konvertiert wird.  
  
 `buffer`  
 Das ArrayBuffer-Objekt, das das Uint16Array darstellt.  
  
 `byteOffset`  
 Dies ist optional. Gibt den Offset in Bytes vom Beginn des Puffers an, bei dem das Uint16Array beginnen soll.  
  
 `length`  
 Die Anzahl der Elemente im Array.  
  
## <a name="constants"></a>Konstanten  
 In der folgenden Tabelle werden die Konstanten des `Uint16Array`-Objekts aufgelistet.  
  
|Konstante|Beschreibung|  
|--------------|-----------------|  
|[BYTES_PER_ELEMENT-Konstante](../../javascript/reference/bytes-per-element-constant-uint16array.md)|Die Größe jedes Elements im Array in Bytes.|  
  
## <a name="properties"></a>Eigenschaften  
 In der folgenden Tabelle werden die Konstanten des `Uint16Array`-Objekts aufgelistet.  
  
|Eigenschaft|Beschreibung|  
|--------------|-----------------|  
|[Buffer-Eigenschaft](../../javascript/reference/buffer-property-uint16array.md)|Schreibgeschützt. Ruft den ArrayBuffer ab, auf den durch dieses Array verwiesen wird.|  
|[ByteLength-Eigenschaft](../../javascript/reference/bytelength-property-uint16array.md)|Schreibgeschützt. Die Länge dieses Arrays vom Beginn des ArrayBuffers in Bytes, so wie bei der Konstruktion festgelegt.|  
|[ByteOffset-Eigenschaft](../../javascript/reference/byteoffset-property-uint16array.md)|Schreibgeschützt. Der Offset dieses Arrays vom Beginn des ArrayBuffers in Bytes, so wie bei der Konstruktion festgelegt.|  
|[Length-Eigenschaft](../../javascript/reference/length-property-uint16array.md)|Die Länge des Arrays.|  
|||  
  
## <a name="methods"></a>Methoden  
 In der folgenden Tabelle werden die Methoden des `Uint16Array`-Objekts aufgelistet.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[set-Methode (Uint16Array)](../../javascript/reference/set-method-uint16array.md)|Legt einen Wert oder ein Wertearray fest.|  
|[subarray-Methode (Uint16Array)](../../javascript/reference/subarray-method-uint16array.md)|Ruft eine neue Uint16Array-Ansicht des ArrayBuffer-Speichers für dieses Array ab.|  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird gezeigt, wie ein Uint16Array-Objekt verwendet wird, um die von XmlHttpRequest abgerufenen Binärdaten zu verarbeiten:  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataview = new DataView(buffer);  
            var ints = new Uint16Array(buffer.byteLength / 2);  
            for (var i = 0; i < ints.length; i++) {  
                ints[i] = dataview.getUint16(i * 2);  
            }  
        alert(ints[10]);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]
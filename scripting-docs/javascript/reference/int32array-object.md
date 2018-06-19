---
title: Int32Array-Objekt | Microsoft Docs
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
ms.assetid: 48696299-e41e-4590-b1b5-26fe19f68139
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 64e37564d4b4ffd336a83285818e90262f32040a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637760"
---
# <a name="int32array-object"></a>Int32Array-Objekt
Ein typisiertes Array von 32-Bit-Ganzzahlwerten. Der Inhalt wird mit 0 initialisiert. Wenn die angeforderte Anzahl von Bytes nicht zugeordnet werden kann, wird eine Ausnahme ausgelöst.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
      int32Array = new Int32Array( length );  
int32Array = new Int32Array( array );  
int32Array = new Int32Array( buffer, byteOffset, length);  
```  
  
## <a name="parameters"></a>Parameter  
 `int32Array`  
 Erforderlich. Der Variablenname, dem die **Int32Array** -Objekt zugewiesen ist.  
  
 `length`  
 Gibt die Anzahl der Elemente im Array an.  
  
 `array`  
 Das Array (oder typisierte Array), das in diesem Array enthalten ist. Der Inhalt wird mit dem Inhalt des angegebenen Arrays oder des typisierten Arrays initialisiert, wobei jedes Element in den Int32-Typ konvertiert wird.  
  
 `buffer`  
 Das ArrayBuffer-Objekt, das das Int32Array darstellt.  
  
 `byteOffset`  
 Dies ist optional. Gibt den Offset in Bytes vom Beginn des Puffers an, bei dem das Int32Array beginnen soll.  
  
 `length`  
 Die Anzahl der Elemente im Array.  
  
## <a name="constants"></a>Konstanten  
 In der folgenden Tabelle werden die Konstanten des `Int32Array`-Objekts aufgelistet.  
  
|Konstante|Beschreibung|  
|--------------|-----------------|  
|[BYTES_PER_ELEMENT-Konstante](../../javascript/reference/bytes-per-element-constant-int32array.md)|Die Größe jedes Elements im Array in Bytes.|  
  
## <a name="properties"></a>Eigenschaften  
 In der folgenden Tabelle werden die Konstanten des `Int32Array`-Objekts aufgelistet.  
  
|Eigenschaft|Beschreibung|  
|--------------|-----------------|  
|[Buffer-Eigenschaft](../../javascript/reference/buffer-property-int32array.md)|Schreibgeschützt. Ruft den ArrayBuffer ab, auf den durch dieses Array verwiesen wird.|  
|[ByteLength-Eigenschaft](../../javascript/reference/bytelength-property-int32array.md)|Schreibgeschützt. Die Länge dieses Arrays vom Beginn des ArrayBuffers in Bytes, so wie bei der Konstruktion festgelegt.|  
|[ByteOffset-Eigenschaft](../../javascript/reference/byteoffset-property-int32array.md)|Schreibgeschützt. Der Offset dieses Arrays vom Beginn des ArrayBuffers in Bytes, so wie bei der Konstruktion festgelegt.|  
|[Length-Eigenschaft](../../javascript/reference/length-property-int32array.md)|Die Länge des Arrays.|  
  
## <a name="methods"></a>Methoden  
 In der folgenden Tabelle werden die Methoden des `Int32Array`-Objekts aufgelistet.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[set-Methode (Int32Array)](../../javascript/reference/set-method-int32array.md)|Legt einen Wert oder ein Wertearray fest.|  
|[subarray-Methode (Int32Array)](../../javascript/reference/subarray-method-int32array.md)|Ruft eine neue Int32Array-Ansicht des ArrayBuffer-Speichers für dieses Array ab.|  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird gezeigt, wie ein Int32Array-Objekt verwendet wird, um die von XmlHttpRequest abgerufenen Binärdaten zu verarbeiten.  
  
```JavaScript  
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
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]
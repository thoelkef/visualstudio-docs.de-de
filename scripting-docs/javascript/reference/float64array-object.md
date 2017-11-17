---
title: Float64Array-Objekt | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 74c945dc-56ae-458c-b0aa-782f240e9b6c
caps.latest.revision: "18"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 20544812d94c1234d85d714f6e469d0de4f4c5ab
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="float64array-object"></a>Float64Array-Objekt
Ein typisiertes Array von 64-Bit-Gleitkommawerten. Der Inhalt wird mit 0 initialisiert. Wenn die angeforderte Anzahl von Bytes nicht zugeordnet werden kann, wird eine Ausnahme ausgelöst.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
      float64Array = new Float64Array( length );  
float64Array = new Float64Array( array );  
float64Array = new Float64Array( buffer, byteOffset, length);  
```  
  
## <a name="parameters"></a>Parameter  
 `float64Array`  
 Erforderlich. Der Variablenname, dem die **Float64Array** -Objekt zugewiesen ist.  
  
 `length`  
 Gibt die Anzahl der Elemente im Array an.  
  
 `array`  
 Das Array (oder typisierte Array), das in diesem Array enthalten ist. Der Inhalt wird mit dem Inhalt des angegebenen Arrays oder des typisierten Arrays initialisiert, wobei jedes Element in den Float64-Typ konvertiert wird.  
  
 `buffer`  
 Das ArrayBuffer-Objekt, das das Float64Array darstellt.  
  
 `byteOffset`  
 Dies ist optional. Gibt den Offset in Bytes vom Beginn des Puffers an, bei dem das Float64Array beginnen soll.  
  
 `length`  
 Die Anzahl der Elemente im Array.  
  
## <a name="constants"></a>Konstanten  
 In der folgenden Tabelle werden die Konstanten des `Float64Array`-Objekts aufgelistet.  
  
|Konstante|Beschreibung|  
|--------------|-----------------|  
|[BYTES_PER_ELEMENT-Konstante](../../javascript/reference/bytes-per-element-constant-float64array.md)|Die Größe jedes Elements im Array in Bytes.|  
  
## <a name="properties"></a>Eigenschaften  
 In der folgenden Tabelle werden die Konstanten des `Float64Array`-Objekts aufgelistet.  
  
|Eigenschaft|Beschreibung|  
|--------------|-----------------|  
|[Buffer-Eigenschaft](../../javascript/reference/bytelength-property-float64array.md)|Schreibgeschützt. Ruft den ArrayBuffer ab, auf den durch dieses Array verwiesen wird.|  
|[ByteLength-Eigenschaft](../../javascript/reference/bytelength-property-float64array.md)|Schreibgeschützt. Die Länge dieses Arrays vom Beginn des ArrayBuffers in Bytes, so wie bei der Konstruktion festgelegt.|  
|[ByteOffset-Eigenschaft](../../javascript/reference/length-property-float64array.md)|Schreibgeschützt. Der Offset dieses Arrays vom Beginn des ArrayBuffers in Bytes, so wie bei der Konstruktion festgelegt.|  
|[Length-Eigenschaft](../../javascript/reference/length-property-float64array.md)|Die Länge des Arrays.|  
  
## <a name="methods"></a>Methoden  
 In der folgenden Tabelle werden die Methoden des `Float64Array`-Objekts aufgelistet.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[Get-Methode](../../javascript/reference/get-method-float64array.md)|Kann unterdrückt werden. Ruft das Element am angegebenen Index ab.|  
|[set-Methode (Float64Array)](../../javascript/reference/set-method-float64array.md)|Legt einen Wert oder ein Wertearray fest.|  
|[subarray-Methode (Float64Array)](../../javascript/reference/subarray-method-float64array.md)|Ruft eine neue Float64Array-Ansicht des ArrayBuffer-Speichers für dieses Array ab.|  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird gezeigt, wie ein Float64Array-Objekt verwendet wird, um die von einem XmlHttpRequest abgerufenen Binärdaten zu verarbeiten:  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataview = new DataView(buffer);  
            var ints = new Float64Array(buffer.byteLength / 8);  
            for (var i = 0; i < ints.length; i++) {  
                ints[i] = dataview.getFloat64(i * 8);  
            }  
        alert(ints[10]);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]
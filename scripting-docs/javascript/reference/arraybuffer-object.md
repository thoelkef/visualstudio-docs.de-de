---
title: ArrayBuffer-Objekt | Microsoft Docs
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
ms.assetid: 9fda1261-f450-493b-b3db-ecfa9ca93cd7
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c253d63d12a4a5e71d1661aae560b74debecdd62
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24634320"
---
# <a name="arraybuffer-object"></a>ArrayBuffer-Objekt
Stellt einen Rohdatenpuffer für Binärdaten dar, der zum Speichern von Daten für die unterschiedlichen typisierten Arrays verwendet wird. `ArrayBuffers`nicht von gelesen oder geschrieben direkt, jedoch an ein typisiertes Array übergeben werden können oder [DataView-Objekts](../../javascript/reference/dataview-object.md) auf den unformatierten Puffer nach Bedarf zu interpretieren.  
  
 Weitere Informationen zu typisierten Arrays finden Sie unter [typisierte Arrays](../../javascript/advanced/typed-arrays-javascript.md).  
  
## <a name="syntax"></a>Syntax  
  
```JavaScript  
  
arrayBuffer = new ArrayBuffer(length);  
```  
  
## <a name="parameters"></a>Parameter  
 `arrayBuffer`  
 Erforderlich. Der Variablenname, dem das `ArrayBuffer`-Objekt zugewiesen wird.  
  
 `length`  
 Die Länge des Puffers. Der Inhalt des ArrayBuffer-Objekts wird mit 0 initialisiert. Wenn die angeforderte Anzahl von Bytes nicht zugeordnet werden kann, wird eine Ausnahme ausgelöst.  
  
## <a name="properties"></a>Eigenschaften  
 In der folgenden Tabelle werden die Eigenschaften des `ArrayBuffer`-Objekts aufgelistet.  
  
|Eigenschaft|Beschreibung|  
|--------------|-----------------|  
|[ByteLength-Eigenschaft](../../javascript/reference/bytelength-property-arraybuffer.md)|Schreibgeschützt. Die Länge des ArrayBuffer-Objekts in Bytes.|  
  
## <a name="functions"></a>Funktionen  
 In der folgenden Tabelle werden die Funktionen des `ArrayBuffer`-Objekts aufgelistet.  
  
|Eigenschaft|Beschreibung|  
|--------------|-----------------|  
|[ArrayBuffer.isView-Funktion](../../javascript/reference/arraybuffer-isview-function-arraybuffer.md)|Bestimmt, ob ob ein Objekt eine Ansicht des Puffers bereitstellt.|  
  
## <a name="methods"></a>Methoden  
 In der folgenden Tabelle werden die Methoden des `ArrayBuffer`-Objekts aufgelistet.  
  
|Eigenschaft|Beschreibung|  
|--------------|-----------------|  
|[Slice-Methode](../../javascript/reference/slice-method-arraybuffer.md)|Gibt einen Abschnitt eines `ArrayBuffer` zurück.|  
  
## <a name="example"></a>Beispiel  
 Im folgende Beispiel wird gezeigt, wie ein ArrayBuffer-Objekt verwendet wird, verarbeitet die Binärdaten aus einer [XMLHttpRequest](http://msdn.microsoft.com/library/ie/ms535874\(v=vs.85\).aspx). Können Sie eine [DataView-Objekts](../../javascript/reference/dataview-object.md) auf die einzelnen Werte zu erhalten.  
  
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
  
## <a name="remarks"></a>Hinweise  
 Weitere Informationen zur Verwendung von `XmlHttpRequest`, finden Sie unter [XMLHttpRequest-Erweiterungen](http://msdn.microsoft.com/en-us/be09137c-6546-441b-b953-dcbf72b77069).  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]
---
title: "DataView-Objekt | Microsoft Docs"
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
ms.assetid: 250ec067-7505-4ee0-82ab-bfd3c2820afa
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# DataView-Objekt
Sie können ein DataView\-Objekt verwenden, um die verschiedenen Arten von Binärdaten an einem beliebigen Speicherort im ArrayBuffer zu lesen und zu schreiben.  
  
## Syntax  
  
```  
  
dataView = new DataView(buffer, byteOffset, byteLength);  
```  
  
## Parameter  
 `dataView`  
 Erforderlich.  Der Variablenname, dem das **DataView**\-Objekt zugewiesen wird.  
  
 `buffer`  
 Der ArrayBuffer, der die DataView darstellt.  
  
 `byteOffset`  
 Dies ist optional.  Gibt den Offset in Bytes vom Beginn des Puffers an, bei dem die DataView beginnen soll.  
  
 `byteLength`  
 Dies ist optional.  Gibt die Länge \(in Bytes\) des Abschnitts des Puffers an, den die DataView darstellen soll.  
  
## Hinweise  
 Wenn byteOffset und byteLength ausgelassen werden, umfasst die DataView den gesamten ArrayBuffer\-Bereich.  Wenn byteLength ausgelassen wird, reicht die DataView aus dem angegebenen byteOffset bis zum Ende des ArrayBuffer.  Wenn das angegebene byteOffset und die byteLength über einen Bereich über das Ende des ArrayBuffer hinaus verweisen, wird eine Ausnahme ausgelöst.  
  
## Eigenschaften  
 In der folgenden Tabelle werden die Eigenschaften des `DataView`\-Objekts aufgelistet.  
  
|Eigenschaft|Beschreibung|  
|-----------------|------------------|  
|[Puffereigenschaft](../../javascript/reference/buffer-property-dataview.md)|Schreibgeschützt.  Ruft das ArrayBuffer ab, auf das durch diese Ansicht verwiesen wird.|  
|[byteLength\-Eigenschaft](../../javascript/reference/bytelength-property-dataview.md)|Schreibgeschützt.  Die Länge dieser Ansicht vom Beginn des ArrayBuffers in Bytes, so wie während der Konstruktionszeit festgelegt.|  
|[byteOffset\-Eigenschaft](../../javascript/reference/byteoffset-property-dataview.md)|Schreibgeschützt.  Der Offset dieser Ansicht vom Beginn des ArrayBuffers in Bytes, so wie während der Konstruktionszeit festgelegt.|  
  
## Methoden  
 In der folgenden Tabelle werden die Methoden des `DataView`\-Objekts aufgelistet.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[getInt8\-Methode](../../javascript/reference/getint8-method-dataview.md)|Ruft den Int8\-Wert am angegebenen Byteoffset vom Beginn der Ansicht ab.|  
|[getUint8\-Methode \(DataView\)](../../javascript/reference/getuint8-method-dataview.md)|Ruft den Uint8\-Wert am angegebenen Byteoffset vom Beginn der Ansicht ab.|  
|[getInt16\-Methode \(DataView\)](../../javascript/reference/getint16-method-dataview.md)|Ruft den Int16\-Wert am angegebenen Byteoffset vom Beginn der Ansicht ab.|  
|[getUint16\-Methode \(DataView\)](../../javascript/reference/getuint16-method-dataview.md)|Ruft den Uint16\-Wert am angegebenen Byteoffset vom Beginn der Ansicht ab.|  
|[getInt32\-Methode \(DataView\)](../../javascript/reference/getint32-method-dataview.md)|Ruft den Int32\-Wert am angegebenen Byteoffset vom Beginn der Ansicht ab.|  
|[getUint32\-Methode \(DataView\)](../../javascript/reference/getuint32-method-dataview.md)|Ruft den Uint32\-Wert am angegebenen Byteoffset vom Beginn der Ansicht ab.|  
|[getFloat32\-Methode \(DataView\)](../../javascript/reference/getfloat32-method-dataview.md)|Ruft den Float32\-Wert am angegebenen Byteoffset vom Beginn der Ansicht ab.|  
|[getFloat64\-Methode \(DataView\)](../../javascript/reference/getfloat64-method-dataview.md)|Ruft den Float64\-Wert am angegebenen Byteoffset vom Beginn der Ansicht ab.|  
|[setInt8\-Methode \(DataView\)](../../javascript/reference/setint8-method-dataview.md)|Speichert einen Int8\-Wert am angegebenen Byteoffset vom Beginn der Ansicht.|  
|[setUint8\-Methode \(DataView\)](../../javascript/reference/setuint8-method-dataview.md)|Speichert einen Uint8\-Wert am angegebenen Byteoffset vom Beginn der Ansicht.|  
|[setInt16\-Methode \(DataView\)](../../javascript/reference/setint16-method-dataview.md)|Speichert einen Int16\-Wert am angegebenen Byteoffset vom Beginn der Ansicht.|  
|[setUint16\-Methode \(DataView\)](../../javascript/reference/setuint16-method-dataview.md)|Speichert einen Uint16\-Wert am angegebenen Byteoffset vom Beginn der Ansicht.|  
|[setInt32\-Methode \(DataView\)](../../javascript/reference/setint32-method-dataview.md)|Speichert einen Int32\-Wert am angegebenen Byteoffset vom Beginn der Ansicht.|  
|[setUint32\-Methode \(DataView\)](../../javascript/reference/setuint32-method-dataview.md)|Speichert einen Uint32\-Wert am angegebenen Byteoffset vom Beginn der Ansicht.|  
|[setFloat32\-Methode \(DataView\)](../../javascript/reference/setfloat32-method-dataview.md)|Speichert einen Float32\-Wert am angegebenen Byteoffset vom Beginn der Ansicht.|  
|[setFloat64\-Methode \(DataView\)](../../javascript/reference/setfloat64-method-dataview.md)|Speichert einen Float64\-Wert am angegebenen Byteoffset vom Beginn der Ansicht.|  
  
## Beispiel  
 Im folgenden Beispiel wird gezeigt, wie ein DataView\-Objekt verwendet wird, um die von einem XmlHttpRequest abgerufenen Binärdaten zu verarbeiten:  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            var ints = new Int32Array(dataView.byteLength / 4);  
            for (var i = 0; i < ints.length; i++) {  
                ints[i] = dataview.getInt32(i * 4);  
            }  
        alert(ints[10]);  
        }  
    }  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]
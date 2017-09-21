---
title: "BP_LOCATION_TYPE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BP_LOCATION_TYPE"
helpviewer_keywords: 
  - "BP_LOCATION_TYPE-Struktur"
ms.assetid: 0248430a-3b61-4809-87a9-e9b6bb7d1130
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# BP_LOCATION_TYPE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Gibt den Positionstyp des Haltepunkts für eine Anforderung Haltepunkt an.  
  
## Syntax  
  
```cpp#  
enum enum_BP_LOCATION_TYPE {   
   BPLT_NONE               = 0x00000000,  
   BPLT_FILE_LINE          = 0x00010000,  
   BPLT_FUNC_OFFSET        = 0x00020000,  
   BPLT_CONTEXT            = 0x00030000,  
   BPLT_STRING             = 0x00040000,  
   BPLT_ADDRESS            = 0x00050000,  
   BPLT_RESOLUTION         = 0x00060000,  
   BPLT_CODE_FILE_LINE     = BPT_CODE | BPLT_FILE_LINE,  
   BPLT_CODE_FUNC_OFFSET   = BPT_CODE | BPLT_FUNC_OFFSET,  
   BPLT_CODE_CONTEXT       = BPT_CODE | BPLT_CONTEXT,  
   BPLT_CODE_STRING        = BPT_CODE | BPLT_STRING,  
   BPLT_CODE_ADDRESS       = BPT_CODE | BPLT_ADDRESS ,  
   BPLT_DATA_STRING        = BPT_DATA | BPLT_STRING,  
   BPLT_TYPE_MASK          = 0x0000FFFF,  
   BPLT_LOCATION_TYPE_MASK = 0xFFFF0000  
};  
typedef DWORD BP_LOCATION_TYPE;  
```  
  
```c#  
public enum enum_BP_LOCATION_TYPE {   
   BPLT_NONE               = 0x00000000,  
   BPLT_FILE_LINE          = 0x00010000,  
   BPLT_FUNC_OFFSET        = 0x00020000,  
   BPLT_CONTEXT            = 0x00030000,  
   BPLT_STRING             = 0x00040000,  
   BPLT_ADDRESS            = 0x00050000,  
   BPLT_RESOLUTION         = 0x00060000,  
   BPLT_CODE_FILE_LINE     = BPT_CODE | BPLT_FILE_LINE,  
   BPLT_CODE_FUNC_OFFSET   = BPT_CODE | BPLT_FUNC_OFFSET,  
   BPLT_CODE_CONTEXT       = BPT_CODE | BPLT_CONTEXT,  
   BPLT_CODE_STRING        = BPT_CODE | BPLT_STRING,  
   BPLT_CODE_ADDRESS       = BPT_CODE | BPLT_ADDRESS ,  
   BPLT_DATA_STRING        = BPT_DATA | BPLT_STRING,  
   BPLT_TYPE_MASK          = 0x0000FFFF,  
   BPLT_LOCATION_TYPE_MASK = 0xFFFF0000  
};  
```  
  
## Mitglieder  
 BPLT\_NONE  
 Gibt keine Haltepunktposition an.  
  
 BPLT\_FILE\_LINE  
 Gibt den Positionstyp des Haltepunkts Zeile als Datei angezeigt.  
  
 BPLT\_FUNC\_OFFSET  
 Gibt den Positionstyp des Haltepunkts, z. B. einen Offset der Funktion an.  
  
 BPLT\_CONTEXT  
 Gibt den Positionstyp des Haltepunkts als Kontext angezeigt.  
  
 BPLT\_STRING  
 Gibt den Positionstyp des Haltepunkts als Zeichenfolge an.  
  
 BPLT\_ADDRESS  
 Gibt den Positionstyp des Haltepunkts als Adresse an.  
  
 BPLT\_RESOLUTION  
 Gibt den Positionstyp des Haltepunkts als Lösung an.  
  
 BPLT\_CODE\_FILE\_LINE  
 Gibt den Positionstyp des Haltepunkts als Zeile des Quellcodes an.  
  
 BPLT\_CODE\_FUNC\_OFFSET  
 Gibt den Positionstyp des Haltepunkts, z. B. einen Code funktions Offset an.  
  
 BPLT\_CODE\_CONTEXT  
 Gibt den Positionstyp des Haltepunkts Code als Kontext angezeigt.  
  
 BPLT\_CODE\_STRING  
 Gibt den Positionstyp des Haltepunkts als Codezeichenfolge an.  
  
 BPLT\_CODE\_ADDRESS  
 Gibt den Positionstyp des Haltepunkts als Code\-Adresse an.  
  
 BPLT\_DATA\_STRING  
 Gibt den Positionstyp des Haltepunkts z. B. eine Zeichenfolge Daten an.  
  
 BPLT\_TYPE\_MASK  
 Gibt eine Bitmaske an, dass der Haltepunkt den Typ aus dem Wert out extrahiert werden kann.  
  
 BPLT\_LOCATION\_TYPE\_MASK  
 Gibt eine Bitmaske an, dass der Typ Breakpointpositions Wert aus dem Paket extrahiert werden kann.  
  
## Hinweise  
 Übergabe als Parameter an die [GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md)\-Methode.  
  
 Ein Typ wird von einem Haltepunkt Breakpointpositions Typ und einem Positionstyp besteht.  Dies bedeutet, dass ein Werttyp niemals nur ein Haltepunkt Breakpointpositions Typ \(z. B.`BPT_CODE`\) oder ein Positionstyp ist \(z. B`BPLT_FILE_LINE`\).  Vordefinierte Konstanten für alle derzeit unterstützten Breakpointpositions Typen werden in dieser Enumeration \(`BPLT_CODE_FILE_LINE` von `BPLT_DATA_STRING`\) enthalten.  
  
 `BPT_CODE` und `BPT_DATA` sind Member der [BP\_TYPE](../../../extensibility/debugger/reference/bp-type.md)\-Enumeration.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md)   
 [BP\_TYPE](../../../extensibility/debugger/reference/bp-type.md)
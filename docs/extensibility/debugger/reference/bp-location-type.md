---
title: BP_LOCATION_TYPE | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- BP_LOCATION_TYPE
helpviewer_keywords:
- BP_LOCATION_TYPE structure
ms.assetid: 0248430a-3b61-4809-87a9-e9b6bb7d1130
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: db35e354b2cfbe91b9c6041dc6239d2dfd2531f8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31108942"
---
# <a name="bplocationtype"></a>BP_LOCATION_TYPE
Gibt den Typ des Haltepunkts für eine Anforderung Haltepunkt an.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
enum enum_BP_LOCATION_TYPE {   
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
  
```csharp  
public enum enum_BP_LOCATION_TYPE {   
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
  
## <a name="members"></a>Member  
 BPLT_NONE  
 Gibt keine Position des Haltepunkts an.  
  
 BPLT_FILE_LINE  
 Gibt den Typ des Haltepunkts als eine Dateizeile an.  
  
 BPLT_FUNC_OFFSET  
 Gibt den Typ des Haltepunkts als Funktion Offset an.  
  
 BPLT_CONTEXT  
 Gibt den Typ des Haltepunkts als Kontext.  
  
 BPLT_STRING  
 Gibt den Typ des Haltepunkts als Zeichenfolge an.  
  
 BPLT_ADDRESS  
 Gibt den Typ des Haltepunkts als eine Adresse an.  
  
 BPLT_RESOLUTION  
 Gibt den Typ des Haltepunkts als eine Auflösung an.  
  
 BPLT_CODE_FILE_LINE  
 Gibt den Typ des Haltepunkts als eine Zeile des Quellcodes an.  
  
 BPLT_CODE_FUNC_OFFSET  
 Gibt den Typ des Haltepunkts als Code Funktion Offset an.  
  
 BPLT_CODE_CONTEXT  
 Gibt den Typ des Haltepunkts als einen Codekontext an.  
  
 BPLT_CODE_STRING  
 Gibt den Typ des Haltepunkts als Codezeichenfolge an.  
  
 BPLT_CODE_ADDRESS  
 Gibt den Typ des Haltepunkts als eine Adresse an.  
  
 BPLT_DATA_STRING  
 Gibt den Typ des Haltepunkts als eine Zeichenfolge an.  
  
 BPLT_TYPE_MASK  
 Gibt eine Bitmaske an, damit das Haltepunkttyp aus den Wert extrahiert werden kann.  
  
 BPLT_LOCATION_TYPE_MASK  
 Gibt eine Bitmaske an, damit das Haltepunkt-Speicherorttyp aus den Wert extrahiert werden kann.  
  
## <a name="remarks"></a>Hinweise  
 Übergeben als Parameter an die [GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md) Methode.  
  
 Ein Haltepunkt Speicherorttyp besteht aus einem Haltepunkt und einen Speicherorttyp. Dies bedeutet, dass ein Haltepunkt Speicherorttyp nie ein Haltepunkt-Typ ist (z. B. `BPT_CODE`) oder einen Ortstyp (z. B. `BPLT_FILE_LINE`). Vordefinierte Konstanten für alle derzeit unterstützten Haltepunkt-Speicherort-Typen sind in dieser Enumeration enthalten (`BPLT_CODE_FILE_LINE` über `BPLT_DATA_STRING`).  
  
 `BPT_CODE` und `BPT_DATA` sind Mitglied der [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md) Enumeration.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md)   
 [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)
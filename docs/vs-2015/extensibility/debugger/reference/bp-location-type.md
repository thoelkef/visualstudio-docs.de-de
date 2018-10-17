---
title: BP_LOCATION_TYPE | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- BP_LOCATION_TYPE
helpviewer_keywords:
- BP_LOCATION_TYPE structure
ms.assetid: 0248430a-3b61-4809-87a9-e9b6bb7d1130
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6feb9f65789ea401b1ee79e2b23f265798fcd18e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49276795"
---
# <a name="bplocationtype"></a>BP_LOCATION_TYPE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Gibt den Typ des Haltepunkts für eine Haltepunkt-Anforderung an.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
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
 Gibt den Typ des Haltepunkts als Adresse an.  
  
 BPLT_RESOLUTION  
 Gibt den Typ des Haltepunkts als Lösung an.  
  
 BPLT_CODE_FILE_LINE  
 Gibt den Typ des Haltepunkts als eine Zeile des Quellcodes an.  
  
 BPLT_CODE_FUNC_OFFSET  
 Gibt den Typ des Haltepunkts als Offset-Funktion Code an.  
  
 BPLT_CODE_CONTEXT  
 Gibt den Typ des Haltepunkts als Codekontext an.  
  
 BPLT_CODE_STRING  
 Gibt den Typ des Haltepunkts als eine Zeichenfolge an.  
  
 BPLT_CODE_ADDRESS  
 Gibt den Typ des Haltepunkts als eine Adresse an.  
  
 BPLT_DATA_STRING  
 Gibt den Typ des Haltepunkts als eine Zeichenfolge mit Daten an.  
  
 BPLT_TYPE_MASK  
 Gibt eine Bitmaske, damit der Haltepunkttyp aus dem Wert extrahiert werden kann.  
  
 BPLT_LOCATION_TYPE_MASK  
 Gibt eine Bitmaske, damit die Haltepunktpositionstyp aus dem Wert extrahiert werden kann.  
  
## <a name="remarks"></a>Hinweise  
 Übergeben als Parameter an die [GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md) Methode.  
  
 Eine Haltepunktpositionstyp besteht aus einem Haltepunkt und einen Speicherorttyp. Dies bedeutet, dass eine Haltepunktpositionstyp nie nur einen Haltepunkttyp ist (z. B. `BPT_CODE`) oder einen Standorttyp (z. B. `BPLT_FILE_LINE`). Vordefinierte Konstanten für alle Haltepunkttypen, Speicherort unterstützt derzeit befinden sich in dieser Enumeration (`BPLT_CODE_FILE_LINE` über `BPLT_DATA_STRING`).  
  
 `BPT_CODE` und `BPT_DATA` sind Mitglied der [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md) Enumeration.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md)   
 [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)


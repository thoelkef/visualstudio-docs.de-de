---
title: BSTR_ARRAY | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- BSTR_ARRAY
helpviewer_keywords:
- BSTR_ARRAY structure
ms.assetid: 48da37f7-a237-48a9-9ff9-389c1a00862c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 90f3089841e4f5eab5a490eb5968eacda8af8808
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53864039"
---
# <a name="bstrarray"></a>BSTR_ARRAY
Eine Struktur, die ein Array von Zeichenfolgen beschreibt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
typedef struct tagBSTR_ARRAY {  
   DWORD dwCount;  
   BSTR* Members;  
} BSTR_ARRAY;  
```  
  
```csharp  
struct BSTR_ARRAY {  
   DWORD    dwCount;  
   string[] Members;  
}  
```  
  
## <a name="terms"></a>Begriffe  
 dwCount  
 Anzahl der Zeichenfolgen in `Members` Array.  
  
 Member  
 Array von Zeichenfolgen.  
  
## <a name="remarks"></a>Hinweise  
 Diese Struktur wird zurückgegeben, die [EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md) Methode.  
  
 [Nur für C++] Jeder einzelnen Zeichenfolge muss freigegeben werden, mithilfe von `SysFreeString`, und die `Members` Array muss mit dem freigegeben `CoTaskMemFree`.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md)
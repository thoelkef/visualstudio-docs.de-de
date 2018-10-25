---
title: BSTR_ARRAY | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
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
ms.openlocfilehash: d122afe0aca50b50133146edb26e13fd31d2c45b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49906942"
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
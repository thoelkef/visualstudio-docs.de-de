---
title: BSTR_ARRAY | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: BSTR_ARRAY
helpviewer_keywords: BSTR_ARRAY structure
ms.assetid: 48da37f7-a237-48a9-9ff9-389c1a00862c
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 32ef5a93cc5051e2431305dd5181908e9cb7b153
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="bstrarray"></a>BSTR_ARRAY
Eine Struktur, die ein Array von Zeichenfolgen beschrieben.  
  
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
 Diese Struktur wird zurückgegeben, aus der [EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md) Methode.  
  
 [Nur C++] Jede einzelne Zeichenfolge muss freigegeben werden, mithilfe von `SysFreeString`, und die `Members` Array reserviert werden muss, mit `CoTaskMemFree`.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md)
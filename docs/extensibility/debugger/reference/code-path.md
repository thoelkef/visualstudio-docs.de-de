---
title: CODE_PATH | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- CODE_PATH
helpviewer_keywords:
- CODE_PATH structure
ms.assetid: 2d4b2890-4c9d-47e1-83c0-df9c6436427f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6c88737638b20eafdef0ef84f5c45e494cf39607
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31109784"
---
# <a name="codepath"></a>CODE_PATH
Beschreibt eine Methode oder Funktion aufrufen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
typedef struct tagCODE_PATH {   
   BSTR                bstrName;  
   IDebugCodeContext2* pCode;  
} CODE_PATH;  
```  
  
```csharp  
public struct CODE_PATH {  
   public string            bstrName;  
   public IDebugCodeContext pCode;  
}  
```  
  
## <a name="members"></a>Member  
 bstrName  
 Der Name des Code-Pfads.  
  
 pCode  
 Die [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) -Objekt, das in den Code einer Funktion in Einzelschritten bezeichnet.  
  
## <a name="remarks"></a>Hinweise  
 Diese Struktur wird verwendet, um einem Einzelschritt in eine Funktion zu implementieren. [EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md) alle Aufrufe von der aktuellen Position im zu debuggenden Programms zurückgegeben. Diese Struktur stellt eine solche Funktionsaufruf dar.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md)
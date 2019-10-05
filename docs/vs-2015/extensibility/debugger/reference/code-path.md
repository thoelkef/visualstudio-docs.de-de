---
title: CODE_PATH | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- CODE_PATH
helpviewer_keywords:
- CODE_PATH structure
ms.assetid: 2d4b2890-4c9d-47e1-83c0-df9c6436427f
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0e75f5417ffabd26b87afb2a62812904446674c2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68153162"
---
# <a name="codepath"></a>CODE_PATH
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Beschreibt eine Methode oder einen Funktionsaufruf an.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
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
 Der Name des Codepfads.  
  
 pCode  
 Die [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) -Objekt, an welcher Stelle in den Code einer Funktion in Einzelschritten identifiziert.  
  
## <a name="remarks"></a>Hinweise  
 Diese Struktur wird verwendet, um Einzelschritt in eine Funktion zu implementieren. [EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md) gibt alle Aufrufe von der aktuellen Position in die Anwendung gedebuggt wird. Diese Struktur stellt ein solcher Aufruf dar.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md)

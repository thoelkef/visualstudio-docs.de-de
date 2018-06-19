---
title: IDebugProgramNode2::GetHostPid | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgramNode2::GetHostPid
helpviewer_keywords:
- IDebugProgramNode2::GetHostPid
ms.assetid: e65b4b15-46d8-4ca7-9456-2b4c078f7cf9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 33296937ec969deb204d98363afd8ec8af9f1e08
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31115293"
---
# <a name="idebugprogramnode2gethostpid"></a>IDebugProgramNode2::GetHostPid
Ruft die System-Prozess-ID für den Prozess, der die Anwendung hostet.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetHostPid (   
   AD_PROCESS_ID * pdwHostPid  
);  
```  
  
```csharp  
int GetHostPid (   
   out AD_PROCESS_ID pdwHostPid  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pdwHostPid`  
 [out] Gibt das System-Prozess-ID für den Hostprozess zuzugreifen.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="example"></a>Beispiel  
 Im folgende Beispiel wird gezeigt, wie diese Methode für eine einfache implementiert `CProgram` Objekt, implementiert die [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) Schnittstelle.  
  
```cpp  
HRESULT CProgram::GetHostPid(DWORD* pdwHostPid) {    
    // Check for valid argument.    
   if (pdwHostPid)    
    {    
        // Get the process identifier of the calling process.    
      *pdwHostPid = GetCurrentProcessId();    
  
        return S_OK;    
    }    
  
    return E_INVALIDARG;    
}    
```  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
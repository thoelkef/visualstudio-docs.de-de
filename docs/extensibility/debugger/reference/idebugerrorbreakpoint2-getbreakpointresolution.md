---
title: IDebugErrorBreakpoint2::GetBreakpointResolution | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugErrorBreakpoint2::GetBreakpointResolution
helpviewer_keywords:
- IDebugErrorBreakpoint2::GetBreakpointResolution
ms.assetid: 1c2324ed-2a11-4e63-8f3a-f420c7a4018b
caps.latest.revision: 10
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 3e2a2cbbc678e1e2ebcd05607a59481866c7153c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idebugerrorbreakpoint2getbreakpointresolution"></a>IDebugErrorBreakpoint2::GetBreakpointResolution
Ruft die Auflösung der Breakpoint-Fehler, die den Fehler beschreibt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetBreakpointResolution(   
   IDebugErrorBreakpointResolution2** ppErrorResolution  
);  
```  
  
```csharp  
int GetBreakpointResolution(   
   out IDebugErrorBreakpointResolution2 ppErrorResolution  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppErrorResolution`  
 [out] Gibt eine [IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md) -Objekt, das den Fehler beschreibt.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)   
 [IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)
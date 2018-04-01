---
title: IDebugProgramNodeAttach2::OnAttach | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProgramNodeAttach2::OnAttach
helpviewer_keywords:
- IDebugProgramNodeAttach2::OnAttach
ms.assetid: 5fe52761-a508-4ab5-abdb-334fb6590334
caps.latest.revision: 3
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: a6b0f74ef5b14fb9e8971c0d539cc2e875658341
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprogramnodeattach2onattach"></a>IDebugProgramNodeAttach2::OnAttach
Fügt an die zugeordnete Anwendung oder den Prozess anfügen, verzögert die [Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md) Methode.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT OnAttach(  
   [in] REFGUID guidProgramId  
);  
```  
  
```csharp  
int OnAttach(  
   ref Guid guidProgramId  
};  
```  
  
#### <a name="parameters"></a>Parameter  
 `guidProgramId`  
 [in] `GUID` zugeordnetes Programm zuweisen.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`. Gibt `S_FALSE` Wenn die [Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md) Methode sollte nicht aufgerufen werden. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode wird während des Prozesses anfügen aufgerufen, bevor die [Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md) -Methode aufgerufen wird. Die `OnAttach` Methode der anfügungsvorgang selbst ausführen kann (in diesem Fall Methodenrückgabe `S_FALSE`) oder das Aufschieben des Prozess anfügen der `IDebugEngine2::Attach` Methode (die `OnAttach` -Methode zurückkehrt `S_OK`). In jedem Fall die `OnAttach` Methode festlegen kann die `GUID` der zu debuggenden Programms an der angegebenen `GUID`.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md)
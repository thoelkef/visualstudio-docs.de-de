---
title: IDebugProgramNodeAttach2::OnAttach | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProgramNodeAttach2::OnAttach
helpviewer_keywords:
- IDebugProgramNodeAttach2::OnAttach
ms.assetid: 5fe52761-a508-4ab5-abdb-334fb6590334
caps.latest.revision: 3
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 5e0162d17fc81b1304213d0259863f35523a833f
ms.contentlocale: de-de
ms.lasthandoff: 09/26/2017

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

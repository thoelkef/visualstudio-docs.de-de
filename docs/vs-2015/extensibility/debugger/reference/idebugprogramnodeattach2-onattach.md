---
title: IDebugProgramNodeAttach2::OnAttach | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
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
caps.latest.revision: 4
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 73e81537ce73a5b7677174d4694ece16a2a823b7
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47514023"
---
# <a name="idebugprogramnodeattach2onattach"></a>IDebugProgramNodeAttach2::OnAttach
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [IDebugProgramNodeAttach2::OnAttach](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugprogramnodeattach2-onattach).  
  
Fügt an die zugeordnete Anwendung oder den anfügungsprozess, verzögert die [Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md) Methode.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
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
 [in] `GUID` an das zugeordnete Programm zuweisen.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`. Gibt `S_FALSE` Wenn die [Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md) -Methode nicht aufgerufen werden soll. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode wird während des Prozesses anfügen aufgerufen, bevor die [Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md) Methode wird aufgerufen. Die `OnAttach` -Methode kann den anfügungsprozess zu sich selbst ausführen (in diesem Fall ist diese Methode gibt `S_FALSE`) oder zurückgestellt werden, den anfügungsprozess, die `IDebugEngine2::Attach` Methode (die `OnAttach` Methodenrückgabe `S_OK`). In jedem Fall die `OnAttach` Methode kann festlegen, die `GUID` der die zu debuggende Programm wird auf der angegebenen `GUID`.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md)


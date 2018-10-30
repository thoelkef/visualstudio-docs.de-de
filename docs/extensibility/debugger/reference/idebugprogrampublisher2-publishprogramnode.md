---
title: IDebugProgramPublisher2::PublishProgramNode | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgramPublisher2::PublishProgramNode
helpviewer_keywords:
- IDebugProgramPublisher2::PublishProgramNode
ms.assetid: d4b72e04-f726-46cf-8e56-5203ff205b12
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e1182158852e978cb78096eec6e60783317f1cc0
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49930458"
---
# <a name="idebugprogrampublisher2publishprogramnode"></a>IDebugProgramPublisher2::PublishProgramNode
Stellt einen Knoten für die Anwendung zur Verfügung für die Verwendung von Debug-Engines (DEs) und die Sitzung Debug-Manager (SDM).  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT PublishProgramNode(  
   IDebugProgramNode2 *pProgramNode  
);  
```  
  
```csharp  
int PublishProgramNode(  
   IDebugProgramNode2 pProgramNode  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pProgramNode`  
 [in] Ein [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) -Objekt, das den Programm-Knoten zur Verfügung stellen darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode ermöglicht die Programme, die Informationen, bevor Sie auswählen, und starten sie zum Debuggen von abgefragt werden.  
  
 Rufen Sie zum Entfernen eines Knotens Programm von der Verfügbarkeit der [UnpublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogramnode.md) Methode.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [UnpublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogramnode.md)
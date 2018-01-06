---
title: IDebugProcessEx2::Detach | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProcessEx2::Detach
helpviewer_keywords: IDebugProcessEx2::Detach method
ms.assetid: 66d54c2c-9302-47c8-9975-f30ed988ab29
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 40176b654f1a108e995a778eb4c7495b062f6114
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprocessex2detach"></a>IDebugProcessEx2::Detach
Diese Methode informiert dem Prozess, dass eine Sitzung nicht mehr den Prozess debuggen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT Detach(   
   IDebugSession2* pSession  
);  
```  
  
```csharp  
int Detach(  
   IDebugSession2 pSession  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pSession`  
 [in] Ein Wert, der die Sitzung zum Trennen von diesem Prozess eindeutig identifiziert.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Die Schnittstelle übergebenen `pSession` nur als Cookie behandelt werden soll, wird ein Wert, der eindeutig von der Sitzung Debug-Manager, die ursprünglich für diesen Prozess angefügt ist, keine der Methoden für die angegebene Schnittstelle funktionsfähig sind.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)
---
title: IDebugProcessEx2::Attach | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProcessEx2::Attach
helpviewer_keywords:
- IDebugProcessEx2::Attach method
ms.assetid: f3334ed7-39bf-4d02-a338-36f567b9b287
caps.latest.revision: 15
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: da89be65f4b02fa0db254dd85463e422d17fe589
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprocessex2attach"></a>IDebugProcessEx2::Attach
Diese Methode informiert dem Prozess, dass eine Sitzung jetzt den Prozess debuggen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT Attach(   
   IDebugSession2* pSession  
);  
```  
  
```csharp  
int Attach(  
   IDebugSession2 pSession  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pSession`  
 [in] Ein Wert, der die Sitzung, Anhängen an diesem Prozess eindeutig identifiziert.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Die Schnittstelle übergebenen `pSession` nur als ein Cookie, das einen Wert behandelt werden soll, die eindeutig von der Sitzung Debug-Manager für diesen Prozess; anfügen keine der Methoden für die angegebene Schnittstelle funktionsfähig sind.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)
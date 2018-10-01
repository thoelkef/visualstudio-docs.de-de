---
title: IDebugProcessEx2::Attach | Microsoft-Dokumentation
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
- IDebugProcessEx2::Attach
helpviewer_keywords:
- IDebugProcessEx2::Attach method
ms.assetid: f3334ed7-39bf-4d02-a338-36f567b9b287
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6bd544b6805d7000263124a971f4e2a75ae7e95f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47513395"
---
# <a name="idebugprocessex2attach"></a>IDebugProcessEx2::Attach
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [IDebugProcessEx2::Attach](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugprocessex2-attach).  
  
Diese Methode informiert dem Prozess, dass eine Sitzung jetzt Debuggen des Prozesses ist.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
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
 [in] Ein Wert, der die Sitzung, Anfügen an diesen Prozess eindeutig identifiziert.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Die Schnittstelle übergebenen `pSession` nur als ein Cookie, das einen Wert behandelt werden soll, die eindeutig den Anfügen an diesen Prozess; sitzungsbasierter Debug-Manager keine der Methoden für die angegebene Schnittstelle funktionsfähig sind.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)


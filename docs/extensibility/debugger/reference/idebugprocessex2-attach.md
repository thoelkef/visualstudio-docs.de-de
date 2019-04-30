---
title: IDebugProcessEx2::Attach | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProcessEx2::Attach
helpviewer_keywords:
- IDebugProcessEx2::Attach method
ms.assetid: f3334ed7-39bf-4d02-a338-36f567b9b287
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0a39f674744d0b1e97e815d33c2d9564f4a39c0d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62917580"
---
# <a name="idebugprocessex2attach"></a>IDebugProcessEx2::Attach
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

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

---
title: IDebugProcess2::Detach | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProcess2::Detach
helpviewer_keywords:
- IDebugProcess2::Detach
ms.assetid: ee2b9084-2db1-4e49-a1d9-387284b7c3f8
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 633ac46a70ffa7a6becfa0648b53e8f683f838b3
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55027804"
---
# <a name="idebugprocess2detach"></a>IDebugProcess2::Detach
Trennt den Debugger von diesem Prozess, indem Sie alle Programme im Prozess trennen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT Detach(   
   void   
);  
```  
  
```csharp  
int Detach();  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Alle Programme und der Prozess weiter ausgeführt, aber sind nicht mehr Teil der Debugsitzung. Nachdem der Trennvorgang abgeschlossen ist, nicht mehr Debuggen, die Ereignisse für diesen Prozess (und seine Programme) gesendet werden ist.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
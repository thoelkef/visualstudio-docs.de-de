---
title: IDebugProgram2::Terminate | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProgram2::Terminate
helpviewer_keywords:
- IDebugProgram2::Terminate
ms.assetid: 4d3127d3-b1e9-4b28-ac22-2f2eea255f86
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fad3f8829bb4d455dd09df2a896a1e2cd9daa9e6
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54975666"
---
# <a name="idebugprogram2terminate"></a>IDebugProgram2::Terminate
Das Programm beendet.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT Terminate(   
   void   
);  
```  
  
```csharp  
int Terminate();  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Wenn möglich, wird das Programm beendet und aus dem Prozess entladen werden; Andernfalls führt die Debug-Engine (DE) eventuell erforderlichen Bereinigungen.  
  
 Diese Methode oder der [Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md) Methode wird von der IDE, in der Regel in der Antwort an den Benutzer, die das Anhalten des alle-Debuggen aufgerufen. Die Implementierung dieser Methode sollten im Idealfall die Anwendung innerhalb des Prozesses beendet. Wenn dies nicht möglich ist, sollte die DE verhindern, dass das Programm ausführen, bei diesem Vorgang keine weiteren (und werden eventuell erforderlichen Bereinigungen). Wenn die `IDebugProcess2::Terminate` Methode wurde von der IDE aufgerufen, wird der gesamte Prozess einige Zeit nach beendet die `IDebugProgram2::Terminate` Methode wird aufgerufen.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)
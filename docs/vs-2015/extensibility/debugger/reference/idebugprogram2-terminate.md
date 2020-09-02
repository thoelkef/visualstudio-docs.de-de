---
title: 'IDebugProgram2:: beenden | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgram2::Terminate
helpviewer_keywords:
- IDebugProgram2::Terminate
ms.assetid: 4d3127d3-b1e9-4b28-ac22-2f2eea255f86
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4673259e4a8ca0d4354037efbc35b63bedfcbc96
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68146344"
---
# <a name="idebugprogram2terminate"></a>IDebugProgram2::Terminate
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Beendet das Programm.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT Terminate(   
   void   
);  
```  
  
```csharp  
int Terminate();  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn möglich, wird das Programm beendet und vom Prozess entladen. Andernfalls führt die Debug-Engine (de) alle erforderlichen Bereinigungs Vorgänge aus.  
  
 Diese Methode oder die [Beendigungs Methode wird](../../../extensibility/debugger/reference/idebugprocess2-terminate.md) von der IDE aufgerufen, in der Regel als Reaktion darauf, dass der Benutzer das gesamte Debuggen stoppt. Die Implementierung dieser Methode sollte im Idealfall das Programm innerhalb des Prozesses beenden. Wenn dies nicht möglich ist, sollte das Programm verhindern, dass das Programm in diesem Prozess mehr ausgeführt wird (und alle notwendigen Bereinigungs Vorgänge ausführen). Wenn die- `IDebugProcess2::Terminate` Methode von der IDE aufgerufen wurde, wird der gesamte Prozess nach dem Aufrufen der- `IDebugProgram2::Terminate` Methode beendet.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)

---
title: 'IDebugProcess2:: enumthreads | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProcess2::EnumThreads
helpviewer_keywords:
- IDebugProcess2::EnumThreads
ms.assetid: 05677385-7a7f-4545-8438-af00dde85db0
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3e9b6447827baa80da2843c992a8d2233dd1a4b6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68188019"
---
# <a name="idebugprocess2enumthreads"></a>IDebugProcess2::EnumThreads
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ruft eine Liste aller Threads ab, die im Prozess ausgeführt werden.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT EnumThreads(  
   IEnumDebugThreads2** ppEnum  
);  
```  
  
```csharp  
int EnumThreads(  
   out IEnumDebugThreads2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppEnum`  
 vorgenommen Gibt ein [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md) -Objekt zurück, das eine Liste aller Threads in allen Programmen im Prozess enthält.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Methode listet die Threads auf, die in jedem Programm ausgeführt werden, und kombiniert Sie dann in einer Prozessansicht der Threads. Ein einzelner Thread kann in mehreren Programmen ausgeführt werden. Diese Methode listet diesen Thread nur einmal auf.  
  
 Diese Methode stellt eine Liste der Threads des Prozesses ohne Duplikate dar. Verwenden Sie andernfalls die [enumthreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) -Methode, um die Threads aufzulisten, die in einem bestimmten Programm ausgeführt werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)

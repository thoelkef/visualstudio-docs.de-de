---
title: NotifyDebuggerOfWaitCompletion-Methode | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- NotifyDebuggerOfWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: 841c5908-4f3f-400b-a7b0-96a95f362817
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1288034f171c56e78f17d02f39843cf4ff600e5e
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/24/2018
ms.locfileid: "39233099"
---
# <a name="notifydebuggerofwaitcompletion-method"></a>NotifyDebuggerOfWaitCompletion-Methode
Platzhalter-Methode, die als Ziel der Haltepunkt vom Debugger verwendet. Diese Methode darf nicht inline oder optimiert sein.  
  
 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** "mscorlib" (in *"mscorlib.dll"*)  
  
## <a name="syntax"></a>Syntax  
  
```vb  
private void NotifyDebuggerOfWaitCompletion()  
```  
  
## <a name="remarks"></a>Hinweise  
 Alle Joinvorgänge mit einer Aufgabe sollten diese Methode aufrufen, wenn die Debugger-Notification-Bit festgelegt ist.  
  
## <a name="requirements"></a>Anforderungen  
  
## <a name="see-also"></a>Siehe auch  
 [Task-Klasse](../../extensibility/debugger/task-class-internal-members.md)
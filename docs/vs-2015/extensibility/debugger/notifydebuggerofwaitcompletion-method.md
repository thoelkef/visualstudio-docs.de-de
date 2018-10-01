---
title: NotifyDebuggerOfWaitCompletion-Methode | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- NotifyDebuggerOfWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: 841c5908-4f3f-400b-a7b0-96a95f362817
caps.latest.revision: 6
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4429b89be624960b787b51c3fa085f43e412889e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47512325"
---
# <a name="notifydebuggerofwaitcompletion-method"></a>NotifyDebuggerOfWaitCompletion-Methode
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [NotifyDebuggerOfWaitCompletion-Methode](https://docs.microsoft.com/visualstudio/extensibility/debugger/notifydebuggerofwaitcompletion-method).  
  
Platzhalter-Methode, die als Ziel der Haltepunkt vom Debugger verwendet. Diese Methode darf nicht inline oder optimiert sein.  
  
 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** "mscorlib" (in "mscorlib.dll")  
  
## <a name="syntax"></a>Syntax  
  
```vb  
private void NotifyDebuggerOfWaitCompletion()  
```  
  
## <a name="remarks"></a>Hinweise  
 Alle Joinvorgänge mit einer Aufgabe sollten diese Methode aufrufen, wenn die Debugger-Notification-Bit festgelegt ist.  
  
## <a name="requirements"></a>Anforderungen  
  
## <a name="see-also"></a>Siehe auch  
 [Aufgabenklasse](../../extensibility/debugger/task-class-internal-members.md)


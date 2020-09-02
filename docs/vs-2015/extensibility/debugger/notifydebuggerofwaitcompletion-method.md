---
title: Notifydebuggerofwaitcompletion-Methode | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- NotifyDebuggerOfWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: 841c5908-4f3f-400b-a7b0-96a95f362817
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bf0548e1e791c41d806ccc222176ee571b037389
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153726"
---
# <a name="notifydebuggerofwaitcompletion-method"></a>NotifyDebuggerOfWaitCompletion-Methode
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die Platzhalter Methode, die vom Debugger als Haltepunkt Ziel verwendet wird. Diese Methode darf nicht Inline oder optimiert sein.  
  
 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** mscorlib (in mscorlib.dll)  
  
## <a name="syntax"></a>Syntax  
  
```vb  
private void NotifyDebuggerOfWaitCompletion()  
```  
  
## <a name="remarks"></a>Bemerkungen  
 Alle joinvorgänge mit einer Aufgabe sollten diese Methode abrufen, wenn Ihr Debugger-Benachrichtigungs Bit festgelegt ist.  
  
## <a name="requirements"></a>Requirements (Anforderungen)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Task-Klasse](../../extensibility/debugger/task-class-internal-members.md)

---
title: SetNotificationForWaitCompletion-Methode | Microsoft-Dokumentation
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
- SetNotificationForWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: da149c9a-20f4-4543-a29e-429c8c1d2e19
caps.latest.revision: 6
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9b1443bbbd49216330d1df9978052bf4d10f7157
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47509012"
---
# <a name="setnotificationforwaitcompletion-method"></a>SetNotificationForWaitCompletion-Methode
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [SetNotificationForWaitCompletion-Methode](https://docs.microsoft.com/visualstudio/extensibility/debugger/setnotificationforwaitcompletion-method).  
  
Legt fest oder löscht das TASK_STATE_WAIT_COMPLETION_NOTIFICATION Zustand Bit.  
  
 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** "mscorlib" (in "mscorlib.dll")  
  
## <a name="syntax"></a>Syntax  
  
```vb  
internal void SetNotificationForWaitCompletion(bool enabled)  
```  
  
#### <a name="parameters"></a>Parameter  
 `enabled`  
  
 `true` Das Bit festgelegt `false` um die Festlegung der Bit.  
  
## <a name="exceptions"></a>Ausnahmen  
  
## <a name="remarks"></a>Hinweise  
 Der Debugger wird dieses Bit zur schrittweisen aus Text eine Async-Methode. Wenn `enabled` ist `true`, diese Methode muss aufgerufen werden, nur für eine Aufgabe, die noch nicht abgeschlossen wurde. Wenn `enabled` ist `false`, diese Methode kann für abgeschlossene Aufgaben aufgerufen werden. In jedem Fall sollten sie nur für Vorgänge des Promise-Stil verwendet werden.  
  
## <a name="requirements"></a>Anforderungen  
  
## <a name="see-also"></a>Siehe auch  
 [Aufgabenklasse](../../extensibility/debugger/task-class-internal-members.md)


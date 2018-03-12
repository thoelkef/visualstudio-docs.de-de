---
title: DEBUG_REASON | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DEBUG_REASON
helpviewer_keywords:
- DEBUG_REASON enumeration
ms.assetid: ad2ee898-8648-4671-9078-d32873862346
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: fda733db5a70d88d5029c4001c632c234d32a823
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="debugreason"></a>DEBUG_REASON
Gibt an, warum der Prozess zum Debuggen gestartet wurde.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
enum enum_DEBUG_REASON {  
   DEBUG_REASON_ERROR         = 0,  
   DEBUG_REASON_USER_LAUNCHED = 1,  
   DEBUG_REASON_USER_ATTACHED = 2,  
   DEBUG_REASON_AUTO_ATTACHED = 3,  
   DEBUG_REASON_CAUSALITY     = 4  
};  
typedef DWORD DEBUG_REASON;  
```  
  
```csharp  
public enum enum_DEBUG_REASON {  
   DEBUG_REASON_ERROR         = 0,  
   DEBUG_REASON_USER_LAUNCHED = 1,  
   DEBUG_REASON_USER_ATTACHED = 2,  
   DEBUG_REASON_AUTO_ATTACHED = 3,  
   DEBUG_REASON_CAUSALITY     = 4  
};  
```  
  
#### <a name="parameters"></a>Parameter  
 DEBUG_REASON_ERROR  
 Ein nicht-spezifische Fehler ist aufgetreten (wird verwendet, als eine standardbedingung Wenn keine der anderen Gründe, anpassen Warum).  
  
 DEBUG_REASON_USER_LAUNCHED  
 Der Prozess wurde auf Anforderung des Benutzers gestartet.  
  
 DEBUG_REASON_USER_ATTACHED  
 Der Prozess bereits ausgeführt wurde vom Benutzer zugeordnet.  
  
 DEBUG_REASON_AUTO_ATTACHED  
 Der Prozess wurde mit automatisch verbunden, wenn er gestartet wurde.  
  
 DEBUG_REASON_CAUSALITY  
 Der Prozess wurde gestartet, aufgrund einer *Just-in-Time* debugging (JIT)-Ereignis.  
  
## <a name="remarks"></a>Hinweise  
 Zurückgegeben von der [GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md) Methode.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)
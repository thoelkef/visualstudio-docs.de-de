---
title: DEBUG_REASON | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- DEBUG_REASON
helpviewer_keywords:
- DEBUG_REASON enumeration
ms.assetid: ad2ee898-8648-4671-9078-d32873862346
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 95a537c703d4afd68bb291205e0c7da8d9b8fc59
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68143011"
---
# <a name="debug_reason"></a>DEBUG_REASON
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Gibt an, warum der Prozess zum Debuggen gestartet wurde.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
enum enum_DEBUG_REASON {  
   DEBUG_REASON_ERROR         = 0,  
   DEBUG_REASON_USER_LAUNCHED = 1,  
   DEBUG_REASON_USER_ATTACHED = 2,  
   DEBUG_REASON_AUTO_ATTACHED = 3,  
   DEBUG_REASON_CAUSALITY     = 4  
};  
typedef DWORD DEBUG_REASON;  
```  
  
```csharp  
public enum enum_DEBUG_REASON {  
   DEBUG_REASON_ERROR         = 0,  
   DEBUG_REASON_USER_LAUNCHED = 1,  
   DEBUG_REASON_USER_ATTACHED = 2,  
   DEBUG_REASON_AUTO_ATTACHED = 3,  
   DEBUG_REASON_CAUSALITY     = 4  
};  
```  
  
#### <a name="parameters"></a>Parameter  
 DEBUG_REASON_ERROR  
 Ein nicht spezifischer Fehler ist aufgetreten (Dies wird als Standard Bedingung verwendet, wenn keiner der anderen Gründe passt).  
  
 DEBUG_REASON_USER_LAUNCHED  
 Der Prozess wurde bei der Anforderung des Benutzers gestartet.  
  
 DEBUG_REASON_USER_ATTACHED  
 Der Benutzer hat den bereits laufenden Prozess angefügt.  
  
 DEBUG_REASON_AUTO_ATTACHED  
 Der Prozess wurde beim Starten automatisch an angefügt.  
  
 DEBUG_REASON_CAUSALITY  
 Der Prozess wurde aufgrund eines JIT-Debugereignisses ( *Just-in-Time* ) gestartet.  
  
## <a name="remarks"></a>Bemerkungen  
 Wird von der [getdebugreason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md) -Methode zurückgegeben.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Weitere Informationen  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)

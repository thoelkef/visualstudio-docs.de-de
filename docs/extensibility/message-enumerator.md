---
title: Nachricht Enumerator | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- message enumerator
- source control plug-ins, message enumeration
ms.assetid: 4a4faa0d-d352-40ea-a21d-c09ea286a8e1
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 6a24db9c50bd298f068c23af0b6bad5755ec252d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="message-enumerator"></a>Message-Enumerator
Folgende Flags werden verwendet, für die `TEXTOUTPROC` Funktion, die eine Rückruffunktion, die die IDE beim Aufrufen bietet der [SccOpenProject](../extensibility/sccopenproject-function.md) (finden Sie unter [LPTEXTOUTPROC](../extensibility/lptextoutproc.md) Einzelheiten zu den Rückruf (Funktion).  
  
 Die IDE gestellt, um den Prozess abzubrechen, erhalten sie möglicherweise eine der Meldungen "Abbrechen". In diesem Fall die Quelle-Plug-in verwendet steuern `SCC_MSG_STARTCANCEL` , Fragen Sie die IDE anzuzeigen die **"Abbrechen"** Schaltfläche. Hiernach kann einen beliebigen Satz von normalen Nachrichten gesendet werden. Wenn keines dieser gibt `SCC_MSG_RTN_CANCEL`, und klicken Sie dann das plug-in wird den Vorgang beendet und gibt zurück. Das plug-in auch fragt `SCC_MSG_DOCANCEL` in regelmäßigen Abständen, um festzustellen, ob der Benutzer den Vorgang abgebrochen wurde. Wenn alle Vorgänge ausgeführt werden, oder wenn der Benutzer abgebrochen wurde, das plug-in sendet `SCC_MSG_STOPCANCEL`. Die `SCC_MSG_INFO`, SCC_MSG_WARNING, und SCC_MSG_ERROR Typen dienen für Nachrichten, die in der bildlauffähigen Liste mit Nachrichten angezeigt werden sollen. `SCC_MSG_STATUS`ist ein spezieller Typ, der angibt, dass der Text in einer Statusleiste oder temporäre Anzeigebereich angezeigt sollten. Es nicht dauerhaft bleiben in der Liste.  
  
## <a name="syntax"></a>Syntax  
  
```  
enum {   
   SCC_MSG_RTN_CANCEL = -1,   
   SCC_MSG_RTN_OK = 0,   
   SCC_MSG_INFO = 1   
   SCC_MSG_WARNING,   
   SCC_MSG_ERROR,   
   SCC_MSG_STATUS,   
   SCC_MSG_DOCANCEL,   
   SCC_MSG_STARTCANCEL,   
   SCC_MSG_STOPCANCEL   
};  
```  
  
## <a name="members"></a>Member  
 SCC_MSG_RTN_CANCEL  
 Zurückgeben von Rückruf an, dass "Abbrechen".  
  
 SCC_MSG_RTN_OK  
 Zurückgeben von Rückruf, um den Vorgang fortzusetzen.  
  
 SCC_MSG_INFO  
 Meldung dient nur zu Informationszwecken.  
  
 SCC_MSG_WARNING  
 Nachricht ist eine Warnung.  
  
 SCC_MSG_ERROR  
 Nachricht ist ein Fehler.  
  
 SCC_MSG_STATUS  
 Nachricht ist für die Statusleiste vorgesehen.  
  
 SCC_MSG_DOCANCEL  
 Kein Text; Gibt IDE `SCC_MSG_RTN_OK` oder `SCC_MSG_RTN_CANCEL`.  
  
 SCC_MSG_STARTCANCEL  
 Startet eine Schleife "Abbrechen".  
  
 SCC_MSG_STOPCANCEL  
 Beendet die Schleife "Abbrechen".  
  
## <a name="see-also"></a>Siehe auch  
 [Datenquellen-Steuerelement-Plug-ins](../extensibility/source-control-plug-ins.md)   
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)
---
title: Message-Enumerator | Microsoft-Dokumentation
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
- message enumerator
- source control plug-ins, message enumeration
ms.assetid: 4a4faa0d-d352-40ea-a21d-c09ea286a8e1
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 374881ecfe7af76b4d5aed3c6ae56b64094406fa
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47509279"
---
# <a name="message-enumerator"></a>Meldungsenumerator
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Meldungsenumerator](https://docs.microsoft.com/visualstudio/extensibility/message-enumerator).  
  
Folgende Flags werden verwendet, für die `TEXTOUTPROC` Funktion, die eine Rückruffunktion, die die IDE beim Aufrufen bietet der [SccOpenProject](../extensibility/sccopenproject-function.md) (finden Sie unter [LPTEXTOUTPROC](../extensibility/lptextoutproc.md) ausführliche Informationen über den Rückruf (Funktion).  
  
 Wenn die IDE gestellt wird, um den Prozess abzubrechen, erhalten sie möglicherweise eine der Meldungen "Abbrechen". In diesem Fall die Quelle-Plug-in verwendet steuern `SCC_MSG_STARTCANCEL` stellen die IDE zum Anzeigen der **Abbrechen** Schaltfläche. Danach kann eine beliebige Anzahl von normalen Nachrichten gesendet werden. Wenn eine der folgenden gibt `SCC_MSG_RTN_CANCEL`, und klicken Sie dann den Vorgang beendet und gibt. Das plug-in fragt auch `SCC_MSG_DOCANCEL` regelmäßig, um zu bestimmen, ob der Benutzer den Vorgang abgebrochen wurde. Wenn alle Vorgänge werden ausgeführt, oder wenn der Benutzer abgebrochen, das plug-in sendet `SCC_MSG_STOPCANCEL`. Die `SCC_MSG_INFO`, SCC_MSG_WARNING, und SCC_MSG_ERROR Typen werden verwendet, für Nachrichten, die in der scrollliste von Nachrichten angezeigt werden. `SCC_MSG_STATUS` ist ein spezieller Typ, der angibt, dass der Text in einer Statusleiste oder temporären Anzeigebereichs angezeigt werden sollen. Es wird jedoch nicht dauerhaft in der Liste weiterhin.  
  
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
 Kein Text; IDE gibt `SCC_MSG_RTN_OK` oder `SCC_MSG_RTN_CANCEL`.  
  
 SCC_MSG_STARTCANCEL  
 Startet eine "Abbrechen"-Schleife.  
  
 SCC_MSG_STOPCANCEL  
 Die "Abbrechen"-Schleife wird beendet.  
  
## <a name="see-also"></a>Siehe auch  
 [Quellcodeverwaltungs-Plug-ins](../extensibility/source-control-plug-ins.md)   
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)


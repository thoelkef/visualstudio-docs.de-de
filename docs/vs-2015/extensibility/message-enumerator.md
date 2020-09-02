---
title: Nachrichtenenumerator | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- message enumerator
- source control plug-ins, message enumeration
ms.assetid: 4a4faa0d-d352-40ea-a21d-c09ea286a8e1
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6bd42c825cd45068e13178856e524268b426ec53
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194338"
---
# <a name="message-enumerator"></a>Meldungsenumerator
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die folgenden Flags werden für die- `TEXTOUTPROC` Funktion verwendet, bei der es sich um eine Rückruffunktion handelt, die die IDE beim Aufrufen von [sccopenproject](../extensibility/sccopenproject-function.md) bereitstellt (Weitere Informationen zur Rückruffunktion finden Sie unter [lptextoutproc](../extensibility/lptextoutproc.md) ).  
  
 Wenn die IDE aufgefordert wird, den Prozess abzubrechen, erhält Sie möglicherweise eine der Abbruch Nachrichten. In diesem Fall verwendet das Quellcodeverwaltungs-Plug-in `SCC_MSG_STARTCANCEL` , um die IDE zum Anzeigen der Schaltfläche **Abbrechen** aufzufordern. Danach können alle normalen Nachrichten gesendet werden. Wenn eine dieser zurückgibt `SCC_MSG_RTN_CANCEL` , beendet das Plug-in den Vorgang und gibt zurück. Das Plug-in fragt auch `SCC_MSG_DOCANCEL` regelmäßig ab, ob der Benutzer den Vorgang abgebrochen hat. Wenn alle Vorgänge abgeschlossen sind, oder wenn der Benutzer abgebrochen wurde, sendet das Plug-in `SCC_MSG_STOPCANCEL` . Die `SCC_MSG_INFO` Typen, SCC_MSG_WARNING und SCC_MSG_ERROR werden für Nachrichten verwendet, die in der scrollliste der Nachrichten angezeigt werden. `SCC_MSG_STATUS` ein spezieller Typ, der angibt, dass der Text in einer Statusleiste oder einem temporären Anzeigebereich angezeigt werden soll. Er bleibt nicht dauerhaft in der Liste.  
  
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
 Rückgabe von Callback, um den Abbruch anzugeben.  
  
 SCC_MSG_RTN_OK  
 Rückgabe von Rückruf zum Fortfahren.  
  
 SCC_MSG_INFO  
 Die Meldung ist "Information".  
  
 SCC_MSG_WARNING  
 Die Meldung ist eine Warnung.  
  
 SCC_MSG_ERROR  
 Die Meldung ist ein Fehler.  
  
 SCC_MSG_STATUS  
 Die Nachricht ist für die Statusleiste vorgesehen.  
  
 SCC_MSG_DOCANCEL  
 Kein Text; IDE gibt `SCC_MSG_RTN_OK` oder zurück `SCC_MSG_RTN_CANCEL` .  
  
 SCC_MSG_STARTCANCEL  
 Startet eine Abbruch Schleife.  
  
 SCC_MSG_STOPCANCEL  
 Beendet die Abbruch Schleife.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Quellcodeverwaltungs-Plug-ins](../extensibility/source-control-plug-ins.md)   
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)

---
title: "Message-Enumerator | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Message-enumerator"
  - "Source Control-Plug-ins Nachricht-enumeration"
ms.assetid: 4a4faa0d-d352-40ea-a21d-c09ea286a8e1
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Message-Enumerator
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Folgende Flags werden verwendet, für die `TEXTOUTPROC` \-Funktion, die eine Callback\-Funktion, die die IDE beim Aufrufen bietet der [SccOpenProject](../extensibility/sccopenproject-function.md) \(finden Sie unter [LPTEXTOUTPROC](../extensibility/lptextoutproc.md) ausführliche Informationen über die Callback\-Funktion\).  
  
 Wenn die IDE gestellt wird, um den Vorgang abzubrechen, kann es einen Abbrechen Nachrichten erhalten. In diesem Fall die Quellcode\-Plug\-in verwendet `SCC_MSG_STARTCANCEL` Fragen die IDE zum Anzeigen der **Abbrechen** Schaltfläche. Danach kann eine beliebige Anzahl von normale Nachrichten gesendet werden. Wenn eine der folgenden gibt `SCC_MSG_RTN_CANCEL`, das plug\-in wird den Vorgang beendet und gibt zurück. Das plug\-in auch fragt `SCC_MSG_DOCANCEL` in regelmäßigen Abständen, um festzustellen, ob den Vorgang wurde vom Benutzer abgebrochen wurde. Wenn alle Vorgänge erfolgen, oder wenn der Benutzer abgebrochen, das plug\-in sendet `SCC_MSG_STOPCANCEL`. Die `SCC_MSG_INFO`, SCC\_MSG\_WARNING, und SCC\_MSG\_ERROR Typen dienen für Nachrichten, die in der Liste von Nachrichten mit Bildlaufleiste angezeigt.`SCC_MSG_STATUS` ist ein spezieller Typ, der angibt, dass der Text in einer Statusleiste oder temporäre Anzeigebereich angezeigt werden sollen. Es nicht dauerhaft in der Liste verbleiben.  
  
## Syntax  
  
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
  
## Mitglieder  
 SCC\_MSG\_RTN\_CANCEL  
 Zurückgeben von Rückruf Abbrechen an.  
  
 SCC\_MSG\_RTN\_OK  
 Zurückgeben von Rückruf, um den Vorgang fortzusetzen.  
  
 SCC\_MSG\_INFO  
 Meldung dient nur zu Informationszwecken.  
  
 SCC\_MSG\_WARNING  
 Nachricht ist eine Warnung.  
  
 SCC\_MSG\_ERROR  
 Nachricht ist ein Fehler.  
  
 SCC\_MSG\_STATUS  
 Nachricht ist für die Statusleiste vorgesehen.  
  
 SCC\_MSG\_DOCANCEL  
 Kein Text. IDE gibt `SCC_MSG_RTN_OK` oder `SCC_MSG_RTN_CANCEL`.  
  
 SCC\_MSG\_STARTCANCEL  
 Startet eine Schleife abbrechen.  
  
 SCC\_MSG\_STOPCANCEL  
 Beendet die Schleife abbrechen.  
  
## Siehe auch  
 [Source Control\-Plug\-ins](../extensibility/source-control-plug-ins.md)   
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)
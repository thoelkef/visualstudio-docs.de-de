---
title: Nachrichtenenumerator | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- message enumerator
- source control plug-ins, message enumeration
ms.assetid: 4a4faa0d-d352-40ea-a21d-c09ea286a8e1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0e09b72bd228839268cffc228dd0dc503cc82bd9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702508"
---
# <a name="message-enumerator"></a>Nachrichtenenumerator
Die folgenden Flags werden `TEXTOUTPROC` für die Funktion verwendet, bei der es sich um eine Rückruffunktion handelt, die die IDE beim Aufrufen des [SccOpenProject](../extensibility/sccopenproject-function.md) bereitstellt (Details zur Rückruffunktion finden Sie unter [LPTEXTOUTPROC).](../extensibility/lptextoutproc.md)

 Wenn die IDE aufgefordert wird, den Vorgang abzubrechen, erhält sie möglicherweise eine der Abbruchnachrichten. In diesem Fall wird `SCC_MSG_STARTCANCEL` die Schaltfläche Abbrechen im Quellcodeverwaltungs-Plug-In verwendet, um die IDE aufzufordern, die Schaltfläche **Abbrechen** anzuzeigen. Danach können alle normalen Nachrichten gesendet werden. Wenn einer dieser `SCC_MSG_RTN_CANCEL`Ergebnisse zurückkehrt, beendet das Plug-In den Vorgang und gibt zurück. Das Plug-In `SCC_MSG_DOCANCEL` fragt auch regelmäßig ab, um festzustellen, ob der Benutzer den Vorgang abgebrochen hat. Wenn alle Vorgänge ausgeführt sind oder der Benutzer abgebrochen `SCC_MSG_STOPCANCEL`hat, sendet das Plug-In . Die `SCC_MSG_INFO`Typen , SCC_MSG_WARNING und SCC_MSG_ERROR werden für Nachrichten verwendet, die in der Bildlaufliste der Nachrichten angezeigt werden. `SCC_MSG_STATUS`ist ein spezieller Typ, der angibt, dass der Text in einer Statusleiste oder einem temporären Anzeigebereich angezeigt werden soll. Sie bleibt nicht dauerhaft in der Liste.

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
 SCC_MSG_RTN_CANCEL Zurück vom Rückruf, um den Abbruch anzuzeigen.

 SCC_MSG_RTN_OK Return from callback fort.

 SCC_MSG_INFO Nachricht ist informational.

 SCC_MSG_WARNING Nachricht ist eine Warnung.

 SCC_MSG_ERROR Meldung ist ein Fehler.

 SCC_MSG_STATUS Nachricht ist für die Statusleiste gedacht.

 SCC_MSG_DOCANCEL Kein Text; IDE `SCC_MSG_RTN_OK` gibt `SCC_MSG_RTN_CANCEL`zurück oder .

 SCC_MSG_STARTCANCEL Startet eine Abbruchschleife.

 SCC_MSG_STOPCANCEL Stoppt die Abbruchschleife.

## <a name="see-also"></a>Weitere Informationen
- [Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-ins.md)
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)

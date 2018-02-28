---
title: LPTEXTOUTPROC | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- LPTEXTOUTPROC
helpviewer_keywords:
- SccMsgDataOnMessage structure
- SccMsgDataOnBeforeGetFile structure
- SccMsgDataIsCancelled structure
- LPTEXTOUTPROC callback function
- SccMsgDataOnAfterGetFile structure
ms.assetid: 2025c969-e3c7-4cf4-a5c5-099d342895ea
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 9fb212d7908d32bc9d9d14d7e8f4786089bc5f89
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="lptextoutproc"></a>LPTEXTOUTPROC
Wenn der Benutzer eine Quelle-Steuerungsvorgang aus innerhalb der integrierten Entwicklungsumgebung (IDE) ausgeführt wird, sollten die Datenquellen-Steuerelements, das Plug-in-Fehler oder Status-Nachrichten, die im Zusammenhang mit dem Betrieb zu vermitteln. Das plug-in kann einen eigenen Meldungsfelder für diesen Zweck angezeigt. Allerdings können für weitere nahtlose Integration, das plug-in Zeichenfolgen an der IDE übergeben, die klicken Sie dann auf die systemeigene Weise zum Anzeigen von Statusinformationen werden angezeigt. Der Mechanismus dafür ist die `LPTEXTOUTPROC` -Funktionszeiger. Die IDE implementiert diese Funktion (im folgenden ausführlicher beschrieben) für die Anzeige von Fehler- und statusmeldungen.  
  
 Die IDE übergibt der quellcodeverwaltung-Plug-in einen Funktionszeiger an diese Funktion als der `lpTextOutProc` Parameter beim Aufrufen der [SccOpenProject](../extensibility/sccopenproject-function.md). Während einer SCC-Operation, z. B. in der Mitte einen Aufruf der [SccGet](../extensibility/sccget-function.md) im Zusammenhang mit vielen Dateien, die-Plug-in Aufrufen der `LPTEXTOUTPROC` -Funktion, in regelmäßigen Abständen übergeben von Zeichenfolgen angezeigt. Diese Zeichenfolgen kann eine Statusleiste, in einem Fenster "Ausgabe" oder in einem separaten Meldungsfeld entsprechend der IDE angezeigt. Optional die IDE möglicherweise zur Anzeige bestimmter Meldungen mit einem **"Abbrechen"** Schaltfläche. Dadurch kann der Benutzer den Vorgang abbrechen, und es bietet der IDE auf die Möglichkeit, diese Informationen an das plug-in übergeben.  
  
## <a name="signature"></a>Signatur  
 Die IDE Ausgabe, dass die Funktion die folgende Signatur verfügt:  
  
```cpp  
typedef LONG (*LPTEXTOUTPROC) (  
   LPSTR display_string,  
   LONG mesg_type  
);  
```  
  
## <a name="parameters"></a>Parameter  
 display_string  
 Eine Textzeichenfolge angezeigt. Diese Zeichenfolge sollte nicht mit einem Wagenrücklauf zurückgegeben oder eine Line feed, Wagenrücklauf enden.  
  
 mesg_type  
 Der Typ der Meldung. Die folgende Tabelle enthält die unterstützten Werte für diesen Parameter.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`SCC_MSG_INFO, SCC_MSG_WARNING, SCC_MSG_ERROR`|Die Nachricht gilt als Information, Warnung oder Fehler.|  
|`SCC_MSG_STATUS`|Die Nachricht zeigt Status und kann in der Statusleiste angezeigt werden.|  
|`SCC_MSG_DOCANCEL`|Bei der keine Meldungszeichenfolge gesendet.|  
|`SCC_MSG_STARTCANCEL`|Anzeigen von beginnt ein **"Abbrechen"** Schaltfläche.|  
|`SCC_MSG_STOPCANCEL`|Anzeigen von beendet eine **"Abbrechen"** Schaltfläche.|  
|`SCC_MSG_BACKGROUND_IS_CANCELLED`|IDE gefragt werden, wenn der Hintergrundvorgang abgebrochen werden, ist: IDE gibt `SCC_MSG_RTN_CANCEL` Wenn der Vorgang abgebrochen wurde; andernfalls wird `SCC_MSG_RTN_OK`. Die `display_string` Parameter umgewandelt wird, als ein [SccMsgDataIsCancelled](#LinkSccMsgDataIsCancelled) -Struktur, die durch die quellcodeverwaltung-Plug-in bereitgestellt wird.|  
|`SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE`|Weist die IDE zu einer Datei an, bevor sie in der Versionskontrolle abgerufen werden. Die `display_string` Parameter umgewandelt wird, als ein [SccMsgDataOnBeforeGetFile](#LinkSccMsgDataOnBeforeGetFile) -Struktur, die durch die quellcodeverwaltung-Plug-in bereitgestellt wird.|  
|`SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE`|Weist die IDE zu einer Datei an, nachdem er in der Versionskontrolle abgerufen wurden. Die `display_string` Parameter umgewandelt wird, als ein [SccMsgDataOnAfterGetFile](#LinkSccMsgDataOnAfterGetFile) -Struktur, die durch die quellcodeverwaltung-Plug-in bereitgestellt wird.|  
|`SCC_MSG_BACKGROUND_ON_MESSAGE`|Weist die IDE mit dem aktuellen Status eines Vorgangs im Hintergrund. Die `display_string` Parameter umgewandelt wird, als ein [SccMsgDataOnMessage](#LinkSccMsgDataOnMessage) -Struktur, die durch die quellcodeverwaltung-Plug-in bereitgestellt wird.|  
  
## <a name="return-value"></a>Rückgabewert  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|SCC_MSG_RTN_OK|Die Zeichenfolge angezeigt wurde, oder der Vorgang erfolgreich abgeschlossen wurde.|  
|SCC_MSG_RTN_CANCEL|Der Benutzer möchte den Vorgang abzubrechen.|  
  
## <a name="example"></a>Beispiel  
 Nehmen Sie die IDE-Aufrufe an die [SccGet](../extensibility/sccget-function.md) mit 20 Dateinamen. Die Datenquellen-Steuerelement-Plug-in möchte zu verhindern, dass durch das Abbrechen des Vorgangs in der Mitte einer Datei abrufen. Nach dem Abrufen von jeder Datei, ruft er `lpTextOutProc`, übergeben sie die Statusinformationen für jede Datei und sendet eine `SCC_MSG_DOCANCEL` Nachricht, falls sie kein Status gemeldet hat. Wenn zu einem beliebigen Zeitpunkt das plug-in einen Rückgabewert von empfängt `SCC_MSG_RTN_CANCEL` aus der IDE es Get bricht den Vorgang ab sofort damit, dass keine weiteren Dateien abgerufen werden.  
  
## <a name="structures"></a>Strukturen  
  
###  <a name="LinkSccMsgDataIsCancelled"></a>SccMsgDataIsCancelled  
  
```cpp  
typedef struct {  
   DWORD dwBackgroundOperationID;  
} SccMsgDataIsCancelled;  
```  
  
 Diese Struktur wird gesendet, mit der `SCC_MSG_BACKGROUND_IS_CANCELLED` Nachricht. Es wird verwendet, um die ID des Hintergrundvorgangs im zu kommunizieren, die abgebrochen wurde.  
  
###  <a name="LinkSccMsgDataOnBeforeGetFile"></a>SccMsgDataOnBeforeGetFile  
  
```cpp  
typedef struct {  
   DWORD dwBackgroundOperationID;  
   PCSTR szFile;  
} SccMsgDataOnBeforeGetFile;  
```  
  
 Diese Struktur wird gesendet, mit der `SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE` Nachricht. Es wird zur Kommunikation der Name der Datei abgerufen werden sollen und die ID des Hintergrundvorgangs im, die das Abrufen von auf diese Weise wird verwendet.  
  
###  <a name="LinkSccMsgDataOnAfterGetFile"></a>SccMsgDataOnAfterGetFile  
  
```cpp  
typedef struct {  
   DWORD dwBackgroundOperationID;  
   PCSTR szFile;  
   SCCRTN sResult;  
} SccMsgDataOnAfterGetFile;  
```  
  
 Diese Struktur wird gesendet, mit der `SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE` Nachricht. Es wird zur Kommunikation des Ergebnis zum Abrufen der angegebenen Datei als auch die ID des Hintergrundvorgangs im, die das Abrufen wurde verwendet. Siehe die Rückgabewerte für die [SccGet](../extensibility/sccget-function.md) für was daher gewährt werden können.  
  
###  <a name="LinkSccMsgDataOnMessage"></a>SccMsgDataOnMessage  
 [C++]  
  
```  
typedef struct {  
   DWORD dwBackgroundOperationID;  
   PCSTR szMessage;  
   BOOL bIsError;  
} SccMsgDataOnMessage;  
```  
  
 Diese Struktur wird gesendet, mit der `SCC_MSG_BACKGROUND_ON_MESSAGE` Nachricht. Es wird verwendet, um den aktuellen Status eines Vorgangs im Hintergrund zu kommunizieren. Der Status wird als eine Zeichenfolge, die von der IDE angezeigt werden und `bIsError` gibt den Schweregrad der Meldung (`TRUE` für eine Fehlermeldung; `FALSE` für eine Warnung oder eine informative Meldung). Die ID des Hintergrundvorgangs senden den Status wird auch zugewiesen.  
  
## <a name="code-example"></a>Codebeispiel  
 Hier ist ein kurzes Beispiel eines Aufrufs `LPTEXTOUTPROC` zum Senden der `SCC_MSG_BACKGROUND_ON_MESSAGE` Nachricht, die zeigt, wie die Struktur für den Aufruf umgewandelt.  
  
```cpp  
LONG SendStatusMessage(  
    LPTEXTOUTPROC pTextOutProc,  
    DWORD         dwBackgroundID,  
    LPCTSTR       pStatusMsg,  
    BOOL          bIsError)  
{  
    SccMsgDataOnMessage msgData = { 0 };  
    LONG                result  = 0;  
  
    msgData.dwBackgroundOperationID = dwBackgroundID;  
    msgData.szMessage               = pStatusMsg;  
    msgData.bIsError                = bIsError;  
  
    result = pTextOutProc(reinterpret_cast<LPCTSTR>(&msgData), SCC_MSG_BACKGROUND_ON_MESSAGE);  
    return result;  
}  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Rückruffunktionen implementiert, die von der IDE](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-ins.md)
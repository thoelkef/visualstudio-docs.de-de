---
title: LPTEXTOUTPROC | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- LPTEXTOUTPROC
helpviewer_keywords:
- SccMsgDataOnMessage structure
- SccMsgDataOnBeforeGetFile structure
- SccMsgDataIsCancelled structure
- LPTEXTOUTPROC callback function
- SccMsgDataOnAfterGetFile structure
ms.assetid: 2025c969-e3c7-4cf4-a5c5-099d342895ea
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f14942ffd59ce2c6eacf7da2d0d1ab252d58e2cb
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60100507"
---
# <a name="lptextoutproc"></a>LPTEXTOUTPROC
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn der Benutzer einen Quellcodeverwaltungsvorgang von innerhalb der integrierten Entwicklungsumgebung (IDE) ausgeführt wird, sollten das Quellcodeverwaltungs-Plug-Ins Fehler oder Status-Meldungen, die im Zusammenhang mit der Operation zu vermitteln. Das plug-in kann eine eigene Meldungsfeldern zu diesem Zweck werden angezeigt. Allerdings können für die weitere nahtlose Integration der Plug-in-Zeichenfolgen der IDE übergeben, die klicken Sie dann auf native Weise zum Anzeigen von Statusinformationen werden angezeigt. Der Mechanismus hierfür ist die `LPTEXTOUTPROC` Funktionszeiger. Die IDE implementiert diese Funktion, die (im folgenden ausführlicher beschrieben), für die Anzeige von Fehler- und statusmeldungen.  
  
 Die IDE übergibt und der Quellcode-Plug-in einen Funktionszeiger zu dieser Funktion, als die `lpTextOutProc` Parameter beim Aufrufen der [SccOpenProject](../extensibility/sccopenproject-function.md). Während eines SCC-Vorgangs, z. B. in der Mitte einen Aufruf der [SccGet](../extensibility/sccget-function.md) im Zusammenhang mit vielen Dateien, die-Plug-in Aufrufen der `LPTEXTOUTPROC` Funktion, die in regelmäßigen Abständen übergeben von Zeichenfolgen, die zum Anzeigen. Diese Zeichenfolgen möglicherweise eine Statusleiste, die in einem Fenster "Ausgabe" oder in einem separaten Meldungsfeld, entsprechend der IDE angezeigt. Optional die IDE möglicherweise können Sie bestimmte Nachrichten mit einem **Abbrechen** Schaltfläche. Dadurch kann der Benutzer, den Vorgang abzubrechen, und es bietet der IDE auf die Möglichkeit, diese Informationen zurück an das plug-in übergeben.  
  
## <a name="signature"></a>Signatur  
 Die IDE Ausgabe, dass die Funktion die folgende Signatur verfügt:  
  
```cpp#  
typedef LONG (*LPTEXTOUTPROC) (  
   LPSTR display_string,  
   LONG mesg_type  
);  
```  
  
## <a name="parameters"></a>Parameter  
 display_string  
 Eine Textzeichenfolge angezeigt. Diese Zeichenfolge sollte nicht mit einem Wagenrücklauf zurück oder einen Zeilenvorschub beendet werden.  
  
 mesg_type  
 Der Typ der Meldung. Die folgende Tabelle enthält die unterstützten Werte für diesen Parameter an.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`SCC_MSG_INFO, SCC_MSG_WARNING, SCC_MSG_ERROR`|Die Nachricht gilt als Information, Warnung oder Fehler.|  
|`SCC_MSG_STATUS`|Die Nachricht wird angezeigt und kann in der Statusleiste angezeigt werden.|  
|`SCC_MSG_DOCANCEL`|Mit der keine Zeichenfolge gesendet.|  
|`SCC_MSG_STARTCANCEL`|Beginnt die Anzeige einer **Abbrechen** Schaltfläche.|  
|`SCC_MSG_STOPCANCEL`|Beendet die Anzeige einer **Abbrechen** Schaltfläche.|  
|`SCC_MSG_BACKGROUND_IS_CANCELLED`|Fordert IDE, wenn der Vorgang im Hintergrund ist, abgebrochen werden soll: IDE gibt `SCC_MSG_RTN_CANCEL` Wenn der Vorgang abgebrochen wurde; andernfalls `SCC_MSG_RTN_OK`. Die `display_string` als Parameter umgewandelt wird ein [SccMsgDataIsCancelled](#LinkSccMsgDataIsCancelled) -Struktur, die durch das Quellcodeverwaltungs-Plug-in bereitgestellt wird.|  
|`SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE`|Teilt die IDE zu einer Datei an, bevor sie von der Versionskontrolle abgerufen werden. Die `display_string` als Parameter umgewandelt wird ein [SccMsgDataOnBeforeGetFile](#LinkSccMsgDataOnBeforeGetFile) -Struktur, die durch das Quellcodeverwaltungs-Plug-in bereitgestellt wird.|  
|`SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE`|Weist Sie die IDE zu einer Datei, nachdem sie aus der Versionskontrolle abgerufen wurde. Die `display_string` als Parameter umgewandelt wird ein [SccMsgDataOnAfterGetFile](#LinkSccMsgDataOnAfterGetFile) -Struktur, die durch das Quellcodeverwaltungs-Plug-in bereitgestellt wird.|  
|`SCC_MSG_BACKGROUND_ON_MESSAGE`|Teilt die IDE mit dem aktuellen Status eines Hintergrundvorgangs. Die `display_string` als Parameter umgewandelt wird ein [SccMsgDataOnMessage](#LinkSccMsgDataOnMessage) -Struktur, die durch das Quellcodeverwaltungs-Plug-in bereitgestellt wird.|  
  
## <a name="return-value"></a>Rückgabewert  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|SCC_MSG_RTN_OK|Die Zeichenfolge angezeigt wurde, oder der Vorgang erfolgreich abgeschlossen wurde.|  
|SCC_MSG_RTN_CANCEL|Der Benutzer möchte den Vorgang abzubrechen.|  
  
## <a name="example"></a>Beispiel  
 Nehmen Sie die IDE-Aufrufe an die [SccGet](../extensibility/sccget-function.md) mit 20 Dateinamen. Möchte, dass das Quellcodeverwaltungs-Plug-in zu verhindern, dass der Vorgang in der Mitte einer Datei Get abgebrochen wird. Nach dem Abrufen von jeder Datei, ruft `lpTextOutProc`, übergeben sie die Statusinformationen für jede Datei und sendet eine `SCC_MSG_DOCANCEL` Nachricht, wenn es kein Status gemeldet wurde. Wenn zu einem beliebigen Zeitpunkt das plug-in einen Rückgabewert von empfängt `SCC_MSG_RTN_CANCEL` aus der IDE sie Get-Vorgang abgebrochen wird sofort, damit keine Dateien mehr abgerufen werden.  
  
## <a name="structures"></a>Strukturen  
  
### <a name="LinkSccMsgDataIsCancelled"></a> SccMsgDataIsCancelled  
  
```cpp#  
typedef struct {  
   DWORD dwBackgroundOperationID;  
} SccMsgDataIsCancelled;  
```  
  
 Diese Struktur wird gesendet, mit der `SCC_MSG_BACKGROUND_IS_CANCELLED` Nachricht. Es wird verwendet, um die ID der der Vorgang im Hintergrund zu kommunizieren, das abgebrochen wurde.  
  
### <a name="LinkSccMsgDataOnBeforeGetFile"></a> SccMsgDataOnBeforeGetFile  
  
```cpp#  
typedef struct {  
   DWORD dwBackgroundOperationID;  
   PCSTR szFile;  
} SccMsgDataOnBeforeGetFile;  
```  
  
 Diese Struktur wird gesendet, mit der `SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE` Nachricht. Es wird zum Kommunizieren der Name der Datei abgerufen werden sollen und die ID der der Vorgang im Hintergrund, der das Abrufen von durchführt.  
  
### <a name="LinkSccMsgDataOnAfterGetFile"></a> SccMsgDataOnAfterGetFile  
  
```cpp#  
typedef struct {  
   DWORD dwBackgroundOperationID;  
   PCSTR szFile;  
   SCCRTN sResult;  
} SccMsgDataOnAfterGetFile;  
```  
  
 Diese Struktur wird gesendet, mit der `SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE` Nachricht. Es wird verwendet, um das Ergebnis vom Abrufen der angegebenen Datei als auch die ID der der Vorgang im Hintergrund, die das Abrufen von zu kommunizieren. Finden Sie unter die Rückgabewerte für die [SccGet](../extensibility/sccget-function.md) für was daher angegeben werden kann.  
  
### <a name="LinkSccMsgDataOnMessage"></a> SccMsgDataOnMessage  
 [C++]  
  
```  
typedef struct {  
   DWORD dwBackgroundOperationID;  
   PCSTR szMessage;  
   BOOL bIsError;  
} SccMsgDataOnMessage;  
```  
  
 Diese Struktur wird gesendet, mit der `SCC_MSG_BACKGROUND_ON_MESSAGE` Nachricht. Es wird verwendet, um den aktuellen Status eines Hintergrundvorgangs zu kommunizieren. Der Status wird angegeben, wie eine Zeichenfolge, die von der IDE angezeigt werden soll und `bIsError` gibt den Schweregrad der Meldung (`TRUE` für eine Fehlermeldung, `FALSE` für eine Warnung oder informationsmeldung). Die ID des Hintergrundvorgangs senden den Status wird auch zugewiesen.  
  
## <a name="code-example"></a>Codebeispiel  
 Hier ist ein kurzes Beispiel des Aufrufs `LPTEXTOUTPROC` zum Senden der `SCC_MSG_BACKGROUND_ON_MESSAGE` Nachricht, die zeigt, wie die Struktur für den Aufruf umgewandelt.  
  
```cpp#  
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
 [Von der IDE implementierte Rückruffunktionen](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-ins.md)

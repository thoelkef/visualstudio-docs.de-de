---
title: "LPTEXTOUTPROC | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "LPTEXTOUTPROC"
helpviewer_keywords: 
  - "SccMsgDataOnMessage-Struktur"
  - "SccMsgDataOnBeforeGetFile-Struktur"
  - "SccMsgDataIsCancelled-Struktur"
  - "LPTEXTOUTPROC Callback-Funktion"
  - "SccMsgDataOnAfterGetFile-Struktur"
ms.assetid: 2025c969-e3c7-4cf4-a5c5-099d342895ea
caps.latest.revision: 21
caps.handback.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
---
# LPTEXTOUTPROC
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Wenn der Benutzer ein Datenquellen\-Steuerelement\-Vorgang von innerhalb der integrierten Entwicklungsumgebung \(IDE\) ausgeführt wird, sollten das Quellcodeverwaltungs\-Plug\-in Fehler oder Status\-Nachrichten, die im Zusammenhang mit der Operation zu vermitteln. Das plug\-in kann eine eigene Meldungsfeldern zu diesem Zweck werden angezeigt. Allerdings können weitere nahtlosen Integration, das plug\-in Zeichenfolgen an der IDE übergeben, die klicken Sie dann auf systemeigene Weise anzeigen von Statusinformationen werden angezeigt. Der Mechanismus hierfür ist die `LPTEXTOUTPROC` Funktionszeiger. Die IDE implementiert diese Funktion \(weiter unten ausführlicher beschrieben\) zum Anzeigen von Fehler\- und Statusinformationen.  
  
 Die IDE übergibt an das Datenquellen\-Steuerelement\-Plug\-in einen Funktionszeiger an diese Funktion als der `lpTextOutProc` \-Parameter beim Aufrufen der [SccOpenProject](../extensibility/sccopenproject-function.md). Bei einem SCC\-Vorgang z. B. mitten in einem Aufruf der [SccGet](../extensibility/sccget-function.md) im Zusammenhang mit vielen Dateien, das plug\-in kann Aufrufen der `LPTEXTOUTPROC` Funktion, die in regelmäßigen Abständen übergeben von Zeichenfolgen angezeigt. Diese Zeichenfolgen möglicherweise eine Statusleiste, die in einem Ausgabefenster oder in einem separaten Meldungsfeld entsprechend der IDE angezeigt. Optional die IDE möglicherweise können Sie bestimmte Nachrichten mit einem **Abbrechen** Schaltfläche. Dadurch kann der Benutzer den Vorgang abbrechen und der IDE gibt die Möglichkeit, diese Informationen an das plug\-in übergeben.  
  
## Signatur  
 Die IDE Ausgabe, dass die Funktion die folgende Signatur verfügt:  
  
```cpp#  
typedef LONG (*LPTEXTOUTPROC) ( LPSTR display_string, LONG mesg_type );  
```  
  
## Parameter  
 display\_string  
 Eine Textzeichenfolge angezeigt. Diese Zeichenfolge sollte nicht mit einem Wagenrücklauf zurück oder einen Zeilenvorschub abgebrochen werden.  
  
 mesg\_type  
 Der Typ der Nachricht. Die folgende Tabelle enthält die unterstützten Werte für diesen Parameter.  
  
|Wert|Beschreibung|  
|----------|------------------|  
|`SCC_MSG_INFO, SCC_MSG_WARNING, SCC_MSG_ERROR`|Die Nachricht gilt als Information, Warnung oder Fehler.|  
|`SCC_MSG_STATUS`|Die Nachricht wird angezeigt, und in der Statusleiste angezeigt werden kann.|  
|`SCC_MSG_DOCANCEL`|Mit keine Zeichenfolge gesendet.|  
|`SCC_MSG_STARTCANCEL`|Anzeigen von beginnt ein **Abbrechen** Schaltfläche.|  
|`SCC_MSG_STOPCANCEL`|Wird nicht mehr angezeigt ein **Abbrechen** Schaltfläche.|  
|`SCC_MSG_BACKGROUND_IS_CANCELLED`|IDE gefragt werden, wenn der Hintergrundvorgang wird abgebrochen: IDE gibt `SCC_MSG_RTN_CANCEL` Wenn der Vorgang abgebrochen wurde; andernfalls wird `SCC_MSG_RTN_OK`. Die `display_string` Parameter umgewandelt ist ein [SccMsgDataIsCancelled](#LinkSccMsgDataIsCancelled) \-Struktur, die durch das Quellcodeverwaltungs\-Plug\-in bereitgestellt werden.|  
|`SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE`|Teilt die IDE über eine Datei, bevor sie von der Versionskontrolle abgerufen werden. Die `display_string` Parameter umgewandelt ist ein [SccMsgDataOnBeforeGetFile](#LinkSccMsgDataOnBeforeGetFile) \-Struktur, die durch das Quellcodeverwaltungs\-Plug\-in bereitgestellt werden.|  
|`SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE`|Teilt die IDE über eine Datei, nachdem sie aus der Versionskontrolle abgerufen wurde. Die `display_string` Parameter umgewandelt ist ein [SccMsgDataOnAfterGetFile](#LinkSccMsgDataOnAfterGetFile) \-Struktur, die durch das Quellcodeverwaltungs\-Plug\-in bereitgestellt werden.|  
|`SCC_MSG_BACKGROUND_ON_MESSAGE`|Weist die IDE des aktuellen Status eines Hintergrundvorgangs. Die `display_string` Parameter umgewandelt ist ein [SccMsgDataOnMessage](#LinkSccMsgDataOnMessage) \-Struktur, die durch das Quellcodeverwaltungs\-Plug\-in bereitgestellt werden.|  
  
## Rückgabewert  
  
|Wert|Beschreibung|  
|----------|------------------|  
|SCC\_MSG\_RTN\_OK|Die Zeichenfolge angezeigt wurde, oder der Vorgang wurde erfolgreich abgeschlossen.|  
|SCC\_MSG\_RTN\_CANCEL|Der Benutzer möchte den Vorgang abzubrechen.|  
  
## Beispiel  
 Nehmen Sie die IDE\-Aufrufe an die [SccGet](../extensibility/sccget-function.md) mit 20 Dateinamen. Das Quellcodeverwaltungs\-Plug\-in möchte zu verhindern, dass Abbrechen des Vorgangs in der Mitte einer Datei abrufen. Nachdem Sie jede Datei erhalten sie ruft `lpTextOutProc`, übergeben sie die Statusinformationen für jede Datei und sendet eine `SCC_MSG_DOCANCEL` Nachricht, falls sie kein Status gemeldet wurde. Wenn zu einem beliebigen Zeitpunkt das plug\-in einen Rückgabewert von empfängt `SCC_MSG_RTN_CANCEL` aus der IDE es Get bricht den Vorgang ab sofort, so dass keine weiteren Dateien abgerufen werden.  
  
## Strukturen  
  
###  <a name="LinkSccMsgDataIsCancelled"></a> SccMsgDataIsCancelled  
  
```cpp#  
typedef struct { DWORD dwBackgroundOperationID; } SccMsgDataIsCancelled;  
```  
  
 Diese Struktur wird gesendet, mit der `SCC_MSG_BACKGROUND_IS_CANCELLED` Nachricht. Es wird verwendet, um die ID des Hintergrundvorgangs kommunizieren, die abgebrochen wurde.  
  
###  <a name="LinkSccMsgDataOnBeforeGetFile"></a> SccMsgDataOnBeforeGetFile  
  
```cpp#  
typedef struct { DWORD dwBackgroundOperationID; PCSTR szFile; } SccMsgDataOnBeforeGetFile;  
```  
  
 Diese Struktur wird gesendet, mit der `SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE` Nachricht. Sie wird zum kommunizieren, der Name der Datei abgerufen werden sollen und die ID des Hintergrundvorgangs, die das Abrufen von durchführt.  
  
###  <a name="LinkSccMsgDataOnAfterGetFile"></a> SccMsgDataOnAfterGetFile  
  
```cpp#  
typedef struct { DWORD dwBackgroundOperationID; PCSTR szFile; SCCRTN sResult; } SccMsgDataOnAfterGetFile;  
```  
  
 Diese Struktur wird gesendet, mit der `SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE` Nachricht. Hiermit wird das Ergebnis zum Abrufen der angegebenen Datei als auch die ID des Hintergrundvorgangs, die das Abrufen wurde die Kommunikation. Finden Sie die Rückgabewerte für die [SccGet](../extensibility/sccget-function.md) für was daher erteilt werden können.  
  
###  <a name="LinkSccMsgDataOnMessage"></a> SccMsgDataOnMessage  
 \[C\+\+\]  
  
```  
typedef struct { DWORD dwBackgroundOperationID; PCSTR szMessage; BOOL bIsError; } SccMsgDataOnMessage;  
```  
  
 Diese Struktur wird gesendet, mit der `SCC_MSG_BACKGROUND_ON_MESSAGE` Nachricht. Hiermit wird den aktuellen Status eines Hintergrundvorgangs kommunizieren. Der Status wird als eine Zeichenfolge, die von der IDE angezeigt werden und `bIsError` Gibt den Schweregrad der Meldung \(`TRUE` Fehlermeldung; `FALSE` für eine Warnung oder eine informative Meldung\). Die ID des Hintergrundvorgangs Senden des Status wird auch zugewiesen.  
  
## Codebeispiel  
 Hier ist ein kurzes Beispiel Aufrufen von `LPTEXTOUTPROC` zum Senden der `SCC_MSG_BACKGROUND_ON_MESSAGE` Nachricht zeigt, wie die Struktur für den Aufruf umgewandelt.  
  
```cpp#  
LONG SendStatusMessage( LPTEXTOUTPROC pTextOutProc, DWORD         dwBackgroundID, LPCTSTR       pStatusMsg, BOOL          bIsError) { SccMsgDataOnMessage msgData = { 0 }; LONG                result  = 0; msgData.dwBackgroundOperationID = dwBackgroundID; msgData.szMessage               = pStatusMsg; msgData.bIsError                = bIsError; result = pTextOutProc(reinterpret_cast<LPCTSTR>(&msgData), SCC_MSG_BACKGROUND_ON_MESSAGE); return result; }  
```  
  
## Siehe auch  
 [Callback\-Funktionen, die von der IDE implementiert](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [Source Control\-Plug\-ins](../extensibility/source-control-plug-ins.md)
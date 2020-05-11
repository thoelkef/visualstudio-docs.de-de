---
title: LPTEXTOUTPROC | Microsoft Docs
ms.date: 11/04/2016
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
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 38c3e8263b9a30058c2de019e5e92160b716aa71
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702791"
---
# <a name="lptextoutproc"></a>LPTEXTOUTPROC

Wenn der Benutzer einen Quellcodeverwaltungsvorgang innerhalb der integrierten Entwicklungsumgebung (IDE) ausführt, möchte das Quellcodeverwaltungs-Plug-In möglicherweise Fehler- oder Statusmeldungen im Zusammenhang mit dem Vorgang übermitteln. Das Plug-In kann zu diesem Zweck eigene Meldungsfelder anzeigen. Für eine nahtlosere Integration kann das Plug-In jedoch Zeichenfolgen an die IDE übergeben, die sie dann auf ihre systemeigene Art und Weise anzeigt, Statusinformationen anzuzeigen. Der Mechanismus dafür `LPTEXTOUTPROC` ist der Funktionszeiger. Die IDE implementiert diese Funktion (siehe unten) zum Anzeigen von Fehlern und Status.

Die IDE übergibt beim Aufrufen des [SccOpenProject](../extensibility/sccopenproject-function.md)an `lpTextOutProc` das Quellcodeverwaltungs-Plug-In einen Funktionszeiger an diese Funktion als Parameter. Während eines SCC-Vorgangs, z. B. in der Mitte eines Aufrufs des [SccGet](../extensibility/sccget-function.md) mit vielen Dateien, kann das Plug-In die `LPTEXTOUTPROC` Funktion aufrufen und periodisch Zeichenfolgen zur Anzeige übergeben. Die IDE kann diese Zeichenfolgen in einer Statusleiste, in einem Ausgabefenster oder gegebenenfalls in einem separaten Meldungsfeld anzeigen. Optional kann die IDE möglicherweise bestimmte Nachrichten mit einer **Schaltfläche Abbrechen** anzeigen. Dadurch kann der Benutzer den Vorgang abbrechen und gibt der IDE die Möglichkeit, diese Informationen an das Plug-In zurückzugeben.

## <a name="signature"></a>Signatur
 Die Ausgabefunktion der IDE hat die folgende Signatur:

```cpp
typedef LONG (*LPTEXTOUTPROC) (
   LPSTR display_string,
   LONG mesg_type
);
```

## <a name="parameters"></a>Parameter

display_string

Eine anzuzeigende Textzeichenfolge. Diese Zeichenfolge sollte nicht mit einem Wagenrücklauf oder einem Zeilenvorschub beendet werden.

mesg_type

Der Typ der Meldung. In der folgenden Tabelle sind die unterstützten Werte für diesen Parameter aufgeführt.

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|`SCC_MSG_INFO, SCC_MSG_WARNING, SCC_MSG_ERROR`|Die Nachricht wird als Information, Warnung oder Fehler betrachtet.|
|`SCC_MSG_STATUS`|Die Meldung zeigt den Status an und kann in der Statusleiste angezeigt werden.|
|`SCC_MSG_DOCANCEL`|Gesendet ohne Nachrichtenzeichenfolge.|
|`SCC_MSG_STARTCANCEL`|Beginnt mit der Anzeige einer **Schaltfläche Abbrechen.**|
|`SCC_MSG_STOPCANCEL`|Beendet die **Cancel** Anzeige einer Abbrechen-Schaltfläche.|
|`SCC_MSG_BACKGROUND_IS_CANCELLED`|Fragt IDE, ob der Hintergrundvorgang abgebrochen `SCC_MSG_RTN_CANCEL` werden soll: IDE gibt zurück, wenn der Vorgang abgebrochen wurde. Andernfalls kehrt `SCC_MSG_RTN_OK`zurück . Der `display_string` Parameter wird als [SccMsgDataIsCancelled-Struktur](#LinkSccMsgDataIsCancelled) umgegossen, die vom Quellcodeverwaltungs-Plug-In bereitgestellt wird.|
|`SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE`|Teilt die IDE eine Datei mit, bevor sie aus der Versionskontrolle abgerufen wird. Der `display_string` Parameter wird als [SccMsgDataOnBeforeGetFile-Struktur](#LinkSccMsgDataOnBeforeGetFile) umgegossen, die vom Quellcodeverwaltungs-Plug-In bereitgestellt wird.|
|`SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE`|Teilt die IDE eine Datei mit, nachdem sie aus der Versionskontrolle abgerufen wurde. Der `display_string` Parameter wird als [SccMsgDataOnAfterGetFile-Struktur](#LinkSccMsgDataOnAfterGetFile) umgegossen, die vom Quellcodeverwaltungs-Plug-In bereitgestellt wird.|
|`SCC_MSG_BACKGROUND_ON_MESSAGE`|Gibt die IDE des aktuellen Status eines Hintergrundvorgangs an. Der `display_string` Parameter wird als [SccMsgDataOnMessage-Struktur](#LinkSccMsgDataOnMessage) umgegossen, die vom Quellcodeverwaltungs-Plug-In bereitgestellt wird.|

## <a name="return-value"></a>Rückgabewert

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|SCC_MSG_RTN_OK|Die Zeichenfolge wurde angezeigt, oder der Vorgang wurde erfolgreich abgeschlossen.|
|SCC_MSG_RTN_CANCEL|Der Benutzer möchte den Vorgang abbrechen.|

## <a name="example"></a>Beispiel
 Angenommen, die IDE ruft [sccGet](../extensibility/sccget-function.md) mit zwanzig Dateinamen auf. Das Quellcodeverwaltungs-Plug-In möchte verhindern, dass der Vorgang in der Mitte eines Dateiaberhaltens abgebrochen wird. Nachdem jede Datei abgesendet wurde, ruft sie auf, `lpTextOutProc`übergibt sie die Statusinformationen für jede Datei und sendet eine `SCC_MSG_DOCANCEL` Nachricht, wenn sie keinen Status zu melden hat. Wenn das Plug-In zu irgendeinem Zeitpunkt `SCC_MSG_RTN_CANCEL` einen Rückgabewert von der IDE erhält, bricht es den Abrufvorgang sofort ab, sodass keine weiteren Dateien abgerufen werden.

## <a name="structures"></a>Strukturen

### <a name="sccmsgdataiscancelled"></a><a name="LinkSccMsgDataIsCancelled"></a>SccMsgDataIsCancelled

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
} SccMsgDataIsCancelled;
```

 Diese Struktur wird `SCC_MSG_BACKGROUND_IS_CANCELLED` mit der Nachricht gesendet. Es wird verwendet, um die ID des Hintergrundvorgangs zu kommunizieren, der abgebrochen wurde.

### <a name="sccmsgdataonbeforegetfile"></a><a name="LinkSccMsgDataOnBeforeGetFile"></a>SccMsgDataOnBeforeGetFile

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
   PCSTR szFile;
} SccMsgDataOnBeforeGetFile;
```

 Diese Struktur wird `SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE` mit der Nachricht gesendet. Es wird verwendet, um den Namen der Datei, die abgerufen werden soll, und die ID des Hintergrundvorgangs, der das Abrufen durchführt, mitzuteilen.

### <a name="sccmsgdataonaftergetfile"></a><a name="LinkSccMsgDataOnAfterGetFile"></a>SccMsgDataOnAfterGetFile

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
   PCSTR szFile;
   SCCRTN sResult;
} SccMsgDataOnAfterGetFile;
```

 Diese Struktur wird `SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE` mit der Nachricht gesendet. Es wird verwendet, um das Ergebnis des Abrufens der angegebenen Datei sowie die ID des Hintergrundvorgangs zu kommunizieren, der das Abrufen durchgeführt hat. Die Rückgabewerte für [SccGet](../extensibility/sccget-function.md) finden Sie in den Rückgabewerten für das, was als Ergebnis angegeben werden kann.

### <a name="sccmsgdataonmessage"></a><a name="LinkSccMsgDataOnMessage"></a>SccMsgDataOnMessage

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
   PCSTR szMessage;
   BOOL bIsError;
} SccMsgDataOnMessage;
```

 Diese Struktur wird `SCC_MSG_BACKGROUND_ON_MESSAGE` mit der Nachricht gesendet. Es wird verwendet, um den aktuellen Status eines Hintergrundvorgangs zu kommunizieren. Der Status wird als Zeichenfolge ausgedrückt, die `bIsError` von der IDE angezeigt`TRUE` werden soll, und gibt den Schweregrad der Nachricht an (für eine Fehlermeldung; `FALSE` für eine Warnung oder für eine Informationsmeldung). Die ID des Hintergrundvorgangs, der den Status sendet, wird ebenfalls angegeben.

## <a name="code-example"></a>Codebeispiel
 Hier ist ein kurzes Beispiel für den Aufruf, `LPTEXTOUTPROC` um die `SCC_MSG_BACKGROUND_ON_MESSAGE` Nachricht zu senden, und zeigt, wie die Struktur für den Anruf gecastet wird.

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

## <a name="see-also"></a>Weitere Informationen
- [Von der IDE implementierte Rückruffunktionen](../extensibility/callback-functions-implemented-by-the-ide.md)
- [Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-ins.md)

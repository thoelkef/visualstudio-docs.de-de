---
title: SccCheckin-Funktion | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccCheckin
helpviewer_keywords:
- SccCheckin function
ms.assetid: e3f26ac2-6163-42e1-a764-22cfea5a3bc6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a5ba512642e1a63d9d39856f96194d717583d44f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701182"
---
# <a name="scccheckin-function"></a>SccCheckin-Funktion
Diese Funktion checkt zuvor ausgecheckte Dateien in das Quellcodeverwaltungssystem ein, speichert die Änderungen und erstellt eine neue Version. Diese Funktion wird mit einer Anzahl und einem Array von Namen der einzucheckenden Dateien aufgerufen.

## <a name="syntax"></a>Syntax

```cpp
SCCRTN SccCheckin (
   LPVOID    pvContext,
   HWND      hWnd,
   LONG      nFiles,
   LPSTR*    lpFileNames,
   LPCSTR    lpComment,
   LONG      fOptions,
   LPCMDOPTS pvOptions
);
```

### <a name="parameters"></a>Parameter
 pvContext

[in] Die Quellcodeverwaltungs-Plug-In-Kontextstruktur.

 hWnd

[in] Ein Handle für das IDE-Fenster, das das SCC-Plug-In als übergeordnetes Element für alle dialogfelder verwenden kann, die es bereitstellt.

 nFiles

[in] Anzahl der dateien, die eingecheckt werden sollen.

 lpFileNames

[in] Array mit vollqualifizierten lokalen Pfadnamen von Dateien, die eingecheckt werden sollen.

 lpComment

[in] Kommentar, der auf jede der ausgewählten Dateien angewendet werden soll, die eingecheckt werden. Dieser Parameter `NULL` ist, wenn das Quellcodeverwaltungs-Plug-In zur Eingabe eines Kommentars auffordern soll.

 Foptions

[in] Befehlsflags, entweder `SCC_KEEP_CHECKEDOUT`0 oder .

 pvOptions

[in] SCC-Plug-in-spezifische Optionen.

## <a name="return-value"></a>Rückgabewert
 Die Quellcodeverwaltungs-Plug-In-Implementierung dieser Funktion wird voraussichtlich einen der folgenden Werte zurückgeben:

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|SCC_OK|Die Datei wurde erfolgreich eingecheckt.|
|SCC_E_FILENOTCONTROLLED|Die ausgewählte Datei befindet sich nicht unter Quellcodeverwaltung.|
|SCC_E_ACCESSFAILURE|Beim Zugriff auf das Quellcodeverwaltungssystem ist ein Problem auftritt, wahrscheinlich aufgrund von Netzwerk- oder Konfliktproblemen. Es wird ein Wiederholungsversuch empfohlen.|
|SCC_E_NONSPECIFICERROR|Unspezifischer Fehler. Die Datei wurde nicht eingecheckt.|
|SCC_E_NOTCHECKEDOUT|Der Benutzer hat die Datei nicht ausgecheckt, kann sie daher nicht einchecken.|
|SCC_E_CHECKINCONFLICT|Das Einchecken konnte aus:<br /><br /> - Ein anderer Benutzer hat `bAutoReconcile` im Voraus eingecheckt und war falsch.<br /><br /> - oder -<br /><br /> - Die automatische Zusammenführung kann nicht durchgeführt werden (z. B. wenn Dateien binär sind).|
|SCC_E_VERIFYMERGE|Die Datei wurde automatisch zusammengeführt, aber nicht in der ausstehenden Benutzerüberprüfung eingecheckt.|
|SCC_E_FIXMERGE|Die Datei wurde automatisch zusammengeführt, aber aufgrund eines Zusammenführungskonflikts, der manuell aufgelöst werden muss, nicht eingecheckt.|
|SCC_E_NOTAUTHORIZED|Der Benutzer darf diesen Vorgang nicht ausführen.|
|SCC_I_OPERATIONCANCELED|Der Vorgang wurde vor dem Abschluss abgebrochen.|
|SCC_I_RELOADFILE|Eine Datei oder ein Projekt muss neu geladen werden.|
|SCC_E_FILENOTEXIST|Lokale Datei wurde nicht gefunden.|

## <a name="remarks"></a>Bemerkungen
 Der Kommentar gilt für alle eingecheckten Dateien. Das Kommentarargument kann `null` eine Zeichenfolge sein, in diesem Fall kann das Quellcodeverwaltungs-Plug-In den Benutzer zur Eingabe einer Kommentarzeichenfolge für jede Datei auffordern.

 Dem `fOptions` Argument kann ein Wert `SCC_KEEP_CHECKEDOUT` des Flags gegeben werden, um die Absicht des Benutzers anzugeben, die Datei einzuchecken und erneut auszuchecken.

## <a name="see-also"></a>Weitere Informationen
- [Quellcodeverwaltungs-Plug-In-API-Funktionen](../extensibility/source-control-plug-in-api-functions.md)

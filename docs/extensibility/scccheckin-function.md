---
title: SccCheckin-Funktion | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccCheckin
helpviewer_keywords:
- SccCheckin function
ms.assetid: e3f26ac2-6163-42e1-a764-22cfea5a3bc6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 178cebb974147a95aac35ebabe484dc4a7777407
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62802994"
---
# <a name="scccheckin-function"></a>SccCheckin-Funktion
Diese Funktion überprüft im zuvor ausgecheckten Dateien auf das Quellcodeverwaltungssystem, die Änderungen zu speichern und Erstellen einer neuen Version. Diese Funktion wird mit einem Zähler und ein Array von Namen der Dateien eingecheckt werden aufgerufen.

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

[in] Datenquellen-Steuerelement-Plug-in Context-Struktur.

 hWnd

[in] Ein Handle für das IDE-Fenster, das die SCC-Plug-in als übergeordnetes Element für alle Dialogfelder verwenden können, die er bereitstellt.

 nFiles

[in] Anzahl der Dateien, die eingecheckt werden sollen.

 lpFileNames

[in] Array der Namen von voll gekennzeichneter lokaler Pfad von Dateien, die eingecheckt werden.

 lpComment

[in] Der Kommentar, der auf die einzelnen ausgewählten Dateien, die eingecheckt angewendet werden. Dieser Parameter ist `NULL` , wenn das Quellcodeverwaltungs-Plug-In für einen Kommentar auffordert.

 Bestanden

[in] Befehl Flags, die entweder 0 oder `SCC_KEEP_CHECKEDOUT`.

 pvOptions

[in] SCC-plug-in spezifischen Optionen.

## <a name="return-value"></a>Rückgabewert
 Die Source-Steuerelement-Plug-in-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:

|Wert|Beschreibung|
|-----------|-----------------|
|SCC_OK|Datei wurde erfolgreich eingecheckt.|
|SCC_E_FILENOTCONTROLLED|Die ausgewählte Datei ist nicht unter quellcodeverwaltung befindet.|
|SCC_E_ACCESSFAILURE|Es wurde ein Problem, das Zugriff auf das Quellcodeverwaltungssystem, möglicherweise aufgrund eines Netzwerk-oder-Konflikte bestehen. Eine Wiederholung wird empfohlen.|
|SCC_E_NONSPECIFICERROR|Nicht spezifischen Fehler. Datei wurde nicht eingecheckt.|
|SCC_E_NOTCHECKEDOUT|Der Benutzer hat nicht die Datei, damit Sie sie einchecken kann nicht überprüft werden.|
|SCC_E_CHECKINCONFLICT|Einchecken konnte nicht ausgeführt werden, da:<br /><br /> – Ein anderer Benutzer hat jetzt aktiviert und `bAutoReconcile` wurde "false".<br /><br /> - oder - <br /><br /> – Die automatische Zusammenführung kann nicht erfolgen, (z. B., wenn die Dateien "binary" sind).|
|SCC_E_VERIFYMERGE|Datei wurde automatisch zusammengeführt, jedoch nicht überprüft wurden ausstehende Überprüfung des Benutzers.|
|SCC_E_FIXMERGE|Datei wurde automatisch zusammengeführt, aber nicht in eingecheckt wurde aufgrund eines Zusammenführungskonflikts, das manuell gelöst werden muss.|
|SCC_E_NOTAUTHORIZED|Der Benutzer ist nicht zulässig, um diesen Vorgang auszuführen.|
|SCC_I_OPERATIONCANCELED|Vorgang wurde vor Abschluss abgebrochen.|
|SCC_I_RELOADFILE|Eine Datei oder ein Projekt muss neu geladen werden.|
|SCC_E_FILENOTEXIST|Lokale Datei wurde nicht gefunden.|

## <a name="remarks"></a>Hinweise
 Der Kommentar gilt für alle Dateien, die eingecheckt wird. Das kommentarargument möglich einen `null` string "," in diesem Fall kann das Quellcodeverwaltungs-Plug-in den Benutzer für eine Kommentarzeichenfolge für jede Datei auffordern.

 Die `fOptions` Argument einen Wert angegeben werden kann die `SCC_KEEP_CHECKEDOUT` Flag an, dass die Absicht des Benutzers überprüfen Sie die Datei ein, und Testen Sie es noch mal.

## <a name="see-also"></a>Siehe auch
- [Datenquellen-Steuerelement-Plug-in-API-Funktionen](../extensibility/source-control-plug-in-api-functions.md)
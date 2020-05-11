---
title: SccAdd-Funktion | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccAdd
helpviewer_keywords:
- SccAdd function
ms.assetid: 545268f3-8e83-446a-a398-1a9db9e866e8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 23a6226b0d3cc2441a509c16b2e4672a766f3329
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701315"
---
# <a name="sccadd-function"></a>SccAdd-Funktion
Diese Funktion fügt dem Quellcodeverwaltungssystem neue Dateien hinzu.

## <a name="syntax"></a>Syntax

```cpp
SCCRTN SccAdd(
   LPVOID    pvContext,
   HWND      hWnd,
   LONG      nFiles,
   LPCSTR*   lpFileNames,
   LPCSTR    lpComment,
   LONG*     pfOptions,
   LPCMDOPTS pvOptions
);
```

### <a name="parameters"></a>Parameter
 pvContext

[in] Die Quellcodeverwaltungs-Plug-In-Kontextstruktur.

 hWnd

[in] Ein Handle für das IDE-Fenster, das das Quellcodeverwaltungs-Plug-In als übergeordnetes Element für alle dialogfelder verwenden kann, die es bereitstellt.

 nFiles

[in] Anzahl der Dateien, die dem aktuellen Projekt `lpFileNames` hinzugefügt werden sollen, wie im Array angegeben.

 lpFileNames

[in] Array voll qualifizierter lokaler Namen von Dateien, die hinzugefügt werden sollen.

 lpComment

[in] Der Kommentar, der auf alle hinzugefügten Dateien angewendet werden soll.

 pfOptions

[in] Array von Befehlsflags, die pro Datei bereitgestellt werden.

 pvOptions

[in] Quellcodeverwaltung Plug-in-spezifische Optionen.

## <a name="return-value"></a>Rückgabewert
 Die Quellcodeverwaltungs-Plug-In-Implementierung dieser Funktion wird voraussichtlich einen der folgenden Werte zurückgeben:

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|SCC_OK|Der Add-Vorgang war erfolgreich.|
|SCC_E_FILEALREADYEXISTS|Die ausgewählte Datei befindet sich bereits unter Quellcodeverwaltung.|
|SCC_E_TYPENOTSUPPORTED|Der Dateityp (z. B. Binärdatei) wird vom Quellcodeverwaltungssystem nicht unterstützt.|
|SCC_E_OPNOTSUPPORTED|Das Quellcodeverwaltungssystem unterstützt diesen Vorgang nicht.|
|SCC_E_ACCESSFAILURE|Beim Zugriff auf das Quellcodeverwaltungssystem ist ein Problem auftritt, wahrscheinlich aufgrund von Netzwerk- oder Konfliktproblemen. Es wird ein Wiederholungsversuch empfohlen.|
|SCC_E_NOTAUTHORIZED|Der Benutzer darf diesen Vorgang nicht ausführen.|
|SCC_E_NONSPECIFICERROR|Unspezifisches Versagen; nicht ausgeführt hinzugefügt.|
|SCC_I_OPERATIONCANCELED|Der Vorgang wurde vor Abschluss abgebrochen.|
|SCC_I_RELOADFILE|Eine Datei oder ein Projekt muss neu geladen werden.|
|SCC_E_FILENOTEXIST|Lokale Datei wurde nicht gefunden.|

## <a name="remarks"></a>Bemerkungen
 Die `fOptions` üblichen werden hier durch `pfOptions`ein `LONG` Array ersetzt, , mit einer Optionsspezifikation pro Datei. Dies liegt daran, dass der Dateityp von Datei zu Datei variieren kann.

> [!NOTE]
> Es ist ungültig, `SCC_FILETYPE_TEXT` sowohl `SCC_FILETYPE_BINARY` die Optionen für dieselbe Datei anzugeben, aber es ist gültig, keines der beiden zu geben. Das Festlegen von keiner `SCC_FILETYPE_AUTO`der beiden Einstellungen ist identisch, in diesem Fall erkennt das Quellcodeverwaltungs-Plug-In den Dateityp automatisch.

 Unten ist die Liste der `pfOptions` Flags, die im Array verwendet werden:

|Option|Wert|Bedeutung|
|------------|-----------|-------------|
|SCC_FILETYPE_AUTO|0x00|Das Quellcodeverwaltungs-Plug-In sollte den Dateityp erkennen.|
|SCC_FILETYPE_TEXT|0x01|Gibt eine ASCII-Textdatei an.|
|SCC_FILETYPE_BINARY|0x02|Gibt einen anderen Dateityp als ASCII-Text an.|
|SCC_ADD_STORELATEST|0x04|Speichert nur die neueste Kopie der Datei, keine Deltas.|
|SCC_FILETYPE_TEXT_ANSI|0x08|Behandelt die Datei als ANSI-Text.|
|SCC_FILETYPE_UTF8|0x10|Behandelt die Datei als Unicode-Text im UTF8-Format.|
|SCC_FILETYPE_UTF16LE|0x20|Behandelt die Datei als Unicode-Text im UTF16 Little Endian-Format.|
|SCC_FILETYPE_UTF16BE|0x40|Behandelt die Datei als Unicode-Text im UTF16 Big Endian-Format.|

## <a name="see-also"></a>Weitere Informationen
- [Quellcodeverwaltungs-Plug-In-API-Funktionen](../extensibility/source-control-plug-in-api-functions.md)

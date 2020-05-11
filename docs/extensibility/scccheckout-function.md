---
title: SccCheckout-Funktion | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccCheckout
helpviewer_keywords:
- SccCheckout function
ms.assetid: 06e9ecd7-fc09-40c1-9dd1-2b56c622c80b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6ed809e33a80bf2903c88550e97b28b1e0178bcd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701104"
---
# <a name="scccheckout-function"></a>SccCheckout-Funktion
Angesichts einer Liste vollqualifizierter Dateinamen werden diese mit dieser Funktion auf dem lokalen Laufwerk ausgecheckt. Der Kommentar gilt für alle ausgecheckten Dateien. Das Kommentarargument kann `null` eine Zeichenfolge sein.

## <a name="syntax"></a>Syntax

```cpp
SCCRTN SccCheckout (
   LPVOID    pvContext,
   HWND      hWnd,
   LONG      nFiles,
   LPCSTR*   lpFileNames,
   LPCSTR    lpComment,
   LONG      fOptions,
   LPCMDOPTS pvOptions
);
```

### <a name="parameters"></a>Parameter
 pvContext

[in] Die Quellcodeverwaltungs-Plug-In-Kontextstruktur.

 hWnd

[in] Ein Handle für das IDE-Fenster, das das Quellcodeverwaltungs-Plug-In als übergeordnetes Element für alle dialogfelder verwenden kann, die es bereitstellt.

 nFiles

[in] Anzahl der dateien, die ausgecheckt werden sollen.

 lpFileNames

[in] Array mit vollqualifizierten lokalen Pfadnamen von auszucheckenden Dateien.

 lpComment

[in] Kommentar, der auf jede der ausgewählten Dateien angewendet werden soll, die ausgecheckt werden.

 Foptions

[in] Befehlsflags (siehe [Bitflags, die von bestimmten Befehlen verwendet werden).](../extensibility/bitflags-used-by-specific-commands.md)

 pvOptions

[in] Quellcodeverwaltung Plug-in-spezifische Optionen.

## <a name="return-value"></a>Rückgabewert
 Die Quellcodeverwaltungs-Plug-In-Implementierung dieser Funktion wird voraussichtlich einen der folgenden Werte zurückgeben:

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|SCC_OK|Der Check-out war erfolgreich.|
|SCC_E_FILENOTCONTROLLED|Die ausgewählte Datei befindet sich nicht unter Quellcodeverwaltung.|
|SCC_E_ACCESSFAILURE|Beim Zugriff auf das Quellcodeverwaltungssystem ist ein Problem auftritt, wahrscheinlich aufgrund von Netzwerk- oder Konfliktproblemen. Es wird ein Wiederholungsversuch empfohlen.|
|SCC_E_NOTAUTHORIZED|Der Benutzer darf diesen Vorgang nicht ausführen.|
|SCC_E_NONSPECIFICERROR|Unspezifischer Fehler. Die Datei wurde nicht ausgecheckt.|
|SCC_E_ALREADYCHECKEDOUT|Der Benutzer hat die Datei bereits ausgecheckt.|
|SCC_E_FILEISLOCKED|Die Datei ist gesperrt, was die Erstellung neuer Versionen verhindert.|
|SCC_E_FILEOUTEXCLUSIVE|Ein anderer Benutzer hat ein exklusives Auschecken für diese Datei durchgeführt.|
|SCC_I_OPERATIONCANCELED|Der Vorgang wurde vor Abschluss abgebrochen.|

## <a name="see-also"></a>Weitere Informationen
- [Quellcodeverwaltungs-Plug-In-API-Funktionen](../extensibility/source-control-plug-in-api-functions.md)
- [Bitflags, die von bestimmten Befehlen verwendet werden](../extensibility/bitflags-used-by-specific-commands.md)

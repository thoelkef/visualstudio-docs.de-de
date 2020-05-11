---
title: SccDiff-Funktion | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccDiff
helpviewer_keywords:
- SccDiff function
ms.assetid: d49bc8c5-f631-4153-9d3c-feb3564da305
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9b68df68ce7fa4ad5cbc98db256204ddf8623d2c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701021"
---
# <a name="sccdiff-function"></a>SccDiff-Funktion
Diese Funktion zeigt die Unterschiede zwischen der aktuellen Datei (auf dem lokalen Datenträger) und der zuletzt eingecheckten Version im Quellcodeverwaltungssystem an (oder sucht optional nur nach).

## <a name="syntax"></a>Syntax

```cpp
SCCRTN SccDiff(
   LPVOID    pvContext,
   HWND      hWnd,
   LPCSTR    lpFileName,
   LONG      fOptions,
   LPCMDOPTS pvOptions
);
```

### <a name="parameters"></a>Parameter
 pvContext

[in] Die Quellcodeverwaltungs-Plug-In-Kontextstruktur.

 hWnd

[in] Ein Handle für das IDE-Fenster, das das Quellcodeverwaltungs-Plug-In als übergeordnetes Element für alle dialogfelder verwenden kann, die es bereitstellt.

 lpFileName

[in] Dateiname, für den die Differenz angefordert wird.

 Foptions

[in] Befehlsflags. Einzelheiten finden Sie in den Hinweisen.

 pvOptions

[in] Quellcodeverwaltung Plug-in-spezifische Optionen.

## <a name="return-value"></a>Rückgabewert
 Die Quellcodeverwaltungs-Plug-In-Implementierung dieser Funktion wird voraussichtlich einen der folgenden Werte zurückgeben:

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|SCC_OK|Die Arbeitskopie und die Serverversion sind identisch.|
|SCC_I_FILESDIFFERS|Die Arbeitskopie unterscheidet sich von der Unterquellcode-Version.|
|SCC_I_RELOADFILE|Eine Datei oder ein Projekt muss neu geladen werden.|
|SCC_E_FILENOTCONTROLLED|Die Datei befindet sich nicht unter Quellcodeverwaltung.|
|SCC_E_NOTAUTHORIZED|Der Benutzer darf diesen Vorgang nicht ausführen.|
|SCC_E_ACCESSFAILURE|Beim Zugriff auf das Quellcodeverwaltungssystem ist ein Problem auftritt, wahrscheinlich aufgrund von Netzwerk- oder Konfliktproblemen. Es wird ein Wiederholungsversuch empfohlen.|
|SCC_E_NONSPECIFICERROR|Unspezifisches Versagen; Dateidifferenz wurde nicht ermittelt.|
|SCC_E_FILENOTEXIST|Die lokale Datei wurde nicht gefunden.|

## <a name="remarks"></a>Bemerkungen
 Diese Funktion dient zwei verschiedenen Zwecken. Standardmäßig wird eine Liste der Änderungen an einer Datei angezeigt. Das Quellcodeverwaltungs-Plug-In öffnet sein eigenes Fenster in jedem format, das es wählt, um die Unterschiede zwischen der Datei des Benutzers auf dem Datenträger und der neuesten Version der Datei unter Quellcodeverwaltung anzuzeigen.

 Alternativ muss die IDE möglicherweise einfach feststellen, ob sich eine Datei geändert hat. Beispielsweise muss die IDE möglicherweise ermitteln, ob es sicher ist, eine Datei auszuchecken, ohne den Benutzer zu informieren. In diesem Fall wird die `SCC_DIFF_CONTENTS` IDE in das Flag eingebunden. Das Quellcodeverwaltungs-Plug-In muss die Datei auf dem Datenträger byte-byte mit der datei unter Quellcodeverwaltung überprüfen und einen Wert zurückgeben, der angibt, ob die beiden Dateien unterschiedlich sind, ohne dem Benutzer etwas anzuzeigen.

 Als Leistungsoptimierung kann das Quellcodeverwaltungs-Plug-In eine Alternative verwenden, die auf einer Prüfsumme oder einem Zeitstempel `SCC_DIFF_CONTENTS`basiert, anstelle des Byte-by-Byte-Vergleichs, der durch folgende Art und Weise gefordert wird: Diese Vergleichsformen sind offensichtlich schneller, aber weniger zuverlässig. Möglicherweise unterstützen nicht alle Quellcodeverwaltungssysteme diese alternativen Vergleichsmethoden, und das Plug-In muss möglicherweise auf einen Inhaltsvergleich zurückgreifen. Alle Quellcodeverwaltungs-Plug-Ins müssen mindestens einen Inhaltsvergleich unterstützen.

> [!NOTE]
> Die schnellen Differenzflaggen schließen sich gegenseitig aus. Es ist gültig, keine Flags zu übergeben, aber es ist nicht gültig, gleichzeitig mehr als eine zu übergeben. `SCC_DIFF_QUICK_DIFF`, eine Maske, die alle Flags kombiniert, kann zum Testen verwendet werden, sollte aber niemals als Parameter übergeben werden.

|`fOption`|Bedeutung|
|---------------|-------------|
|SCC_DIFF_IGNORECASE|Fallunsensitive Vergleich (kann für schnelle oder visuelle Differenz verwendet werden).|
|SCC_DIFF_IGNORESPACE|Ignoriert Leerraum (kann für schnelle oder visuelle Differenzen verwendet werden).|
|SCC_DIFF_QD_CONTENTS|Vergleicht die Datei stillschweigend, Byte für Byte.|
|SCC_DIFF_QD_CHECKSUM|Vergleicht die Datei bei Unterstützung stillschweigend über eine Prüfsumme. Wenn diese nicht unterstützt wird, wird auf einen Inhaltsvergleich zurückzurückgeblickt.|
|SCC_DIFF_QD_TIME|Vergleicht die Datei bei Unterstützung stillschweigend über ihren Zeitstempel. Wenn diese nicht unterstützt wird, wird auf einen Inhaltsvergleich zurückzurückgeblickt.|

## <a name="see-also"></a>Weitere Informationen
- [Quellcodeverwaltungs-Plug-In-API-Funktionen](../extensibility/source-control-plug-in-api-functions.md)

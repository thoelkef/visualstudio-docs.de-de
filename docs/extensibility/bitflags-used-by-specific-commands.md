---
title: Von bestimmten Befehlen verwendete Bitflags | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, bitflags used by specific commands
ms.assetid: 37969977-6f7d-45c9-ba03-1306ae71f5d1
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 47dd3b1c75ab7ff206714509a82449d744a02952
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66333524"
---
# <a name="bitflags-used-by-specific-commands"></a>Von bestimmten Befehlen verwendete Bitflags
Das Verhalten einer Reihe von Funktionen in der Quelle-Plug-in-API kann durch Festlegen von einem oder mehreren Bits in einem einzelnen Wert geändert werden. Diese Werte werden als Bitflags bezeichnet. Die verschiedenen Bitflags, die von der Quelle-Plug-in-API verwendet, werden hier beschrieben gruppiert, die von der Funktion, die sie verwendet.

## <a name="checked-out-flag"></a>Flag ausgecheckt
 Dieses Flag kann festgelegt werden, entweder die [SccAdd](../extensibility/sccadd-function.md) oder [SccCheckin](../extensibility/scccheckin-function.md).

|Flag|Wert|Beschreibung|
|----------|-----------|-----------------|
|`SCC_KEEP_CHECKEDOUT`|0x1000|Halten Sie die Datei ausgecheckt haben.|

## <a name="add-flags"></a>Hinzufügen von flags
 Diese Flags werden verwendet, durch die [SccAdd](../extensibility/sccadd-function.md).

|Flag|Wert|Beschreibung|
|----------|-----------|-----------------|
|`SCC_FILETYPE_AUTO`|0x00|Das Quellcodeverwaltungs-Plug-in wird erwartet, automatisch zu erkennen, ob die Datei Text- oder Binärdaten.|
|`SCC_FILETYPE_TEXT`|0x01|Dateityp ist Text.|
|`SCC_FILETYPE_BINARY`|0x04|Dateityp ist binär. **Hinweis:** `SCC_FILETYPE_TEXT` und `SCC_FILETYPE_BINARY` Flags schließen sich gegenseitig. Legen Sie genau eines oder keines von beiden.|
|`SCC_ADD_STORELATEST`|0x02|Store nur die neueste Version (keine Deltas).|

## <a name="diff-flags"></a>Diff-flags
 Die [SccDiff](../extensibility/sccdiff-function.md) diese Flags definieren des Bereichs eines Diff-Vorgangs verwendet. Die `SCC_DIFF_QD_xxx` Flags schließen sich gegenseitig. Wenn eines dieser Projekte angegeben wird, ist kein visuelles Feedback gegeben werden soll. In einem "schnellen"Diff (QD), das plug-in wird nicht bestimmt, wie die Datei unterscheidet sich, nur dann, wenn er sich unterscheidet. Wenn keines ist diese Flags angegeben "visual Diff" erfolgt., Ausführliche Dateiunterschieden werden berechnet und angezeigt. Wenn die angeforderte QD nicht unterstützt wird, verschiebt zur nächsten bewährte des Plug-Ins. Z. B. überprüfen, ob die IDE, eine Prüfsumme anfordert, und das plug-in nicht unterstützt,-Plug-in ist eine vollständige-Inhalt (immer noch sehr viel schneller als eine visuelle Darstellung).

|Flag|Wert|Beschreibung|
|----------|-----------|-----------------|
|`SCC_DIFF_IGNORECASE`|0x0002|Ignorieren von Groß-/Kleinschreibung unterschieden.|
|`SCC_DIFF_IGNORESPACE`|0x0004|Ignorieren von Leerzeichen Unterschiede. **Hinweis**:  Die `SCC_DIFF_IGNORECASE` und `SCC_DIFF_IGNORESPACE` Flags sind optionale Bitflags.|
|`SCC_DIFF_QD_CONTENTS`|0x0010|QD durch Vergleichen der gesamte Dateiinhalt.|
|`SCC_DIFF_QD_CHECKSUM`|0x0020|Warteschlangentiefe von Checksum.|
|`SCC_DIFF_QD_TIME`|0x0040|Warteschlangentiefe von Datums-/Zeitstempel der Datei.|
|`SCC_DIFF_QUICK_DIFF`|0x0070|Dies ist eine Maske, mit der alle dem QD Bitflags überprüft. Es sollte nicht in eine Funktion übergeben werden; die drei QD Bitflags schließen sich gegenseitig aus. QD bedeutet immer ohne Anzeige der Benutzeroberfläche.|

## <a name="populatelist-flag"></a>PopulateList-flag
 Dieses Flag wird verwendet, durch die [SccPopulateList](../extensibility/sccpopulatelist-function.md) in die `fOptions` Parameter.

|Flag|Wert|Beschreibung|
|----------|-----------|-----------------|
|`SCC_PL_DIR`|0x00000001L|Die IDE wird Verzeichnisse, Dateien nicht übergeben.|

## <a name="populatedirlist-flags"></a>PopulateDirList-flags
 Diese Flags werden verwendet, durch die [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) in die `fOptions` Parameter.

|Optionswert|Wert|Beschreibung|
|------------------|-----------|-----------------|
|SCC_PDL_ONELEVEL|0x0000|Überprüfen Sie nur eine Ebene der Verzeichnisse für Verzeichnisse (Dies ist die Standardeinstellung).|
|SCC_PDL_RECURSIVE|0x0001|Untersuchen Sie rekursiv alle Verzeichnisse in jedem angegebenen Verzeichnis.|
|SCC_PDL_INCLUDEFILES|0x0002|Schließen Sie Dateinamen in den Prozess der Überprüfung an.|

## <a name="openproject-flags"></a>Projekt öffnen-flags
 Diese Flags werden verwendet, durch die [SccOpenProject](../extensibility/sccopenproject-function.md) in die `dwFlags` Parameter.

|Optionswert|Wert|Beschreibung|
|------------------|-----------|-----------------|
|SCC_OP_CREATEIFNEW|0x00000001L|Wenn das Projekt in der quellcodeverwaltung nicht vorhanden ist, erstellen Sie ihn aus. Wenn dieses Flag nicht festgelegt ist, fordert die Benutzer für Projekt zum Erstellen (es sei denn, `SCC_OP_SILENTOPEN` -Flag angegeben ist).|
|SCC_OP_SILENTOPEN|0x00000002L|Keine benutzeraufforderung, um ein Projekt zu erstellen; Rückgabe `SCC_E_UNKNOWNPROJECT`.|

## <a name="get-flags"></a>Abrufen von flags
 Diese Flags werden verwendet, durch die [SccGet](../extensibility/sccget-function.md) und [SccCheckout](../extensibility/scccheckout-function.md).

|Flag|Wert|Beschreibung|
|----------|-----------|-----------------|
|`SCC_GET_ALL`|0x00000001L|Die IDE wird Verzeichnisse, Dateien nicht übergeben: Rufen Sie aller Dateien in diesen Verzeichnissen verwenden ab.|
|`SCC_GET_RECURSIVE`|0x00000002L|Die IDE wird Verzeichnisse übergeben: Rufen Sie diese Verzeichnisse und alle ihre Unterverzeichnisse.|

## <a name="noption-values"></a>nOption Werte
 Diese Flags werden verwendet, durch die [SccSetOption](../extensibility/sccsetoption-function.md) in die `nOption` Parameter.

|Flag|Wert|Beschreibung|
|----------|-----------|-----------------|
|`SCC_OPT_EVENTQUEUE`|0x00000001L|Legen Sie die Status der Ereigniswarteschlange.|
|`SCC_OPT_USERDATA`|0x00000002L|Geben Sie die Benutzerdaten für `SCC_OPT_NAMECHANGEPFN`.|
|`SCC_OPT_HASCANCELMODE`|0x00000003L|Die IDE kann auf "Abbrechen" verarbeiten.|
|`SCC_OPT_NAMECHANGEPFN`|0x00000004L|Legen Sie einen Rückruf für die Änderungen des Computernamens.|
|`SCC_OPT_SCCCHECKOUTONLY`|0x00000005L|Deaktivieren Sie Auschecken der Quelle quellcodeverwaltung-Plug-in-Benutzeroberfläche zu, und legen Sie Arbeitsverzeichnis nicht.|
|`SCC_OPT_SHARESUBPROJ`|0x00000006L|Hinzufügen von Quellcode-Verwaltungssystem, das ein Arbeitsverzeichnis angeben. Versuchen Sie es in das zugeordnete Projekt freigeben, wenn es sich um ein direkter Nachfolger ist.|

## <a name="dwval-bitflags"></a>DwVal bitflags
 Diese Flags werden verwendet, durch die [SccSetOption](../extensibility/sccsetoption-function.md) in die `dwVal` Parameter.

|Flag|Wert|Beschreibung|Ein, die `nOption` Wert|
|----------|-----------|-----------------|-----------------------------|
|`SCC_OPT_EQ_DISABLE`|0x00L|Hält die Ereignisaktivität für die Warteschlange.|`SCC_OPT_EVENTQUEUE`|
|`SCC_OPT_EQ_ENABLE`|0x01L|Aktiviert die Protokollierung der Ereignis-Warteschlange.|`SCC_OPT_EVENTQUEUE`|
|`SCC_OPT_HCM_NO`|0L|(Standard) Verfügt über keine "Abbrechen"-Modus; -Plug-in angeben muss, falls gewünscht.|`SCC_OPT_HASCANCELMODE`|
|`SCC_OPT_HCM_YES`|1L|IDE behandelt "Abbrechen".|`SCC_OPT_HASCANCELMODE`|
|`SCC_OPT_SCO_NO`|0L|(Standard) Problem-Plug-in-Benutzeroberfläche sehen Sie sich. Arbeitsverzeichnis festgelegt ist.|`SCC_OPT_SCCCHECKOUTONLY`|
|`SCC_OPT_SCO_YES`|1L|Keine Plug-in-Benutzeroberfläche sehen, kein Arbeitsverzeichnis.|`SCC_OPT_SCCCHECKOUTONLY`|

## <a name="see-also"></a>Siehe auch
- [Quellcodeverwaltungs-Plug-ins](../extensibility/source-control-plug-ins.md)
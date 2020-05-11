---
title: Bitflags, die von bestimmten Befehlen verwendet werden | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, bitflags used by specific commands
ms.assetid: 37969977-6f7d-45c9-ba03-1306ae71f5d1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ffa1fd8bf025d665977e87dc8b88da724ade5a8b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740010"
---
# <a name="bitflags-used-by-specific-commands"></a>Bitflags, die von bestimmten Befehlen verwendet werden
Das Verhalten einer Reihe von Funktionen in der Quellcodeverwaltungs-Plug-In-API kann geändert werden, indem ein oder mehrere Bits in einem einzelnen Wert gesetzt werden. Diese Werte werden als Bitflags bezeichnet. Die verschiedenen Bitflags, die von der Quellcodeverwaltungs-Plug-In-API verwendet werden, werden hier nach der Funktion gruppiert, die sie verwendet.

## <a name="checked-out-flag"></a>Ausgechecktflagge
 Dieses Flag kann entweder für [SccAdd](../extensibility/sccadd-function.md) oder [SccCheckin](../extensibility/scccheckin-function.md)festgelegt werden.

|Flag|Wert|BESCHREIBUNG|
|----------|-----------|-----------------|
|`SCC_KEEP_CHECKEDOUT`|0x1000|Halten Sie die Datei ausgecheckt.|

## <a name="add-flags"></a>Hinzufügen von Flags
 Diese Flags werden von [SccAdd](../extensibility/sccadd-function.md)verwendet.

|Flag|Wert|BESCHREIBUNG|
|----------|-----------|-----------------|
|`SCC_FILETYPE_AUTO`|0x00|Es wird erwartet, dass das Quellcodeverwaltungs-Plug-In automatisch erkennt, ob es sich bei der Datei um Text oder Binärdatei handelt.|
|`SCC_FILETYPE_TEXT`|0x01|Dateityp ist Text.|
|`SCC_FILETYPE_BINARY`|0x04|Der Dateityp ist binär. **Hinweis:** `SCC_FILETYPE_TEXT` `SCC_FILETYPE_BINARY` und Flags schließen sich gegenseitig aus.   Legen Sie genau eine oder keines fest.|
|`SCC_ADD_STORELATEST`|0x02|Speichern Sie nur die neueste Version (keine Deltas).|

## <a name="diff-flags"></a>Diff-Flags
 [SccDiff](../extensibility/sccdiff-function.md) verwendet diese Flags, um den Umfang eines Diff-Vorgangs zu definieren. Die `SCC_DIFF_QD_xxx` Flaggen schließen sich gegenseitig aus. Wenn einer von ihnen angegeben ist, ist kein visuelles Feedback zu geben. In einem "Quick Diff" (QD) bestimmt das Plug-In nicht, wie sich die Datei unterscheidet, nur wenn sie anders ist. Wenn keines dieser Flags angegeben ist, wird ein "visueller Diff" ausgeführt. detaillierte Dateiunterschiede werden berechnet und angezeigt. Wenn die angeforderte QD nicht unterstützt wird, wird das Plug-In zum nächstbesten verschoben. Wenn die IDE z. B. eine Prüfsumme anfordert und das Plug-In sie nicht unterstützt, führt das Plug-In eine Überprüfung des vollständigen Inhalts durch (immer noch viel schneller als eine visuelle Anzeige).

|Flag|Wert|BESCHREIBUNG|
|----------|-----------|-----------------|
|`SCC_DIFF_IGNORECASE`|0x0002|Ignorieren Sie Fallunterschiede.|
|`SCC_DIFF_IGNORESPACE`|0x0004|Ignorieren Sie Leerraumunterschiede. **Hinweis:**  Die `SCC_DIFF_IGNORECASE` `SCC_DIFF_IGNORESPACE` und Flags sind optionale Bitflags.|
|`SCC_DIFF_QD_CONTENTS`|0x0010|QD durch Vergleichen des gesamten Dateiinhalts.|
|`SCC_DIFF_QD_CHECKSUM`|0x0020|QD nach Prüfsumme.|
|`SCC_DIFF_QD_TIME`|0x0040|QD nach Dateidatums-/Uhrzeitstempel.|
|`SCC_DIFF_QUICK_DIFF`|0x0070|Dies ist eine Maske, die verwendet wird, um alle QD-Bitflags zu überprüfen. Sie sollte nicht an eine Funktion übergeben werden; Die drei QD-Bitflags schließen sich gegenseitig aus. QD bedeutet immer keine Anzeige der Benutzeroberfläche.|

## <a name="populatelist-flag"></a>PopulateList-Flag
 Dieses Flag wird von der [SccPopulateList](../extensibility/sccpopulatelist-function.md) im `fOptions` Parameter verwendet.

|Flag|Wert|BESCHREIBUNG|
|----------|-----------|-----------------|
|`SCC_PL_DIR`|0x00000001L|Die IDE übergibt Verzeichnisse, keine Dateien.|

## <a name="populatedirlist-flags"></a>PopulateDirList-Flags
 Diese Flags werden von der [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) im `fOptions` Parameter verwendet.

|Optionswert|Wert|BESCHREIBUNG|
|------------------|-----------|-----------------|
|SCC_PDL_ONELEVEL|0x0000|Untersuchen Sie nur eine Ebene von Verzeichnissen für Verzeichnisse (dies ist die Standardeinstellung).|
|SCC_PDL_RECURSIVE|0x0001|Überprüfen Sie alle Verzeichnisse unter jedem gegebenen Verzeichnis rekursiv.|
|SCC_PDL_INCLUDEFILES|0x0002|Schließen Sie Dateinamen in den Prüfungsprozess ein.|

## <a name="openproject-flags"></a>OpenProject-Flags
 Diese Flags werden vom [SccOpenProject](../extensibility/sccopenproject-function.md) im `dwFlags` Parameter verwendet.

|Optionswert|Wert|BESCHREIBUNG|
|------------------|-----------|-----------------|
|SCC_OP_CREATEIFNEW|0x00000001L|Wenn das Projekt in der Quellcodeverwaltung nicht vorhanden ist, erstellen Sie es. Wenn dieses Flag nicht festgelegt ist, fordern `SCC_OP_SILENTOPEN` Sie den Benutzer für das Projekt zum Erstellen auf (es sei denn, es wird ein Flag angegeben).|
|SCC_OP_SILENTOPEN|0x00000002L|Fordern Sie den Benutzer nicht auf, ein Projekt zu erstellen. einfach `SCC_E_UNKNOWNPROJECT`zurückgeben .|

## <a name="get-flags"></a>Holen Sie sich Flaggen
 Diese Flags werden von [SccGet](../extensibility/sccget-function.md) und [SccCheckout](../extensibility/scccheckout-function.md)verwendet.

|Flag|Wert|BESCHREIBUNG|
|----------|-----------|-----------------|
|`SCC_GET_ALL`|0x00000001L|Die IDE übergibt Verzeichnisse, keine Dateien: Abrufen aller Dateien in diesen Verzeichnissen.|
|`SCC_GET_RECURSIVE`|0x00000002L|Die IDE übergibt Verzeichnisse: Holen Sie sich diese Verzeichnisse und alle ihre Unterverzeichnisse.|

## <a name="noption-values"></a>nOption-Werte
 Diese Flags werden von der [SccSetOption](../extensibility/sccsetoption-function.md) im `nOption` Parameter verwendet.

|Flag|Wert|BESCHREIBUNG|
|----------|-----------|-----------------|
|`SCC_OPT_EVENTQUEUE`|0x00000001L|Legen Sie den Status der Ereigniswarteschlange fest.|
|`SCC_OPT_USERDATA`|0x00000002L|Geben Sie `SCC_OPT_NAMECHANGEPFN`Benutzerdaten für an.|
|`SCC_OPT_HASCANCELMODE`|0x00000003L|Die IDE kann abbrechen.|
|`SCC_OPT_NAMECHANGEPFN`|0x00000004L|Legen Sie einen Rückruf für Namensänderungen fest.|
|`SCC_OPT_SCCCHECKOUTONLY`|0x00000005L|Deaktivieren Sie das Auschecken der Quellcodeverwaltungs-Plug-In-Benutzeroberfläche, und legen Sie kein Arbeitsverzeichnis fest.|
|`SCC_OPT_SHARESUBPROJ`|0x00000006L|Fügen Sie aus dem Quellcodeverwaltungssystem hinzu, um ein Arbeitsverzeichnis anzugeben. Versuchen Sie, das zugeordnete Projekt freizugeben, wenn es sich um ein direktes abhängiges Projekt handelt.|

## <a name="dwval-bitflags"></a>dwVal-Bitflags
 Diese Flags werden von der [SccSetOption](../extensibility/sccsetoption-function.md) im `dwVal` Parameter verwendet.

|Flag|Wert|BESCHREIBUNG|Wird `nOption` nach Wert verwendet|
|----------|-----------|-----------------|-----------------------------|
|`SCC_OPT_EQ_DISABLE`|0x00L|Hält die Ereigniswarteschlangenaktivität an.|`SCC_OPT_EVENTQUEUE`|
|`SCC_OPT_EQ_ENABLE`|0x01L|Aktiviert die Protokollierung der Ereigniswarteschlange.|`SCC_OPT_EVENTQUEUE`|
|`SCC_OPT_HCM_NO`|0L|(Standard) Hat keinen Abbruchmodus; Stecker muss auf Wunsch liefern.|`SCC_OPT_HASCANCELMODE`|
|`SCC_OPT_HCM_YES`|1 L|IDE-Handles abbrechen.|`SCC_OPT_HASCANCELMODE`|
|`SCC_OPT_SCO_NO`|0L|(Standard) OK zum Auschecken von Plug-In-Benutzeroberfläche; Arbeitsverzeichnis festgelegt ist.|`SCC_OPT_SCCCHECKOUTONLY`|
|`SCC_OPT_SCO_YES`|1 L|Kein Plug-In UI Checkout, kein Arbeitsverzeichnis.|`SCC_OPT_SCCCHECKOUTONLY`|

## <a name="see-also"></a>Weitere Informationen
- [Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-ins.md)

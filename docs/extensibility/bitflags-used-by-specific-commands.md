---
title: Bitflags, die von bestimmten Befehlen verwendet | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, bitflags used by specific commands
ms.assetid: 37969977-6f7d-45c9-ba03-1306ae71f5d1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3bc59c79e0f047cc7880332c4c23643ab2136c86
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="bitflags-used-by-specific-commands"></a>Bitflags, die von bestimmten Befehlen verwendet
Das Verhalten einer Reihe von Funktionen in der Quelle Steuerelement-Plug-in-API kann geändert werden, durch einen oder mehrere Bits in einem einzelnen Wert festlegen. Diese Werte werden als Bitflags bezeichnet. Die verschiedenen Bitflags, die von der Quelle Steuerelement-Plug-in-API verwendet werden hier beschrieben gruppiert, die von der Funktion, die sie verwendet.  
  
## <a name="checked-out-flag"></a>Flag ausgecheckt  
 Dieses Flag kann festgelegt werden, entweder die [SccAdd](../extensibility/sccadd-function.md) oder [SccCheckin](../extensibility/scccheckin-function.md).  
  
|Flag|Wert|Beschreibung|  
|----------|-----------|-----------------|  
|`SCC_KEEP_CHECKEDOUT`|0 x 1000|Behalten Sie die Datei ausgecheckt.|  
  
## <a name="add-flags"></a>Hinzufügen von Flags  
 Diese Flags werden verwendet, indem Sie die [SccAdd](../extensibility/sccadd-function.md).  
  
|Flag|Wert|Beschreibung|  
|----------|-----------|-----------------|  
|`SCC_FILETYPE_AUTO`|0 x 00|Die Datenquellen-Steuerelement-Plug-in wird erwartet, automatisch zu erkennen, ob die Datei Text- oder Binärformat.|  
|`SCC_FILETYPE_TEXT`|0 x 01|Dateityp ist Text.|  
|`SCC_FILETYPE_BINARY`|0x04|Dateityp ist binär. **Hinweis:** `SCC_FILETYPE_TEXT` und `SCC_FILETYPE_BINARY` Flags schließen sich gegenseitig.   Legen Sie genau eine oder keines von beiden.|  
|`SCC_ADD_STORELATEST`|0 x 02|Speichern Sie nur die neueste Version (keine Deltas).|  
  
## <a name="diff-flags"></a>Diff-Flags  
 Die [SccDiff](../extensibility/sccdiff-function.md) diese Flags zum Definieren des Gültigkeitsbereichs eines Diff-Vorgangs verwendet. Die `SCC_DIFF_QD_xxx` Flags schließen sich gegenseitig. Wenn eines dieser angegeben ist, existiert keine visuelle Bestätigung gewährt werden. In einer "schnelle"Diff (QD), das plug-in wird nicht zu bestimmen wie die Datei unterscheidet, nur, wenn sie sich unterscheidet. Wenn keines ist dieser Flags angegeben "visual Diff" erfolgt., Detaillierte Dateiunterschiede werden berechnet und angezeigt. Wenn die angeforderte QD nicht unterstützt wird, verschiebt das plug-in mit dem nächsten best. Beispielsweise überprüft, ob die IDE, eine Prüfsumme anfordert und das plug-in nicht wird unterstützt,-Plug-in ist eine vollständige-Inhalt (noch viel schneller als eine visuelle Darstellung).  
  
|Flag|Wert|Beschreibung|  
|----------|-----------|-----------------|  
|`SCC_DIFF_IGNORECASE`|0x0002|Ignorieren von Groß-/Kleinschreibung unterschieden.|  
|`SCC_DIFF_IGNORESPACE`|0x0004|Unterschiede Leerraum zu ignorieren. **Hinweis:** der `SCC_DIFF_IGNORECASE` und `SCC_DIFF_IGNORESPACE` Flags sind optionale Bitflags.|  
|`SCC_DIFF_QD_CONTENTS`|0x0010|QD durch Vergleichen der gesamte Dateiinhalt.|  
|`SCC_DIFF_QD_CHECKSUM`|0x0020|QD von Checksum.|  
|`SCC_DIFF_QD_TIME`|0 x 0040|QD von Datums-/Zeitstempel der Datei.|  
|`SCC_DIFF_QUICK_DIFF`|0x0070|Dies ist eine Maske zum Prüfen auf alle QD Bitflags. Es darf nicht in eine Funktion übergeben werden; die drei QD Bitflags schließen sich gegenseitig aus. QD bedeutet immer ohne Anzeige der Benutzeroberfläche.|  
  
## <a name="populatelist-flag"></a>PopulateList-Flag  
 Dieses Flag wird verwendet, durch die [SccPopulateList](../extensibility/sccpopulatelist-function.md) in der `fOptions` Parameter.  
  
|Flag|Wert|Beschreibung|  
|----------|-----------|-----------------|  
|`SCC_PL_DIR`|0x00000001L|Die IDE übergibt Verzeichnisse, Dateien nicht.|  
  
## <a name="populatedirlist-flags"></a>PopulateDirList-Flags  
 Diese Flags werden verwendet, indem Sie die [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) in der `fOptions` Parameter.  
  
|Optionswert|Wert|Beschreibung|  
|------------------|-----------|-----------------|  
|SCC_PDL_ONELEVEL|0x0000|Untersuchen Sie nur eine Ebene von Verzeichnissen für Verzeichnisse (Dies ist die Standardeinstellung).|  
|SCC_PDL_RECURSIVE|0x0001|Rekursiv überprüfen alle Verzeichnisse in jedem angegebenen Verzeichnis.|  
|SCC_PDL_INCLUDEFILES|0x0002|Schließen Sie Dateinamen ein, bei der Prüfung.|  
  
## <a name="openproject-flags"></a>Projekt öffnen-Flags  
 Diese Flags werden verwendet, indem Sie die [SccOpenProject](../extensibility/sccopenproject-function.md) in der `dwFlags` Parameter.  
  
|Optionswert|Wert|Beschreibung|  
|------------------|-----------|-----------------|  
|SCC_OP_CREATEIFNEW|0x00000001L|Wenn das Projekt in der quellcodeverwaltung nicht vorhanden ist, erstellen Sie ihn aus. Wenn dieses Flag nicht festgelegt ist, fordert Benutzer zum Projekt und erstellen (es sei denn, `SCC_OP_SILENTOPEN` -Flag angegeben ist).|  
|SCC_OP_SILENTOPEN|0x00000002L|Keine benutzeraufforderung zum Erstellen eines Projekts; Rückgabe `SCC_E_UNKNOWNPROJECT`.|  
  
## <a name="get-flags"></a>Abrufen von Flags  
 Diese Flags werden verwendet, indem Sie die [SccGet](../extensibility/sccget-function.md) und [SccCheckout](../extensibility/scccheckout-function.md).  
  
|Flag|Wert|Beschreibung|  
|----------|-----------|-----------------|  
|`SCC_GET_ALL`|0x00000001L|Die IDE Verzeichnisse übergeben wird, nicht die Dateien: Abrufen aller Dateien in diese Verzeichnisse.|  
|`SCC_GET_RECURSIVE`|0x00000002L|Die IDE Verzeichnisse übergeben wird: Rufen Sie diese Verzeichnisse und ihre alle Unterverzeichnisse.|  
  
## <a name="noption-values"></a>nOption Werte  
 Diese Flags werden verwendet, indem Sie die [SccSetOption](../extensibility/sccsetoption-function.md) in der `nOption` Parameter.  
  
|Flag|Wert|Beschreibung|  
|----------|-----------|-----------------|  
|`SCC_OPT_EVENTQUEUE`|0x00000001L|Status der Ereigniswarteschlange festgelegt.|  
|`SCC_OPT_USERDATA`|0x00000002L|Geben Sie die Benutzerdaten für `SCC_OPT_NAMECHANGEPFN`.|  
|`SCC_OPT_HASCANCELMODE`|0x00000003L|Die IDE kann "Abbrechen" verarbeiten.|  
|`SCC_OPT_NAMECHANGEPFN`|0x00000004L|Legen Sie einen Rückruf für Änderungen des Computernamens.|  
|`SCC_OPT_SCCCHECKOUTONLY`|0x00000005L|Deaktivieren von Source Control-Plug-in UI Auschecken, und Arbeitsverzeichnis nicht festlegen.|  
|`SCC_OPT_SHARESUBPROJ`|0x00000006L|Fügen Sie aus dem Quellcodeverwaltungssystem ein Arbeitsverzeichnis angeben. Versuchen Sie es in das zugehörige Projekt freigeben, wenn er direkt untergeordnet ist.|  
  
## <a name="dwval-bitflags"></a>DwVal Bitflags  
 Diese Flags werden verwendet, indem Sie die [SccSetOption](../extensibility/sccsetoption-function.md) in der `dwVal` Parameter.  
  
|Flag|Wert|Beschreibung|Verwendet von `nOption` Wert|  
|----------|-----------|-----------------|-----------------------------|  
|`SCC_OPT_EQ_DISABLE`|0x00L|Hält die Ereignisaktivität-Warteschlange.|`SCC_OPT_EVENTQUEUE`|  
|`SCC_OPT_EQ_ENABLE`|0x01L|Aktiviert die Protokollierung der Ereignis-Warteschlange.|`SCC_OPT_EVENTQUEUE`|  
|`SCC_OPT_HCM_NO`|0L|(Standard) Hat keine Modus "Abbrechen". -Plug-in angeben muss, falls gewünscht.|`SCC_OPT_HASCANCELMODE`|  
|`SCC_OPT_HCM_YES`|1L|IDE behandelt "Abbrechen".|`SCC_OPT_HASCANCELMODE`|  
|`SCC_OPT_SCO_NO`|0L|(Standard) OK, um das Auschecken von UI-Plug-in; Arbeitsverzeichnis festgelegt ist.|`SCC_OPT_SCCCHECKOUTONLY`|  
|`SCC_OPT_SCO_YES`|1L|Keine plug-in UI Auschecken, kein Arbeitsverzeichnis.|`SCC_OPT_SCCCHECKOUTONLY`|  
  
## <a name="see-also"></a>Siehe auch  
 [Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-ins.md)
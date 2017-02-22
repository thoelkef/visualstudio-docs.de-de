---
title: "Bitflags, die von bestimmten Befehlen verwendet | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Quellcode-Plug-ins Bitflags, die von bestimmten Befehlen verwendet"
ms.assetid: 37969977-6f7d-45c9-ba03-1306ae71f5d1
caps.latest.revision: 24
caps.handback.revision: 24
ms.author: "gregvanl"
manager: "ghogen"
---
# Bitflags, die von bestimmten Befehlen verwendet
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Das Verhalten einer Anzahl von Datenquellen\-Steuerelement\-Plug\-in API\-Funktionen kann durch Festlegen von einem oder mehreren Bits in einem einzelnen Wert geändert werden. Diese Werte werden als Bitflags bezeichnet. Die verschiedenen Bitflags, die von der Quelle Steuerelement\-Plug\-in\-API verwendet werden hier beschrieben gruppiert, die von der Funktion, die sie verwendet.  
  
## Flag ausgecheckt  
 Dieses Flag kann festgelegt werden, entweder die [SccAdd](../extensibility/sccadd-function.md) oder [SccCheckin](../extensibility/scccheckin-function.md).  
  
|Flag|Wert|Beschreibung|  
|----------|----------|------------------|  
|`SCC_KEEP_CHECKEDOUT`|0 x 1000|Halten Sie die Datei ausgecheckt haben.|  
  
## Hinzufügen von Flags  
 Diese Flags werden verwendet, indem die [SccAdd](../extensibility/sccadd-function.md).  
  
|Flag|Wert|Beschreibung|  
|----------|----------|------------------|  
|`SCC_FILETYPE_AUTO`|0 x 00|Das Quellcodeverwaltungs\-Plug\-in wird erwartet, automatisch zu erkennen, ob die Datei Text\- oder Binärdaten.|  
|`SCC_FILETYPE_TEXT`|0 x 01|Type ist Text.|  
|`SCC_FILETYPE_BINARY`|0 x 04|Dateityp ist binär. **Note:**  `SCC_FILETYPE_TEXT` und `SCC_FILETYPE_BINARY` Flags gegenseitig. Legen Sie genau eine oder keine.|  
|`SCC_ADD_STORELATEST`|0 x 02|Speichern Sie nur die neueste Version \(keine Deltas\).|  
  
## Diff\-Flags  
 Die [SccDiff](../extensibility/sccdiff-function.md) diese Flags zum Definieren des Gültigkeitsbereichs eines Diff\-Vorgangs verwendet. Die `SCC_DIFF_QD_xxx` Flags gegenseitig. Wenn Sie einen von ihnen angegeben wird, erfolgt kein visuelles Feedback gegeben werden soll. In einer "schnellen"Diff \(%QD\), das plug\-in wird nicht bestimmt, wie die Datei unterscheidet, nur, wenn er sich unterscheidet. Wenn keines dieser Flags angegeben wird "visual Diff" erfolgt; Detaillierte Dateiunterschiede werden berechnet und angezeigt. Wenn die angeforderte %QD nicht unterstützt wird, verschiebt zur nächsten bewährte das plug\-in. Z. B. überprüfen, ob die IDE eine Prüfsumme anfordert und das plug\-in nicht wird unterstützt,\-Plug\-in wird eine vollständige\-Inhalt \(immer noch sehr viel schneller als eine visuelle Darstellung\).  
  
|Flag|Wert|Beschreibung|  
|----------|----------|------------------|  
|`SCC_DIFF_IGNORECASE`|0 x 0002|Unterschiede zu ignorieren.|  
|`SCC_DIFF_IGNORESPACE`|0 x 0004|Ignoriert Leerzeichen Unterschiede. **Note:**  Die `SCC_DIFF_IGNORECASE` und `SCC_DIFF_IGNORESPACE` Flags sind optionale Bitflags.|  
|`SCC_DIFF_QD_CONTENTS`|0x0010|%QD durch Vergleichen der gesamte Dateiinhalt.|  
|`SCC_DIFF_QD_CHECKSUM`|0x0020|%QD von Checksum.|  
|`SCC_DIFF_QD_TIME`|0 x 0040|%QD von Datums\-\/Zeitstempel der Datei.|  
|`SCC_DIFF_QUICK_DIFF`|0x0070|Dies ist eine Maske, die verwendet, um alle %QD Bitflags überprüfen. Es sollte nicht an eine Funktion übergeben werden; die drei %QD Bitflags schließen sich gegenseitig aus. %QD bedeutet immer ohne Anzeige der Benutzeroberfläche.|  
  
## PopulateList\-Flag  
 Dieses Flag wird verwendet, indem die [SccPopulateList](../extensibility/sccpopulatelist-function.md) in der `fOptions` Parameter.  
  
|Flag|Wert|Beschreibung|  
|----------|----------|------------------|  
|`SCC_PL_DIR`|0x00000001L|Die IDE wird Verzeichnisse, Dateien nicht übergeben.|  
  
## PopulateDirList\-Flags  
 Diese Flags werden verwendet, indem die [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) in der `fOptions` Parameter.  
  
|Optionswert|Wert|Beschreibung|  
|-----------------|----------|------------------|  
|SCC\_PDL\_ONELEVEL|0x0000|Überprüfen Sie nur eine Ebene von Verzeichnissen für Verzeichnisse \(Dies ist die Standardeinstellung\).|  
|SCC\_PDL\_RECURSIVE|0 x 0001|Rekursiv überprüfen alle Verzeichnisse in jedem angegebenen Verzeichnis.|  
|SCC\_PDL\_INCLUDEFILES|0 x 0002|Schließen Sie Dateinamen ein, bei der Prüfung.|  
  
## Projekt öffnen\-Flags  
 Diese Flags werden verwendet, indem die [SccOpenProject](../extensibility/sccopenproject-function.md) in der `dwFlags` Parameter.  
  
|Optionswert|Wert|Beschreibung|  
|-----------------|----------|------------------|  
|SCC\_OP\_CREATEIFNEW|0x00000001L|Wenn das Projekt im Datenquellen\-Steuerelement vorhanden ist, erstellen Sie ihn. Wenn dieses Flag nicht festgelegt ist, fordert die Benutzer für Projekt erstellen \(es sei denn, `SCC_OP_SILENTOPEN` \-Flag angegeben ist\).|  
|SCC\_OP\_SILENTOPEN|0x00000002L|Benutzer nicht aufgefordert, ein Projekt zu erstellen; Rückgabe `SCC_E_UNKNOWNPROJECT`.|  
  
## Abrufen von Flags  
 Diese Flags werden verwendet, indem die [SccGet](../extensibility/sccget-function.md) und [SccCheckout](../extensibility/scccheckout-function.md).  
  
|Flag|Wert|Beschreibung|  
|----------|----------|------------------|  
|`SCC_GET_ALL`|0x00000001L|Die IDE ist die Übergabe Verzeichnisse, Dateien und nicht: Abrufen aller Dateien in diesen Verzeichnissen.|  
|`SCC_GET_RECURSIVE`|0x00000002L|Die IDE ist die Übergabe Verzeichnisse: erhalten Sie diese Verzeichnisse und alle ihre Unterverzeichnisse.|  
  
## nOption Werte  
 Diese Flags werden verwendet, indem die [SccSetOption](../extensibility/sccsetoption-function.md) in der `nOption` Parameter.  
  
|Flag|Wert|Beschreibung|  
|----------|----------|------------------|  
|`SCC_OPT_EVENTQUEUE`|0x00000001L|Legen Sie die Status der Ereigniswarteschlange.|  
|`SCC_OPT_USERDATA`|0x00000002L|Geben Sie die Benutzerdaten für `SCC_OPT_NAMECHANGEPFN`.|  
|`SCC_OPT_HASCANCELMODE`|0x00000003L|Die IDE kann Abbrechen verarbeiten.|  
|`SCC_OPT_NAMECHANGEPFN`|0x00000004L|Legen Sie einen Rückruf für ändern.|  
|`SCC_OPT_SCCCHECKOUTONLY`|0x00000005L|Datenquellen\-Steuerelement\-Plug\-in\-Benutzeroberfläche Auschecken deaktivieren, und Arbeitsverzeichnis nicht festlegen.|  
|`SCC_OPT_SHARESUBPROJ`|0x00000006L|Hinzufügen von Quellcode\-Verwaltungssystem ein Arbeitsverzeichnis angeben. Versuchen Sie, in das zugehörige Projekt freigeben, wenn er direkt untergeordnet ist.|  
  
## DwVal Bitflags  
 Diese Flags werden verwendet, indem die [SccSetOption](../extensibility/sccsetoption-function.md) in der `dwVal` Parameter.  
  
|Flag|Wert|Beschreibung|Verwendet von `nOption` Wert|  
|----------|----------|------------------|----------------------------------|  
|`SCC_OPT_EQ_DISABLE`|0x00L|Hält die Ereignisaktivität Warteschlange.|`SCC_OPT_EVENTQUEUE`|  
|`SCC_OPT_EQ_ENABLE`|0x01L|Aktiviert die Protokollierung der Ereignis\-Warteschlange.|`SCC_OPT_EVENTQUEUE`|  
|`SCC_OPT_HCM_NO`|0L|\(Standard\) Verfügt über keine Abbrechen\-Modus. \-Plug\-Ins muss angeben, falls gewünscht.|`SCC_OPT_HASCANCELMODE`|  
|`SCC_OPT_HCM_YES`|1L|IDE behandelt "Abbrechen".|`SCC_OPT_HASCANCELMODE`|  
|`SCC_OPT_SCO_NO`|0L|\(Standard\) OK, um das Auschecken von Plug\-in\-Benutzeroberfläche; Arbeitsverzeichnis festgelegt ist.|`SCC_OPT_SCCCHECKOUTONLY`|  
|`SCC_OPT_SCO_YES`|1L|Keine Plug\-in\-Benutzeroberfläche Auschecken, kein Arbeitsverzeichnis.|`SCC_OPT_SCCCHECKOUTONLY`|  
  
## Siehe auch  
 [Source Control\-Plug\-ins](../extensibility/source-control-plug-ins.md)
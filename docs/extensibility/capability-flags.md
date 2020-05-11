---
title: Fähigkeits-Flags | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, capability flags
ms.assetid: a3f6071c-eac8-4bcd-8ffd-8d0a2d24a252
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9660cbe5a18e82974858fa4d923a38fc73e773f2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739869"
---
# <a name="capability-flags"></a>Fähigkeitsflags
Die SCC_CAP_*xxx-Flags* sind Bitflags, die verwendet werden, um die Funktionen eines Quellcodeverwaltungs-Plug-Ins anzugeben. Die SCC_EXCAP_*xxx-Flags* sind inkrementelle Flags, die erweiterte Funktionen angeben und ganzzahlige Werte auflösen.

|Fähigkeitscode|Wert|BESCHREIBUNG|
|---------------------|-----------|-----------------|
|`SCC_CAP_REMOVE`|0x00000001L|Unterstützt den [Befehl SccRemove](../extensibility/sccremove-function.md) und "Befehl".|
|`SCC_CAP_RENAME`|0x00000002L|Unterstützt den [SccRename](../extensibility/sccrename-function.md) und den Befehl.|
|`SCC_CAP_DIFF`|0x00000004L|Unterstützt den [Befehl SccDiff](../extensibility/sccdiff-function.md) und den Befehl.|
|`SCC_CAP_HISTORY`|0x00000008L|Unterstützt die [SccHistory](../extensibility/scchistory-function.md) und den Befehl.|
|`SCC_CAP_PROPERTIES`|0x00000010L|Unterstützt den Befehl [SccProperties](../extensibility/sccproperties-function.md) und den Befehl.|
|`SCC_CAP_RUNSCC`|0x00000020L|Unterstützt den [Befehl SccRunScc](../extensibility/sccrunscc-function.md) und den Befehl.|
|`SCC_CAP_GETCOMMANDOPTIONS`|0x00000040L|Unterstützt die [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) und den Befehl.|
|`SCC_CAP_QUERYINFO`|0x00000080L|Unterstützt den [Befehl SccQueryInfo](../extensibility/sccqueryinfo-function.md) und den Befehl.|
|`SCC_CAP_GETEVENTS`|0x00000100L|Unterstützt den [Befehl SccGetEvents](../extensibility/sccgetevents-function.md) und den Befehl.|
|`SCC_CAP_GETPROJPATH`|0x00000200L|Unterstützt den [Befehl SccGetProjPath](../extensibility/sccgetprojpath-function.md) und den Befehl.|
|`SCC_CAP_ADDFROMSCC`|0x00000400L|Unterstützt den [Befehl SccAddFromScc](../extensibility/sccaddfromscc-function.md) und den Befehl.|
|`SCC_CAP_COMMENTCHECKOUT`|0x000000800L|Unterstützt einen Kommentar zum Auschecken.|
|`SCC_CAP_COMMENTCHECKIN`|0x00001000L|Unterstützt einen Kommentar zum Einchecken.|
|`SCC_CAP_COMMENTADD`|0x00002000L|Unterstützt einen Kommentar zu Add.|
|`SCC_CAP_COMMENTREMOVE`|0x00004000L|Unterstützt einen Kommentar zu Entfernen.|
|`SCC_CAP_TEXTOUT`|0x00008000L|Schreibt Text in eine von IDE bereitgestellte Ausgabefunktion.|
|`SCC_CAP_ADD_STORELATEST`|0x00200000L|Unterstützt das Speichern von Dateien ohne Deltas.|
|`SCC_CAP_HISTORY_MULTFILE`|0x004000000L|Unterstützt mehrere Dateiverlaufsversionen.|
|`SCC_CAP_IGNORECASE`|0x00800000L|Unterstützt den Dateivergleich bei Groß-/Kleinschreibung.|
|`SCC_CAP_IGNORESPACE`|0x01000000L|Unterstützt den Dateivergleich, der Leerraum ignoriert.|
|`SCC_CAP_POPULATELIST`|0x02000000L|Unterstützt das Suchen zusätzlicher Dateien.|
|`SCC_CAP_COMMENTPROJECT`|0x04000000L|Unterstützt Kommentare zum Erstellen von Projekt.|
|`SCC_CAP_DIFFALWAYS`|0x10000000L|Unterstützt diff in allen Zuständen, wenn unter Kontrolle.|
|`SCC_CAP_GET_NOUI`|0x20000000L|Das Plug-In unterstützt keine Benutzeroberfläche für Get, aber IDE kann dennoch [SccGet](../extensibility/sccget-function.md)aufrufen.|
|`SCC_CAP_REENTRANT`|0x40000000L|Plug-in ist wiedereintretend und threadsicher. In Version 1.0 wurde davon ausgegangen, dass keine Plug-Ins wiedereintretend und threadsicher sind. Wenn ein 1.1-Plug-In dieses Bit festlegt, darf der Host mehrere Projekte parallel öffnen.|

## <a name="capability-bits-added-in-version-12"></a>In Version 1.2 hinzugefügte Funktionsbits

|Fähigkeitscode|Wert|BESCHREIBUNG|
|---------------------|-----------|-----------------|
|`SCC_CAP_CREATESUBPROJECT`|0x00010000L|Unterstützt das [SccCreateSubProject](../extensibility/scccreatesubproject-function.md).|
|`SCC_CAP_GETPARENTPROJECT`|0x00020000L|Unterstützt [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md).|
|`SCC_CAP_BATCH`|0x00040000L|Unterstützt [SccBeginBatch](../extensibility/sccbeginbatch-function.md) und [SccEndBatch](../extensibility/sccendbatch-function.md).|
|`SCC_CAP_DIRECTORYSTATUS`|0x00080000L|Unterstützt [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md).|
|`SCC_CAP_DIRECTORYDIFF`|0x00100000L|Unterstützt [sccDirDiff](../extensibility/sccdirdiff-function.md).|
|`SCC_CAP_MULTICHECKOUT`|0x08000000L|Unterstützt mehrere Auscheckungen in einer Datei und der [SccIsMultiCheckoutEnabled](../extensibility/sccismulticheckoutenabled-function.md).|
|`SCC_CAP_SCCFILE`|0x80000000L|Unterstützt die *MSSCCPRJ.SCC-Datei* (vorbehaltlich der Benutzer-/Administrator-Override) und die [SccWillCreateSccFile](../extensibility/sccwillcreatesccfile-function.md).|

## <a name="capability-bits-added-in-version-13"></a>In Version 1.3 hinzugefügte Funktionsbits
 Diese Flags werden nacheinander an die [SccGetExtendedCapabilities-Funktion](../extensibility/sccgetextendedcapabilities-function.md) übergeben, um zu bestimmen, ob die Funktion unterstützt wird.

|Erweiterter Fähigkeitscode|Wert|BESCHREIBUNG|
|------------------------------|-----------|-----------------|
|`SCC_EXCAP_CHECKOUT_LOCALVER`|1|Unterstützt `SCC_CHECKOUT_LOCALVER` die Option für Auschecken.|
|`SCC_EXCAP_BACKGROUND_GET`|2|Unterstützt [sccBackgroundGet](../extensibility/sccbackgroundget-function.md).|
|`SCC_EXCAP_ENUM_CHANGED_FILES`|3|Unterstützt die [SccEnumChangedFiles](../extensibility/sccenumchangedfiles-function.md).|
|`SCC_EXCAP_POPULATELIST_DIR`|4|Unterstützt das Suchen zusätzlicher Verzeichnisse.|
|`SCC_EXCAP_QUERYCHANGES`|5|Unterstützt das Aufzählen von Dateiänderungen.|
|`SCC_EXCAP_ADD_FILES_FROM_SCC`|6|Unterstützt [SccAddFilesFromSCC](../extensibility/sccaddfilesfromscc-function.md).|
|`SCC_EXCAP_GET_USER_OPTIONS`|7|Unterstützt die [SccGetUserOption](../extensibility/sccgetuseroption-function.md).|
|`SCC_EXCAP_THREADSAFE_QUERY_INFO`|8|Unterstützt das Aufrufen von SccQueryInfo auf mehreren Threads.|
|`SCC_EXCAP_REMOVE_DIR`|9|Unterstützt die SccRemoveDir-Funktion.|
|`SCC_EXCAP_DELETE_CHECKEDOUT`|10|Kann ausgecheckte Dateien löschen.|
|`SCC_EXCAP_RENAME_CHECKEDOUT`|11|Kann ausgecheckte Dateien umbenennen.|

## <a name="see-also"></a>Weitere Informationen
- [Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-ins.md)

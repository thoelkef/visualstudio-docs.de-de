---
title: Vergleichen des Projektordners mit dem Quellcodeverwaltungsspeicher | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, comparing versions
- source control plug-ins, local project folders
ms.assetid: 65217e8b-15a6-4446-92b0-4cff1c6220f5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: facb3b656e0ac50b50fdb0291307aa2fe98b1df4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706865"
---
# <a name="optional-comparison-of-local-project-folder-to-source-control-store"></a>Optionaler Vergleich des lokalen Projektordners mit dem Speicher der Quellcodeverwaltung
In der Quellcodeverwaltung Plug-in API 1.2 wird der Vergleich zwischen dem lokalen Projektordner und der Quellcodeverwaltung mithilfe der Funktionen [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md) und [SccDirDiff](../../extensibility/sccdirdiff-function.md)durchgeführt.

 Wenn im **Projektmappen-Explorer**anstelle einer einzelnen Datei ein Ordner ausgewählt ist, ruft das Kontextmenü **Versionen vergleichen** die neuen [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md) und [SccDirDiff](../../extensibility/sccdirdiff-function.md) im Quellcodeverwaltungs-Plug-In auf.

## <a name="new-capability-flags"></a>Neue Funktionsflags
 `SCC_CAP_DIRECTORYDIFF`

 `SCC_CAP_DIRECTORYCHECKOUT`

## <a name="new-functions"></a>Neue Funktionen
- [SccDirDiff](../../extensibility/sccdirdiff-function.md)

- [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md)

 Die `SccDirQueryInfo` Funktion wird `SccDirDiff` zuvor aufgerufen, um zu bestimmen, ob das Arbeitsverzeichnis von der Quelle gesteuert wird. Die `SccDirDiff` Funktion zeigt die Unterschiede zwischen dem aktuellen lokalen Verzeichnis und dem entsprechenden Quellcodeverwaltungsordner an. Dieser Befehl fordert das Quellcodeverwaltungs-Plug-In auf, die Liste der Änderungen am Verzeichnis anzuzeigen. Ein Quellcodeverwaltungs-Plug-In stellt eine eigene Benutzeroberfläche bereit, um die Unterschiede anzuzeigen.

> [!NOTE]
> Diese Funktion verwendet dieselben Befehlsflags wie [SccDiff](../../extensibility/sccdiff-function.md). Als Quellcodeverwaltungs-Plug-In-Anbieter können Sie den "Quick Diff"-Vorgang für Verzeichnisse nicht unterstützen.

## <a name="see-also"></a>Weitere Informationen
- [Neuigkeiten in API-Version 1.2 des Quellcodeverwaltungs-Plug-Ins](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)

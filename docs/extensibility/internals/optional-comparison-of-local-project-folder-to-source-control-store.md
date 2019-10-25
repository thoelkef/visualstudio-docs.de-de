---
title: Projektordner mit Quellcode-Steuerungs Speicher vergleichen | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, comparing versions
- source control plug-ins, local project folders
ms.assetid: 65217e8b-15a6-4446-92b0-4cff1c6220f5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 45bd5b105a2fd24078bc85d8cf5b044351cd78be
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72726126"
---
# <a name="optional-comparison-of-local-project-folder-to-source-control-store"></a>Optionaler Vergleich des lokalen Projektordners mit dem Speicher der Quellcodeverwaltung
In der Quellcodeverwaltungs-Plug-in-API 1,2 wird der Vergleich zwischen dem lokalen Projektordner und der Quell Code Verwaltung mithilfe der Funktionen [sccdirqueryinfo](../../extensibility/sccdirqueryinfo-function.md) und [sccdirdiff](../../extensibility/sccdirdiff-function.md)durchgeführt.

 Wenn Sie in **Projektmappen-Explorer**einen Ordner anstelle einer einzelnen Datei auswählen, ruft das Kontextmenü für die **Vergleichs Versionen** das neue [sccdirqueryinfo](../../extensibility/sccdirqueryinfo-function.md) -und [sccdirdiff](../../extensibility/sccdirdiff-function.md) -Element im Quellcodeverwaltungs-Plug-in auf.

## <a name="new-capability-flags"></a>Neue funktionsflags
 `SCC_CAP_DIRECTORYDIFF`

 `SCC_CAP_DIRECTORYCHECKOUT`

## <a name="new-functions"></a>Neue Funktionen
- [SccDirDiff](../../extensibility/sccdirdiff-function.md)

- [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md)

 Die `SccDirQueryInfo`-Funktion wird vor `SccDirDiff` aufgerufen, um zu bestimmen, ob das Arbeitsverzeichnis Quell gesteuert ist. Die `SccDirDiff`-Funktion zeigt die Unterschiede zwischen dem aktuellen lokalen Verzeichnis und dem entsprechenden Ordner für die Quell Code Verwaltung an. Dieser Befehl fordert das Quellcodeverwaltungs-Plug-in auf, die Liste der Änderungen im Verzeichnis anzuzeigen. Ein Quellcodeverwaltungs-Plug-in stellt eine eigene Benutzeroberfläche zum Anzeigen der Unterschiede bereit.

> [!NOTE]
> Diese Funktion verwendet die gleichen [Befehlsflags wie sccdiff](../../extensibility/sccdiff-function.md). Als Anbieter von Quellcodeverwaltungs-Plug-Ins können Sie den Vorgang für die schnelle diff-Ausführung für Verzeichnisse nicht unterstützen.

## <a name="see-also"></a>Siehe auch
- [Neuigkeiten in API-Version 1.2 des Quellcodeverwaltungs-Plug-Ins](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
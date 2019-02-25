---
title: Vergleichen des Projektordners mit dem Datenquellen-Steuerelement Store | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, comparing versions
- source control plug-ins, local project folders
ms.assetid: 65217e8b-15a6-4446-92b0-4cff1c6220f5
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5ac710fd3994dca24d8e15e3d15c18d9f456a744
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56614193"
---
# <a name="optional-comparison-of-local-project-folder-to-source-control-store"></a>Optionaler Vergleich des lokalen Projektordners mit dem Speicher der Quellcodeverwaltung
Steuern Sie in der Quelle der Vergleich zwischen dem lokalen Projektordner und die Datenquellen-Steuerelements erreicht wird, indem Sie mithilfe der Funktionen-Plug-in-API-1.2 [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md) und [SccDirDiff](../../extensibility/sccdirdiff-function.md).

 In **Projektmappen-Explorer**, wenn ein Ordner, anstatt eine einzelne Datei ausgewählt ist, die **Versionsvergleich** Kontextmenü Ruft die neue [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md) und [ SccDirDiff](../../extensibility/sccdirdiff-function.md) in das Quellcodeverwaltungs-Plug-in.

## <a name="new-capability-flags"></a>Neue Funktionsflags
 `SCC_CAP_DIRECTORYDIFF`

 `SCC_CAP_DIRECTORYCHECKOUT`

## <a name="new-functions"></a>Neue Funktionen
- [SccDirDiff](../../extensibility/sccdirdiff-function.md)

- [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md)

 Die `SccDirQueryInfo` Funktion wird aufgerufen, bevor `SccDirDiff` zu bestimmen, ob das Arbeitsverzeichnis der quellcodeverwaltung unterliegende ist. Die `SccDirDiff` Funktion zeigt die Unterschiede zwischen der aktuellen lokalen Verzeichnis und den entsprechenden Quellcode-Verwaltungsordner an. Dieser Befehl fordert das Quellcodeverwaltungs-Plug-in die Liste der Änderungen in das Verzeichnis anzuzeigen. Ein Quellcodeverwaltungs-Plug-in bietet eine eigene Benutzeroberfläche zum Anzeigen der Unterschiede.

> [!NOTE]
>  Diese Funktion verwendet die gleichen Befehlsflags als [SccDiff](../../extensibility/sccdiff-function.md). Als ein Plug-in-Quellcodeverwaltungsanbieter können Sie die "schnelle Diff"-Vorgang für Verzeichnisse wird nicht unterstützt.

## <a name="see-also"></a>Siehe auch
- [Neuigkeiten in API-Version 1.2 des Quellcodeverwaltungs-Plug-Ins](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
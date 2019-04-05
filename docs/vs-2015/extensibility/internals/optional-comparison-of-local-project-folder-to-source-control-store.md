---
title: Optionaler Vergleich des lokalen Projektordners mit Source Control Store | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, comparing versions
- source control plug-ins, local project folders
ms.assetid: 65217e8b-15a6-4446-92b0-4cff1c6220f5
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 34b9a7ff7d4cc70863090957060db90edfd016b5
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58956644"
---
# <a name="optional-comparison-of-local-project-folder-to-source-control-store"></a>Optionaler Vergleich des lokalen Projektordners mit dem Speicher der Quellcodeverwaltung
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Steuern Sie in der Quelle der Vergleich zwischen dem lokalen Projektordner und die Datenquellen-Steuerelements erreicht wird, indem Sie mithilfe der Funktionen-Plug-in-API-1.2 [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md) und [SccDirDiff](../../extensibility/sccdirdiff-function.md).  
  
 In **Projektmappen-Explorer**, wenn ein Ordner, anstatt eine einzelne Datei ausgewählt ist, die **Versionsvergleich** Kontextmenü Ruft die neue [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md) und [ SccDirDiff](../../extensibility/sccdirdiff-function.md) in das Quellcodeverwaltungs-Plug-in.  
  
## <a name="new-capability-flags"></a>Neue Funktionsflags  
 `SCC_CAP_DIRECTORYDIFF`  
  
 `SCC_CAP_DIRECTORYCHECKOUT`  
  
## <a name="new-functions"></a>Neue Funktionen  
 [SccDirDiff](../../extensibility/sccdirdiff-function.md)  
  
 [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md)  
  
 Die `SccDirQueryInfo` Funktion wird aufgerufen, bevor `SccDirDiff` zu bestimmen, ob das Arbeitsverzeichnis der quellcodeverwaltung unterliegende ist. Die `SccDirDiff` Funktion zeigt die Unterschiede zwischen der aktuellen lokalen Verzeichnis und den entsprechenden Quellcode-Verwaltungsordner an. Dieser Befehl fordert das Quellcodeverwaltungs-Plug-in die Liste der Änderungen in das Verzeichnis anzuzeigen. Ein Quellcodeverwaltungs-Plug-in bietet eine eigene Benutzeroberfläche zum Anzeigen der Unterschiede.  
  
> [!NOTE]
>  Diese Funktion verwendet die gleichen Befehlsflags als [SccDiff](../../extensibility/sccdiff-function.md). Als ein Plug-in-Quellcodeverwaltungsanbieter können Sie die "schnelle Diff"-Vorgang für Verzeichnisse wird nicht unterstützt.  
  
## <a name="see-also"></a>Siehe auch  
 [Neuigkeiten in API-Version 1.2 des Quellcodeverwaltungs-Plug-Ins](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)

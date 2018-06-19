---
title: Vergleichen von Projektordner auf den Speicher der Quellcodeverwaltung | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, comparing versions
- source control plug-ins, local project folders
ms.assetid: 65217e8b-15a6-4446-92b0-4cff1c6220f5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2e0f6f2185385ee7ec3942556a43f58d43e7a4da
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31130570"
---
# <a name="optional-comparison-of-local-project-folder-to-source-control-store"></a>Optionale Vergleich der lokalen Projektordner auf den Speicher der Quellcodeverwaltung
Steuern Sie in der Quelle-Plug-in-API 1.2, die der Vergleich zwischen dem lokalen Projektordner und Datenquellen-Steuerelements erreicht wird, indem Sie mit den Funktionen [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md) und [SccDirDiff](../../extensibility/sccdirdiff-function.md).  
  
 In **Projektmappen-Explorer**, wenn Sie ein Ordner ausgewählt ist, anstatt eine einzelne Datei die **Versionsvergleich** Kontextmenü Ruft die neue [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md) und [ SccDirDiff](../../extensibility/sccdirdiff-function.md) im Datenquellen-Steuerelement-Plug-in.  
  
## <a name="new-capability-flags"></a>Neue Funktion Flags  
 `SCC_CAP_DIRECTORYDIFF`  
  
 `SCC_CAP_DIRECTORYCHECKOUT`  
  
## <a name="new-functions"></a>Neue Funktionen  
 [SccDirDiff](../../extensibility/sccdirdiff-function.md)  
  
 [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md)  
  
 Die `SccDirQueryInfo` Funktion wird aufgerufen, bevor `SccDirDiff` zu bestimmen, ob das Arbeitsverzeichnis quellcodeverwaltete ist. Die `SccDirDiff` Funktion zeigt die Unterschiede zwischen der aktuellen lokalen Verzeichnis und die entsprechenden Quellverwaltungsordner. Dieser Befehl fordert das Quellsteuerelement-Plug-in die Liste der Änderungen in das Verzeichnis anzuzeigen. Ein Quellcodeverwaltungs-Plug-in bietet eine eigene Benutzeroberfläche zum Anzeigen der Unterschiede.  
  
> [!NOTE]
>  Diese Funktion verwendet die gleichen Befehlsflags als [SccDiff](../../extensibility/sccdiff-function.md). Ein Quellcodeverwaltungs-Plug-in-Anbieter können Sie auswählen, dass die "schnelle" Vergleichsvorgang für Verzeichnisse nicht unterstützt.  
  
## <a name="see-also"></a>Siehe auch  
 [Neuigkeiten in API-Version 1.2 des Quellcodeverwaltungs-Plug-Ins](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
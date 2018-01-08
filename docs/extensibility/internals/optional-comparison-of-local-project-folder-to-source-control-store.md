---
title: Vergleichen von Projektordner auf den Speicher der Quellcodeverwaltung | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control plug-ins, comparing versions
- source control plug-ins, local project folders
ms.assetid: 65217e8b-15a6-4446-92b0-4cff1c6220f5
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: cbf4e9f2ccbe895db79115949818345c62245f71
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
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
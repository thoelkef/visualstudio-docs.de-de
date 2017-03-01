---
title: Vergleichen der Projektordner auf Source Control Store | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control plug-ins, comparing versions
- source control plug-ins, local project folders
ms.assetid: 65217e8b-15a6-4446-92b0-4cff1c6220f5
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: d5bc147592bfc36247c35f23ac2885055d096af3
ms.openlocfilehash: b2ed6955e5ba6fa334cc89a0c2ea8a3d4248f362
ms.lasthandoff: 02/22/2017

---
# <a name="optional-comparison-of-local-project-folder-to-source-control-store"></a>Optionale Vergleich der lokalen Projektordner Source Control Store
Steuern, in der Quelle-Plug-in-API 1.2 der Vergleich zwischen dem lokalen Ordner und Datenquellen-Steuerelement erfolgt mit den Funktionen [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md) und [SccDirDiff](../../extensibility/sccdirdiff-function.md).  
  
 In **Projektmappen-Explorer**, wenn ein Ordner, anstatt eine einzelne Datei ausgewählt ist, die **Versionen vergleichen** Kontextmenü Ruft die neue [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md) und [SccDirDiff](../../extensibility/sccdirdiff-function.md) in das Quellcodeverwaltungs-Plug-in.  
  
## <a name="new-capability-flags"></a>Neue Capability Flags  
 `SCC_CAP_DIRECTORYDIFF`  
  
 `SCC_CAP_DIRECTORYCHECKOUT`  
  
## <a name="new-functions"></a>Neue Funktionen  
 [SccDirDiff](../../extensibility/sccdirdiff-function.md)  
  
 [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md)  
  
 Die `SccDirQueryInfo` Funktion aufgerufen wird, bevor `SccDirDiff` bestimmt, ob das Arbeitsverzeichnis quellcodeverwaltete ist. Die `SccDirDiff` -Funktion zeigt die Unterschiede zwischen der aktuellen lokalen Verzeichnis und den entsprechenden Quellcode-Verwaltungsordner. Dieser Befehl fordert das Quellcodeverwaltungs-Plug-in die Liste der Änderungen in das Verzeichnis anzuzeigen. Ein Quellcodeverwaltungs-Plug-in bietet eine eigene Benutzeroberfläche zum Anzeigen der Unterschiede.  
  
> [!NOTE]
>  Diese Funktion verwendet die gleichen Befehlsflags als [SccDiff](../../extensibility/sccdiff-function.md). Als plug-in Quellcodeverwaltungsanbieter können Sie die "schnellen" Vergleichsvorgang für Verzeichnisse nicht unterstützt.  
  
## <a name="see-also"></a>Siehe auch  
 [Was ist neu in Source Control-Plug-in API-Version 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)

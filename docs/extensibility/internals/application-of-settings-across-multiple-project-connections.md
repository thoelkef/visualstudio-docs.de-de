---
title: "Anwendung der Einstellungen über mehrere Project-Verbindungen | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: source control plug-ins, application of settings
ms.assetid: 2116d3d0-c46c-4d0a-b482-08a178584f46
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9750d946a941e86a6c0a6973661f00f8f44cf9b5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="application-of-settings-across-multiple-project-connections"></a>Anwendung der Einstellungen über mehrere Project-Verbindungen
Ein Quellcodeverwaltungs-Plug-in kann mithilfe des Datenquellen-Steuerelement-Plug-in-API 1.2 erstellt einen Batchvorgang mithilfe der gleichen Quelle-Steuerungsvorgang über mehrere Projekte oder mehrere Verbindung Kontexte hinweg ausführen. Batches können zum Entfernen der redundante pro Projekt Dialogfelder von erforderlichen Erfahrungsgrad des Benutzers verwendet werden.  
  
 Wenn ein Benutzer mehrere Elemente, die mehr als eine Verbindung in ein Quellcodeverwaltungs-Plug-in erstellt wählt, mit der Quelle Steuerelement-Plug-in-API 1.1, (z. B. zwei Webprojekte auf Computern mit verschiedenen Dateifreigabe) angehören, und werden überprüft, kann der Benutzer im selben Dialogfeld sehen. wiederholt. Dies geschieht auch, wenn der Benutzer klickt auf die **anwenden auf alle** Kontrollkästchen im Dialogfeld, da die IDE den Zustand für jede Verbindungskontext zurückgesetzt.  
  
## <a name="new-capability-flag"></a>Neue Funktion-Flag  
 `SccBeginBatch`Funktion legt die `SCC_CAP_BATCH` Flag, um anzugeben, dass ein Batch ausgeführt wird  
  
## <a name="new-functions"></a>Neue Funktionen  
 Die folgenden neuen Funktionen unterstützen den Batchvorgang:  
  
-   [SccBeginBatch](../../extensibility/sccbeginbatch-function.md)  
  
-   [SccEndBatch](../../extensibility/sccendbatch-function.md)  
  
 Die `SCCBeginBatch` Funktion beginnt, eine Gruppe von Quellcodeverwaltungsvorgänge. `SccEndBatch`Schließt die Gruppe an. Gruppen können nicht geschachtelt werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Neuigkeiten in API-Version 1.2 des Quellcodeverwaltungs-Plug-Ins](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
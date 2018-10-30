---
title: Anwendung von Einstellungen auf mehrere Projektverbindungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source control plug-ins, application of settings
ms.assetid: 2116d3d0-c46c-4d0a-b482-08a178584f46
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7f848c64072ebd77dfa3494b5dfc390c34855948
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49940852"
---
# <a name="application-of-settings-across-multiple-project-connections"></a>Anwendung von Einstellungen auf mehrere Projektverbindungen
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ein Quellcodeverwaltungs-Plug-In können mithilfe des Datenquellen-Steuerelement-Plug-in-API 1.2, erstellt einen Batchvorgang den gleichen Quellcodeverwaltungsvorgang über mehrere Projekte oder mehrere Verbindung Kontexte ausgeführt. Batches können zum Eliminieren Sie redundante projektbezogene Dialogfelder, die von der Benutzeroberfläche verwendet werden.  
  
 Wenn ein Benutzer mehrere Elemente, die mehr als eine Verbindung in ein Quellcodeverwaltungs-Plug-in erstellt wählt, mit Source Control-Plug-in-API 1.1, (z. B. zwei Webprojekten auf Computern mit verschiedenen Dateifreigabe) angehören, und sie überprüft, werden dem Benutzer im gleichen Dialogfeld angezeigt. wiederholt. Dies geschieht auch, wenn der Benutzer klickt auf die **auf alle anwenden** Kontrollkästchen im Dialogfeld, da die IDE den Zustand für jede Verbindungskontext zurückgesetzt.  
  
## <a name="new-capability-flag"></a>Neue Funktion-Flag  
 `SccBeginBatch` Funktion legt die `SCC_CAP_BATCH` Flags an, dass ein Batchvorgang ausgeführt wird  
  
## <a name="new-functions"></a>Neue Funktionen  
 Die folgenden neuen Funktionen unterstützen den Batchvorgang:  
  
- [SccBeginBatch](../../extensibility/sccbeginbatch-function.md)  
  
- [SccEndBatch](../../extensibility/sccendbatch-function.md)  
  
  Die `SCCBeginBatch` Funktion startet eine Gruppe von Quellcodeverwaltungsvorgänge. `SccEndBatch` Schließt die Gruppe an. Gruppen können nicht geschachtelt werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Neuigkeiten in API-Version 1.2 des Quellcodeverwaltungs-Plug-Ins](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)


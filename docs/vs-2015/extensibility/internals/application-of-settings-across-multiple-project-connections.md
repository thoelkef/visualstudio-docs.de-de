---
title: Anwendung von Einstellungen über mehrere Projekt Verbindungen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, application of settings
ms.assetid: 2116d3d0-c46c-4d0a-b482-08a178584f46
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bca17fdc440fc373d0d4811ed57cd5d27a6c201a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203847"
---
# <a name="application-of-settings-across-multiple-project-connections"></a>Anwendung von Einstellungen auf mehrere Projektverbindungen
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ein Quellcodeverwaltungs-Plug-in, das mit der Quellcodeverwaltungs-Plug-in-API 1,2 erstellt wurde, kann einen Batch Vorgang verwenden, um denselben Quell Code Verwaltungsvorgang für mehrere Projekte oder mehrere Verbindungs Kontexte auszuführen. Batches können verwendet werden, um redundante, pro Projekt geeignete Dialogfelder aus der Benutzer Darstellung auszuschließen.  
  
 Wenn ein Benutzer mehrere Elemente auswählt, die zu mehreren Verbindungen in einem Quellcodeverwaltungs-Plug-in gehören, das mithilfe der Quellcodeverwaltungs-Plug-in-API 1,1 erstellt wurde, (z. b. zwei Webprojekte auf verschiedenen Dateifreigabe Computern), wird das gleiche Dialogfeld wiederholt angezeigt. Dies geschieht selbst dann, wenn der Benutzer im Dialogfeld auf das Kontrollkästchen **für alle** übernehmen klickt, weil die IDE den Zustand für jeden Verbindungs Kontext zurücksetzt.  
  
## <a name="new-capability-flag"></a>Neues funktionsflag  
 `SccBeginBatch` Die Funktion legt das `SCC_CAP_BATCH` Flag fest, um anzugeben, dass ein Batch Vorgang ausgeführt wird.  
  
## <a name="new-functions"></a>Neue Funktionen  
 Die folgenden neuen Funktionen unterstützen den Batch-Vorgang:  
  
- [SccBeginBatch](../../extensibility/sccbeginbatch-function.md)  
  
- [SccEndBatch](../../extensibility/sccendbatch-function.md)  
  
  Die- `SCCBeginBatch` Funktion startet eine Gruppe von Quell Code Verwaltungs Vorgängen. `SccEndBatch` schließt die Gruppe. Die Gruppen dürfen nicht gruppiert werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Neuigkeiten in API-Version 1.2 des Quellcodeverwaltungs-Plug-Ins](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)

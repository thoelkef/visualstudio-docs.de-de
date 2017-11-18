---
title: Projekt Kontext | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: projects [Visual Studio SDK], opening items
ms.assetid: d1803f4a-24eb-44b0-b5d2-cb40c15534be
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 368f6ecb67bc8b01df975da6e68e95b553a0e31d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="project-context"></a>Projektkontext
Wenn der Benutzer hinzugefügt oder mit Projekten und Projektelementen funktioniert, verwendet die IDE das Konzept von Projektkontext, um zu bestimmen, wie verschiedene Vorgänge ausgeführt werden soll.  
  
 Dateien werden in der Regel die standard-Projekt-Objekte, die der Benutzer explizit dazu erstellt die **neues Projekt** Befehl oder durch Auswahl zur Verfügung stellt die **Projekt öffnen** Befehl die  **Datei** Menü. In diesen Fällen Dateien erstellt und im Kontext eines Projekts geöffnet sind und der Projekttyp definiert den Kontext für die Bearbeitung des Dokuments.  
  
 Manche Projekte bieten einen sehr umfangreichen Kontext. Das Projekt z. B. verwaltet, einen Projektumfang, programmseitige-Namespace oder Projektumfang datenbankverbindung für die Datenbindung. Der Benutzer kann häufig Datenbankverbindungen Öffnen von Dateien oder direkt mithilfe eines bestimmten Projekts-Objekts, beispielsweise ein Projektelement im Projektmappen-Explorer angezeigt.  
  
 Zu anderen Zeiten des Projektkontexts eines Elements nicht explizit angegeben. Z. B. der Kontext eines Elements ist nicht verfügbar, wenn der Benutzer durch auswählen eine Datei öffnet die **vorhandene Datei öffnen** Befehl die **Datei** Menü, wenn der Debugger ausgeführt wird, auf eine Datei, oder wenn der Benutzer klickt auf die **In Dateien suchen** -Befehl in der **suchen und Ersetzen** (Dialogfeld). Zu diesen Situationen die Aufrufe der IDE behandeln <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument> zum Ermitteln der best-Projekt, ein Dokument öffnen zu verwalten.  
  
## <a name="see-also"></a>Siehe auch  
 [Projektpriorität](../../extensibility/internals/project-priority.md)   
 [Hinzufügen von Projekt- und Projektelementvorlagen](../../extensibility/internals/adding-project-and-project-item-templates.md)
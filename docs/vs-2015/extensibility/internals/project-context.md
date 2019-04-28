---
title: Projekt-Kontext | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: d1803f4a-24eb-44b0-b5d2-cb40c15534be
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d4ee4da5fdea63cf1bdd33554c72f6dac30d0334
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62429937"
---
# <a name="project-context"></a>Projektkontext
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Wenn der Benutzer hinzufügt, oder es mit Projekten und Projektelementen funktioniert, verwendet die IDE das Konzept der Projektkontext, um zu bestimmen, wie verschiedene Vorgänge ausgeführt werden soll.  
  
 Dateien sind in der Regel die standard-Projekt-Objekte, die der Benutzer explizit dazu erstellt das **neues Projekt** Befehl oder durch Auswahl zur Verfügung. die **Projekt öffnen** Befehl der  **Datei** Menü. In diesen Fällen Dateien erstellt und im Kontext eines Projekts geöffnet, und der Projekttyp definiert den Kontext für die Bearbeitung des Dokuments.  
  
 Einige Projekte bieten eine sehr umfassende Kontextdaten. Das Projekt z. B. verwaltet, einen Projektumfang, programmgesteuerte-Namespace oder ein Projekt abgestimmten datenbankverbindung für die Datenbindung. Der Benutzer kann häufig Dateien oder Verbindungen mit der Datenbank öffnen, direkt unter Verwendung eines bestimmten Projekts-Objekts, z.B. ein Projektelement im Projektmappen-Explorer angezeigt.  
  
 In anderen Fällen ist dem Projektkontext eines Elements nicht explizit angegeben. Beispielsweise im Rahmen eines Elements ist nicht verfügbar, wenn der Benutzer dazu auf eine Datei geöffnet wird die **vorhandene Datei öffnen** Befehl die **Datei** Menü, wenn der Debugger ausgeführt wird, auf eine Datei oder klickt der Benutzer die **In Dateien suchen** -Befehl in der **suchen und Ersetzen** Dialogfeld. Zu diesen Situationen können die IDE-Aufrufe verarbeiten <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument> zum Verwalten der Vorgang des Ermittelns der besten-Projekts, ein Dokument zu öffnen.  
  
## <a name="see-also"></a>Siehe auch  
 [Projektpriorität](../../extensibility/internals/project-priority.md)   
 [Hinzufügen von Projekt- und Projektelementvorlagen](../../extensibility/internals/adding-project-and-project-item-templates.md)

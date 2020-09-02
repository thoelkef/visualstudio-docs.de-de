---
title: Projektkontext | Microsoft-Dokumentation
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62429937"
---
# <a name="project-context"></a>Projektkontext
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Wenn der Benutzer Projekte und Projekt Elemente hinzufügt oder damit arbeitet, verwendet die IDE das Konzept des Projekt Kontexts, um zu bestimmen, wie verschiedene Vorgänge ausgeführt werden sollen.  
  
 In der Regel handelt es sich bei Dateien um die Standard Projekt Objekte, die der Benutzer explizit erstellt, indem er den Befehl " **Neues Projekt** " oder den Befehl " **Projekt öffnen** " im Menü **Datei** auswählt. In diesen Fällen werden Dateien im Kontext eines Projekts erstellt und geöffnet, und der Projekttyp definiert den Kontext für die Bearbeitung des Dokuments.  
  
 Einige Projekte bieten einen sehr umfangreichen Kontext. Das Projekt verwaltet z. b. einen projektbezogenen, programmatischen Namespace oder eine projektbezogene Datenbankverbindung für die Datenbindung. Der Benutzer kann Dateien oder Datenbankverbindungen häufig direkt mithilfe eines bestimmten Projekt Objekts öffnen, z. b. eines in Projektmappen-Explorer angezeigten Projekt Elements.  
  
 Zu anderen Zeiten wird der Projektkontext eines Elements nicht explizit angegeben. Beispielsweise ist der Kontext eines Elements nicht verfügbar, wenn der Benutzer eine Datei öffnet, indem er den Befehl **vorhandene Datei öffnen** im Menü **Datei** auswählt, wenn der Debugger mit einer Datei arbeitet oder wenn der Benutzer im Dialogfeld **Suchen und ersetzen** auf den Befehl **in Dateien suchen** klickt. Um diese Situationen zu behandeln, ruft die IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument> auf, um den Prozess der Suche nach dem besten Projekt zum Öffnen eines Dokuments zu verwalten.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Projekt Priorität](../../extensibility/internals/project-priority.md)   
 [Hinzufügen von Projekt- und Projektelementvorlagen](../../extensibility/internals/adding-project-and-project-item-templates.md)

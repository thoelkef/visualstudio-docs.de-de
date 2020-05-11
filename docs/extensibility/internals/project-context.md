---
title: Projektkontext | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: d1803f4a-24eb-44b0-b5d2-cb40c15534be
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 51e411f0bca361f96cdffcfd89498908fd21d441
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706588"
---
# <a name="project-context"></a>Projektkontext
Wenn der Benutzer Projekte und Projektelemente hinzufügt oder mit ihnen arbeitet, verwendet die IDE den Begriff des Projektkontexts, um zu bestimmen, wie verschiedene Vorgänge ausgeführt werden sollen.

 In der Regel sind Dateien die Standardprojektobjekte, die der Benutzer explizit erstellt, indem er den Befehl **Neues Projekt** auswählt oder durch Auswahl des Befehls **Projekt öffnen** im Menü **Datei** verfügbar macht. In diesen Fällen werden Dateien im Kontext eines Projekts erstellt und geöffnet, und der Projekttyp definiert den Kontext für die Bearbeitung des Dokuments.

 Einige Projekte bieten einen sehr reichhaltigen Kontext. Das Projekt verwaltet z. B. eine projektbezogene, programmgesteuerte Namespace- oder projektbezogene Datenbankverbindung für die Datenbindung. Der Benutzer kann Dateien oder Datenbankverbindungen häufig direkt öffnen, indem er ein bestimmtes Projektobjekt verwendet, z. B. ein Projektelement, das im Projektmappen-Explorer angezeigt wird.

 Zu anderen Zeiten wird der Projektkontext eines Elements nicht explizit angegeben. Beispielsweise ist der Kontext eines Elements nicht verfügbar, wenn der Benutzer eine Datei öffnet, indem er im Menü **Datei** den Befehl **Vorhandene Datei öffnen** auswählt, wenn der Debugger für eine Datei arbeitet, oder wenn der Benutzer im Dialogfeld "In Dateien **suchen"** klickt. **Find and Replace** Um diese Situationen zu <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument> behandeln, ruft die IDE auf, um den Prozess zu verwalten, mit dem das beste Projekt zum Öffnen eines Dokuments gefunden wird.

## <a name="see-also"></a>Weitere Informationen
- [Projektpriorität](../../extensibility/internals/project-priority.md)
- [Hinzufügen von Projekt- und Projektelementvorlagen](../../extensibility/internals/adding-project-and-project-item-templates.md)

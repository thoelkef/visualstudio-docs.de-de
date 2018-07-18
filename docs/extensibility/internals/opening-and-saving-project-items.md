---
title: Öffnen und Speichern von Projektelementen | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], file persistence
- files [Visual Studio], opening and saving
- editors [Visual Studio SDK], file persistence
ms.assetid: f71898ad-335f-4c43-a177-4da87078afd1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 895306a70d386b7a895b52b22704ec42a07d17ce
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31130597"
---
# <a name="opening-and-saving-project-items"></a>Öffnen und Speichern von Projektelementen
Wenn Sie einen neuen Projekttyp hinzufügen, müssen Sie das Öffnen und Speichern von Dateien in Projekten verwalten die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrierten Entwicklungsumgebung (IDE). Die folgenden Themen behandeln die verschiedenen Ansätze zum Öffnen und Speichern von Dateien.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Anzeigen von Dateien mit dem Befehl „Datei öffnen“](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)  
 Bietet eine schrittweise Erklärung die IDE wie behandelt die **geöffnete Datei** Befehl und die Rolle von Projekten bei der Reaktion auf diesen Befehl.  
  
 [Anzeigen von Dateien mit dem Befehl „Öffnen mit“](../../extensibility/internals/displaying-files-by-using-the-open-with-command.md)  
 Bietet eine detaillierte, schrittweise Erklärung die IDE wie behandelt die **Öffnen mit** Befehl fordert das Öffnen einer Datei, die einige standard-Editoren hat.  
  
 [Gewusst wie: Öffnen von projektspezifischen Editoren](../../extensibility/how-to-open-project-specific-editors.md)  
 Enthält schrittweise Anleitungen zum angeben, dass die Dateien eines bestimmten Typs in Ihrem Projekt mit einem projektspezifischen-Editor geöffnet werden soll.  
  
 [Gewusst wie: Öffnen von Standard-Editoren](../../extensibility/how-to-open-standard-editors.md)  
 Enthält schrittweise Anleitungen, um anzugeben, wie die IDE einen standard-Editor für Dateien in den Projekttyp öffnen zu aktivieren.  
  
 [Gewusst wie: Öffnen von Editoren für geöffnete Dokumente](../../extensibility/how-to-open-editors-for-open-documents.md)  
 Enthält schrittweise Anleitungen, um eine projektspezifische-Editor für eine geöffnete Datei zu öffnen.  
  
 [Speichern eines Standarddokuments](../../extensibility/internals/saving-a-standard-document.md)  
 Enthält eine detaillierte Erläuterung die IDE wie behandelt die **speichern**, **speichern unter**, und **alle speichern** Befehle für ein Dokument in einem standard-Editor geöffnet.  
  
 [Speichern eines benutzerdefinierten Dokuments](../../extensibility/internals/saving-a-custom-document.md)  
 Enthält ein Diagramm und eine ausführliche Erläuterung die IDE wie behandelt die **speichern**, **speichern unter**, und **alle speichern** Befehle für Dokumente, die in einen benutzerdefinierten Editor geöffnet.  
  
 [Bestimmen, welcher Editor eine Datei in einem Projekt öffnet](../../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)  
 Erläutert die IDE folgt, um die geeigneten Editor oder Designer für eine Datei auszuwählen.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Erstellen von benutzerdefinierten Editoren und Designern](../../extensibility/creating-custom-editors-and-designers.md)  
 Listet die vier Typen von Editoren, dass die IDE hosten kann, und listet die Beschreibungen der einzelnen Editoren.  
  
 [Projekttypen](../../extensibility/internals/project-types.md)  
 Erläutert, wie Projekte zu steuern, wie Code kompiliert und erstellt wird, wie Editor geöffnet sind und wie Projektelemente formatiert werden.
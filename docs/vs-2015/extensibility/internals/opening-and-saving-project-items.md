---
title: Sie öffnen und Speichern von Projektelementen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], file persistence
- files [Visual Studio], opening and saving
- editors [Visual Studio SDK], file persistence
ms.assetid: f71898ad-335f-4c43-a177-4da87078afd1
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c1013253f39dec2b3d0a97f1bc4b8deb2dca913a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47515986"
---
# <a name="opening-and-saving-project-items"></a>Öffnen und Speichern von Projektelementen
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [öffnen und Speichern von Projektelementen](https://docs.microsoft.com/visualstudio/extensibility/internals/opening-and-saving-project-items).  
  
Wenn Sie einen neuen Projekttyp hinzufügen, müssen Sie das Öffnen und Speichern der Dateien in Projekten verwalten die [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] integrierte Entwicklungsumgebung (IDE). Die folgenden Themen behandeln die unterschiedlichen Ansätze zum Öffnen und Speichern von Dateien.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Anzeigen von Dateien mit dem Befehl „Datei öffnen“](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)  
 Bietet eine schrittweise Erklärung der Behandlung von der IDE die **geöffnete Datei** Befehl und die Rolle von Projekten bei der Reaktion auf diesen Befehl.  
  
 [Anzeigen von Dateien mit dem Befehl „Öffnen mit“](../../extensibility/internals/displaying-files-by-using-the-open-with-command.md)  
 Eine ausführliche, schrittweise Erklärung der Behandlung von der IDE bereit, die **Öffnen mit** Befehl aufgefordert wird das Öffnen einer Datei, die eine Auswahl aus der standard-Editoren.  
  
 [Gewusst wie: Öffnen von projektspezifischen Editoren](../../extensibility/how-to-open-project-specific-editors.md)  
 Enthält schrittweise Anleitungen zum angeben, dass die Dateien eines bestimmten Typs in Ihrem Projekt mit einem projektspezifischen-Editor geöffnet werden soll.  
  
 [Gewusst wie: Öffnen von Standard-Editoren](../../extensibility/how-to-open-standard-editors.md)  
 Enthält schrittweise Anleitungen zum angeben die IDE zu einen standard-Editor für Dateien in Ihrem Projekttyp öffnen zu aktivieren.  
  
 [Gewusst wie: Öffnen von Editoren für geöffnete Dokumente](../../extensibility/how-to-open-editors-for-open-documents.md)  
 Enthält schrittweise Anleitungen für eine geöffnete Datei einen projektspezifische-Editor wird geöffnet.  
  
 [Speichern eines Standarddokuments](../../extensibility/internals/saving-a-standard-document.md)  
 Enthält eine detaillierte Erläuterung der Behandlung von der IDE die **speichern**, **speichern**, und **Alles speichern** Befehle für ein Dokument in einem standard-Editor geöffnet.  
  
 [Speichern eines benutzerdefinierten Dokuments](../../extensibility/internals/saving-a-custom-document.md)  
 Enthält ein Diagramm und ausführliche erläuterungen, wie die IDE verarbeitet die **speichern**, **speichern**, und **Alles speichern** Befehle für Dokumente, die in einen benutzerdefinierten Editor geöffnet.  
  
 [Bestimmen, welcher Editor eine Datei in einem Projekt öffnet](../../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)  
 Beschreibt den Prozess, den die IDE folgt, um die geeigneten Editor oder Designer für eine Datei auszuwählen.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Erstellen von benutzerdefinierten Editoren und Designern](../../extensibility/creating-custom-editors-and-designers.md)  
 Listet die vier Typen von Editoren, dass die IDE hosten kann, und listet die Beschreibungen der einzelnen Editoren an.  
  
 [Projekttypen](../../extensibility/internals/project-types.md)  
 Beschreibt, wie Projekte, dass der Code kompiliert und erstellt wurde, zu steuern, wie Editoren geöffnet werden und wie Projektelemente formatiert werden.


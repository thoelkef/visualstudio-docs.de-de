---
title: "Hinzuf&#252;gen von Projekt- und Projektelementvorlagen | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Projekte [Visual Studio SDK], hinzufügen"
  - "Hinzufügen von Projektelementen [Visual Studio]"
ms.assetid: 8c59217f-56e5-4540-a73b-cd10de189373
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# Hinzuf&#252;gen von Projekt- und Projektelementvorlagen
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Wenn Sie erstellen, sind Sie Projekttypen, müssen Sie Unterstützung für das Hinzufügen neuer Projekte und Projektelemente unterstützen, indem Sie die Standard\-Dialogfelder [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] der integrierten Entwicklungsumgebung \(IDE\) verwenden.  In den folgenden Themen werden verschiedene Techniken zum Hinzufügen von Projekten und Projektelementen.  
  
## In diesem Abschnitt  
 [Projekt\-Kontext](../../extensibility/internals/project-context.md)  
 Erläutert, dass das Projekt die meisten der Kontextinformationen bereitstellt, die in der Umgebung durchsickert.  
  
 [Projektpriorität](../../extensibility/internals/project-priority.md)  
 Erläutert, dass ein Projektelement normalerweise ein Member eines Projekts zu sichern, Mehrdeutigkeit zu vermeiden, besteht darin, das Projekt zu öffnen, das Element zu verwenden.  
  
 [Projekt verschiedene Dateien](../../extensibility/internals/miscellaneous-files-project.md)  
 Enthält Informationen zu den beiden Typen von Editoren bereit, die zum Öffnen von Dateien in einem Projekt verwendet werden können, und das Projekt der Rolle spielt, wenn sie bestimmt, welcher Editor verwendet werden soll, wenn ein Projektelement geöffnet ist.  
  
 [Registrieren von Projekt\- und Elementvorlagen](../../extensibility/internals/registering-project-and-item-templates.md)  
 Erläutert, was eintritt, wenn ein [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Projekt erstellt wird.  
  
 [Hinzufügen von Elementen, die zum Hinzufügen neuer Elemente Dialogfelder](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)  
 Erläutert die Schritte zum Hinzufügen von Elementen zum **Neues Element hinzufügen** Dialogfeld.  
  
 [Verzeichnisse, die im Dialogfeld Neues Projekt hinzufügen](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)  
 Stellt ein Beispiel für das Registrierens eines neuen Verzeichnisses bereit, das die benutzerdefinierten Vorlagen bereitgestellt von VSPackages enthält.  
  
 [Hinzufügen von Verzeichnissen, die im Dialogfeld Neues Element hinzufügen](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)  
 Stellt ein Beispiel für das Registrierens eines neuen Datensatzes Verzeichnisse für das **Neues Element hinzufügen** Dialogfeld bereit.  
  
 [IDE\-definierte Befehle für die Erweiterung Projektsysteme](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)  
 Führt verschiedene Typen von den Befehl Elemente auf, die zum Erweitern von Projektsystemen verwendet werden.  
  
 [CATIDs für Objekte, die in der Regel verwendet werden, um Projekte zu erweitern.](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)  
 Führt CATID für Objekte auf, die verwendet werden, um [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)], [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]und[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] Projektsysteme zu erweitern.  
  
## Verwandte Abschnitte  
 [Gewusst wie: Öffnen von Editoren projektspezifische](../../extensibility/how-to-open-project-specific-editors.md)  
 Stellt schrittweise Anweisungen zum Öffnen eines Elements bereit, das tatsächlich zu einem bestimmten Editor für ein Projekt gebunden ist.  
  
 [Gewusst wie: Öffnen Sie die Standard\-Editoren](../../extensibility/how-to-open-standard-editors.md)  
 Enthält schrittweise Anweisungen zum Öffnen eines standardmäßigen editors bereit.  
  
 [Projekt\-Untertypen](../../extensibility/internals/project-subtypes.md)  
 Stellt Links zu Themen bereit untertyp grundlegenden Projekt.  Erweitern [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] untertypen ein bereits vorhandenes Projekt und [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] Projekte.  
  
 [Projekttypen](../../extensibility/internals/project-types.md)  
 Enthält Links zu zusätzlichen Themen bereit, in denen Informationen bieten zum Erstellen neuer Projekttypen entworfen wird.
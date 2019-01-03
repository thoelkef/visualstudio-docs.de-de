---
title: Assistenten | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], providing wizard support
ms.assetid: 59d9a77f-ee80-474b-a14f-90f477ab717b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ca842c185f4e9b50afffc20e14af70e93776116f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53932797"
---
# <a name="wizards"></a>Assistenten
Nachdem Sie einen Assistenten erstellen, in der Regel damit hinzufügen möchten die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Entwicklungsumgebung (IDE) integriert, sodass andere sie verwenden können. Die hinzugefügten dann erscheint der Assistent die **neues Projekt hinzufügen** oder **neues Element hinzufügen** Dialogfelder. Anzeigen der **neues Projekt hinzufügen** oder **neues Element hinzufügen** Dialogfeld Felder mit der rechten Maustaste in einer geöffneten Projektmappe **Projektmappen-Explorer**, zeigen Sie auf **hinzufügen**, und Klicken Sie dann auf **neues Projekt** oder **neues Element**.  
  
 Assistenten können implementiert werden, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Benutzer informieren, wählen Sie aus der Strukturansicht der verfügbaren Werte, die beim Öffnen der **neues Projekt hinzufügen** Dialogfeld oder **neues Element hinzufügen** im Dialogfeld oder wenn sie mit der rechten Maustaste ein Element im **Projektmappen-Explorer**.  
  
 Im Assistenten können Sie die Möglichkeit, Lokalisieren den Namen eines neuen Projekts oder einer Ites bereitstellen, und Sie können bestimmen, dass das Symbol, das Benutzern angezeigt wird, wenn sie den Assistenten auswählen. Sie können auch die Reihenfolge steuern, in der neuen Elemente relativ zu anderen verfügbaren Elemente angezeigt werden; Elemente keine alphabetisch angeordnet werden.  
  
 Sie können auch einen Assistenten angeben, der anders beginnt auf der Grundlage benutzerdefinierter Parameter, die dem Assistenten übergeben werden, wenn dieses geöffnet wird.  
  
 Die Themen in diesem Abschnitt erläutern die Dateien, die Sie implementieren, um die dazu führen, dass die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **neues Projekt hinzufügen** und **neues Element hinzufügen** Dialogfelder, um den Assistenten für die verfügbaren Assistenten und Vorlagen, Liste und die Anforderungen, die der Assistent erfüllen muss, um ordnungsgemäß ausgeführt wird, in der IDE.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Dateien zur Beschreibung des Vorlagenverzeichnisses (VSDIR)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)  
 Bietet eine Übersicht über welche Vorlage Directory Description-Dateien, und erläutert, wie sie funktionieren in der IDE zum Anzeigen von Ordnern, Assistenten VSZ-Dateien und Vorlagendateien, die einem Projekt in den Dialogfeldern zugeordnet sind.  
  
 [Assistentendatei (VSZ)](../../extensibility/internals/wizard-dot-vsz-file.md)  
 Erläutert, wie der IDE Assistenten gestartet und führt die drei Teile der VSZ-Datei.  
  
 [Assistentenschnittstelle (IDTWizard)](../../extensibility/internals/wizard-interface-idtwizard.md)  
 Beschreibt die `IDTWizard` Schnittstelle, Assistenten implementieren müssen, um in der IDE zu arbeiten.  
  
 [Kontextparameter](../../extensibility/internals/context-parameters.md)  
 Erläutert, wie die Assistenten implementiert werden und was geschieht, wenn die IDE Kontextparameter für die Implementierung übergeben.  
  
 [Benutzerdefinierte Parameter](../../extensibility/internals/custom-parameters.md)  
 Es wird erläutert, wie benutzerdefinierte-Parameter verwenden, um den Vorgang des Assistenten zu steuern, nachdem der Assistent gestartet wird.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Projekttypen](../../extensibility/internals/project-types.md)  
 Enthält Links zu weiteren Themen, die Informationen zum Entwerfen von neuen Projekttypen anbieten.  
  
 [Erweitern von Projekten](../../extensibility/extending-projects.md)  
 Beschreibt, wie Codedateien und Ressourcendateien mithilfe von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]-Projekten und -Projektmappen organisiert werden und wie die Quellcodeverwaltung implementiert wird.
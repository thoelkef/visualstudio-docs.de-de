---
title: Assistenten | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], providing wizard support
ms.assetid: 59d9a77f-ee80-474b-a14f-90f477ab717b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 03cee9de14da76ea65882d906acb3af88e72e999
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31138713"
---
# <a name="wizards"></a>Assistenten
Nachdem Sie einen Assistenten erstellen, in der Regel möchten Sie hinzuzufügen der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrierte Entwicklungsumgebung (IDE), damit er von anderen Benutzern verwendet werden können. Die hinzugefügten dann erscheint der Assistent die **neues Projekt hinzufügen** oder **neues Element hinzufügen** Dialogfelder. Anzeigen der **neues Projekt hinzufügen** oder **neues Element hinzufügen** Dialogfeld Dialogfelder, mit der rechten Maustaste in einer geöffneten Projektmappe **Projektmappen-Explorer**, zeigen Sie auf **hinzufügen**, und Klicken Sie dann auf **neues Projekt** oder **neues Element**.  
  
 Assistenten in implementiert werden können [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] können Benutzer wählen Sie aus der Strukturansicht verfügbarer Werte beim Öffnen der **neues Projekt hinzufügen** (Dialogfeld) oder die **neues Element hinzufügen** (Dialogfeld), oder wenn sie mit der rechten Maustaste ein Element im **Projektmappen-Explorer**.  
  
 In dem Assistenten können Sie die Option zum Lokalisieren von den Namen eines neuen Projekts oder einer Ites bereitzustellen, und können Sie bestimmen, das Symbol, das Benutzern angezeigt werden, wenn sie den Assistenten auswählen. Sie können auch die Reihenfolge steuern, in der neue Elemente relativ zu anderen verfügbaren Elemente angezeigt werden; Elemente müssen nicht alphabetisch sortiert werden.  
  
 Sie können auch einen Assistenten angeben, der unterschiedlich ist, beginnt auf der Grundlage benutzerdefinierter Parameter, die an dem Assistenten übergeben werden, wenn dieses geöffnet wird.  
  
 Die Themen in diesem Abschnitt erläutern die Dateien, die Sie implementieren, um dazu führen, dass die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **neues Projekt hinzufügen** und **neues Element hinzufügen** Dialogfelder des Assistenten für die verfügbaren Assistenten und Vorlagen, auflisten und die Anforderungen, die der Assistent erfüllen muss, damit Sie ordnungsgemäß in der IDE ausgeführt werden.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Dateien zur Beschreibung des Vorlagenverzeichnisses (VSDIR)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)  
 Bietet einen Überblick über die Vorlage Directory Description-Dateien und erläutert, wie sie funktionieren in der IDE zum Anzeigen von Ordnern, VSZ-Assistentendateien und Vorlagendateien, die ein Projekt in den Dialogfeldern zugeordnet sind.  
  
 [Assistentendatei (VSZ)](../../extensibility/internals/wizard-dot-vsz-file.md)  
 Erläutert, wie die IDE Assistenten gestartet wird, und führt die drei Teile der VSZ-Datei.  
  
 [Assistentenschnittstelle (IDTWizard)](../../extensibility/internals/wizard-interface-idtwizard.md)  
 Beschreibt die `IDTWizard` Schnittstelle, die Assistenten implementieren müssen, um in der IDE unter Umständen.  
  
 [Kontextparameter](../../extensibility/internals/context-parameters.md)  
 Erläutert, wie Assistenten implementiert werden und was geschieht, wenn die IDE für die Implementierung von Kontextparametern übergibt.  
  
 [Benutzerdefinierte Parameter](../../extensibility/internals/custom-parameters.md)  
 Erläutert die benutzerdefinierten Parameter verwenden, um die Verwendungsweise des Assistenten gesteuert wird, nachdem der Assistent gestartet wird.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Projekttypen](../../extensibility/internals/project-types.md)  
 Enthält Links zu weiteren Themen, die Informationen zum Entwerfen neuer Projekttypen bieten.  
  
 [Erweitern von Projekten](../../extensibility/extending-projects.md)  
 Beschreibt, wie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Projekte und Projektmappen, Codedateien und Ressourcendateien und wie die quellcodeverwaltung implementiert zu organisieren.
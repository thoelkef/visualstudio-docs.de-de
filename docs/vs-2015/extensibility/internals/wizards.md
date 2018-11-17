---
title: Assistenten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], providing wizard support
ms.assetid: 59d9a77f-ee80-474b-a14f-90f477ab717b
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cbf2eceeb3ae8a3870954d53f8d85c46f3322d24
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51747570"
---
# <a name="wizards"></a>Assistenten
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Nachdem Sie einen Assistenten erstellen, in der Regel damit hinzufügen möchten die [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Entwicklungsumgebung (IDE) integriert, sodass andere sie verwenden können. Die hinzugefügten dann erscheint der Assistent die **neues Projekt hinzufügen** oder **neues Element hinzufügen** Dialogfelder. Anzeigen der **neues Projekt hinzufügen** oder **neues Element hinzufügen** Dialogfeld Felder mit der rechten Maustaste in einer geöffneten Projektmappe **Projektmappen-Explorer**, zeigen Sie auf **hinzufügen**, und Klicken Sie dann auf **neues Projekt** oder **neues Element**.  
  
 Assistenten können implementiert werden, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Benutzer informieren, wählen Sie aus der Strukturansicht der verfügbaren Werte, die beim Öffnen der **neues Projekt hinzufügen** Dialogfeld oder **neues Element hinzufügen** im Dialogfeld oder wenn sie mit der rechten Maustaste ein Element im **Projektmappen-Explorer**.  
  
 Im Assistenten können Sie die Möglichkeit, Lokalisieren den Namen eines neuen Projekts oder einer Ites bereitstellen, und Sie können bestimmen, dass das Symbol, das Benutzern angezeigt wird, wenn sie den Assistenten auswählen. Sie können auch die Reihenfolge steuern, in der neuen Elemente relativ zu anderen verfügbaren Elemente angezeigt werden; Elemente keine alphabetisch angeordnet werden.  
  
 Sie können auch einen Assistenten angeben, der anders beginnt auf der Grundlage benutzerdefinierter Parameter, die dem Assistenten übergeben werden, wenn dieses geöffnet wird.  
  
 Die Themen in diesem Abschnitt erläutern die Dateien, die Sie implementieren, um die dazu führen, dass die [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] **neues Projekt hinzufügen** und **neues Element hinzufügen** Dialogfelder, um den Assistenten für die verfügbaren Assistenten und Vorlagen, Liste und die Anforderungen, die der Assistent erfüllen muss, um ordnungsgemäß ausgeführt wird, in der IDE.  
  
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
  
 [Exemplarische Vorgehensweise: Erstellen eines Assistenten](http://msdn.microsoft.com/library/adb41fe9-fcca-4e87-bf4f-bf2fa68e8b06)  
 Veranschaulicht, wie zum Erstellen eines Assistenten.  
  
 [Erweitern von Projekten](../../extensibility/extending-projects.md)  
 Beschreibt, wie Codedateien und Ressourcendateien mithilfe von [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]-Projekten und -Projektmappen organisiert werden und wie die Quellcodeverwaltung implementiert wird.


---
title: Assistenten | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], providing wizard support
ms.assetid: 59d9a77f-ee80-474b-a14f-90f477ab717b
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6e58ebd736f7bb9f35df6e41d5235f36f7037259
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65687627"
---
# <a name="wizards"></a>Assistenten
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Nachdem Sie einen Assistenten erstellt haben, möchten Sie ihn in der Regel der [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] integrierten Entwicklungsumgebung (Integrated Development Environment, IDE) hinzufügen, damit er von anderen Benutzern verwendet werden kann. Der hinzugefügte Assistent wird dann in den Dialogfeldern **Neues Projekt hinzufügen** oder **Neues Element hinzufügen** angezeigt. Klicken Sie in **Projektmappen-Explorer**mit der rechten Maustaste auf eine geöffnete Projekt Mappe, zeigen Sie auf **Hinzufügen**, und klicken Sie dann auf **Neues Projekt** oder **Neues Element**, um die Dialogfelder **Neues Projekt hinzufügen** oder **Neues Element hinzufügen** anzuzeigen.  
  
 Assistenten können in implementiert werden [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , um Benutzern die Auswahl aus einer Strukturansicht verfügbarer Werte zu ermöglichen, wenn Sie das Dialogfeld **Neues Projekt hinzufügen** oder das Dialogfeld **Neues Element hinzufügen** öffnen, oder wenn Sie mit der rechten Maustaste auf ein Element in **Projektmappen-Explorer**klicken.  
  
 In Ihrem Assistenten können Sie die Option zum Lokalisieren des Namens eines neuen Projekts oder von "Ites" bereitstellen, und Sie können das Symbol ermitteln, das Benutzern angezeigt wird, wenn Sie den Assistenten auswählen. Sie können auch die Reihenfolge steuern, in der neue Elemente relativ zu anderen verfügbaren Elementen angezeigt werden. Elemente müssen nicht alphabetisch angeordnet werden.  
  
 Sie können auch einen Assistenten bereitstellen, der je nach benutzerdefinierten Parametern, die beim Öffnen an den Assistenten übergeben werden, unterschiedlich gestartet werden.  
  
 In den Themen in diesem Abschnitt werden die Dateien erläutert, die Sie implementieren, um die [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Dialogfelder **Neues Projekt hinzufügen** und **Neues Element hinzufügen** zu veranlassen, den Assistenten unter den verfügbaren Assistenten und Vorlagen aufzulisten und die Anforderungen zu erfüllen, die der Assistent erfüllen muss, damit er in der IDE ordnungsgemäß funktioniert.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Dateien zur Beschreibung des Vorlagenverzeichnisses (VSDIR)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)  
 Bietet einen Überblick über die Vorlagen Verzeichnis Beschreibungsdateien und erläutert, wie Sie in der IDE funktionieren, um Ordner, Assistenten. VSZ-Dateien und Vorlagen Dateien anzuzeigen, die einem Projekt in den Dialogfeldern zugeordnet sind.  
  
 [Assistentendatei (VSZ)](../../extensibility/internals/wizard-dot-vsz-file.md)  
 Erläutert, wie die IDE die Assistenten startet und die drei Teile der VSZ-Datei auflistet.  
  
 [Assistentenschnittstelle (IDTWizard)](../../extensibility/internals/wizard-interface-idtwizard.md)  
 Beschreibt die `IDTWizard` Schnittstelle, die Assistenten implementieren müssen, damit Sie in der IDE funktioniert.  
  
 [Kontextparameter](../../extensibility/internals/context-parameters.md)  
 Erläutert, wie Assistenten implementiert werden und was geschieht, wenn die IDE Kontext Parameter an die-Implementierung übergibt.  
  
 [Benutzerdefinierte Parameter](../../extensibility/internals/custom-parameters.md)  
 Erläutert die Verwendung von benutzerdefinierten Parametern zum Steuern des Vorgangs des Assistenten, nachdem der Assistent gestartet wurde.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Projekttypen](../../extensibility/internals/project-types.md)  
 Enthält Links zu weiteren Themen, in denen Informationen zum Entwerfen neuer Projekttypen angeboten werden.  
  
 [Exemplarische Vorgehensweise: Erstellen eines Assistenten](https://msdn.microsoft.com/library/adb41fe9-fcca-4e87-bf4f-bf2fa68e8b06)  
 Veranschaulicht, wie ein Assistent erstellt wird.  
  
 [Erweitern von Projekten](../../extensibility/extending-projects.md)  
 Beschreibt, wie Codedateien und Ressourcendateien mithilfe von [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]-Projekten und -Projektmappen organisiert werden und wie die Quellcodeverwaltung implementiert wird.

---
title: Zauberer | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], providing wizard support
ms.assetid: 59d9a77f-ee80-474b-a14f-90f477ab717b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d65cf2dcc10380b0ac750c8e1b0e7fd56eab95b5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703214"
---
# <a name="wizards"></a>Assistenten
Nachdem Sie einen Assistenten erstellt haben, möchten [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Sie ihn in der Regel der integrierten Entwicklungsumgebung (IDE) hinzufügen, damit andere ihn verwenden können. Der hinzugefügte Assistent wird dann in den Dialogfeldern **Neues Projekt hinzufügen** oder Neues Element **hinzufügen** angezeigt. Um die Dialogfelder **Neues Projekt hinzufügen** oder Neues Element **hinzufügen** anzuzeigen, klicken Sie im **Projektmappen-Explorer**mit der rechten Maustaste auf eine Lösung , zeigen Sie auf **Hinzufügen**, und klicken Sie dann auf **Neues Projekt** oder Neues **Element**.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Assistenten können implementiert werden, damit Benutzer aus einer Strukturansicht der verfügbaren Werte auswählen können, wenn sie das Dialogfeld Neues Projekt **hinzufügen** oder das Dialogfeld Neues Element **hinzufügen** öffnen oder wenn sie mit der rechten Maustaste auf ein Element im **Projektmappen-Explorer**klicken.

 In Ihrem Assistenten können Sie die Möglichkeit bereitstellen, den Namen eines neuen Projekts oder ites zu lokalisieren, und Sie können das Symbol bestimmen, das Benutzern angezeigt wird, wenn sie den Assistenten auswählen. Sie können auch die Reihenfolge steuern, in der neue Elemente relativ zu anderen verfügbaren Elementen angezeigt werden. Elemente müssen nicht alphabetisch organisiert werden.

 Sie können auch einen Assistenten bereitstellen, der basierend auf benutzerdefinierten Parametern, die beim Öffnen an den Assistenten übergeben werden, anders gestartet wird.

 In den Themen in diesem Abschnitt werden [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] die Dateien erläutert, die Sie implementieren, um die Dialogfelder **Neues Projekt hinzufügen** und Neues **Element hinzufügen** dazu zu bringen, dass der Assistent den Assistenten unter den verfügbaren Assistenten und Vorlagen auflistet, sowie die Anforderungen, die der Assistent erfüllen muss, damit er in der IDE ordnungsgemäß funktioniert.

## <a name="in-this-section"></a>In diesem Abschnitt
- [Dateien zur Beschreibung des Vorlagenverzeichnisses (VSDIR)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)

 Bietet einen Überblick darüber, welche Vorlagenverzeichnisbeschreibungsdateien und erläutert, wie sie in der IDE funktionieren, um Ordner, .vsz-Dateien und Vorlagendateien anzuzeigen, die einem Projekt in den Dialogfeldern zugeordnet sind.

- [Assistentendatei (VSZ)](../../extensibility/internals/wizard-dot-vsz-file.md)

 Erläutert, wie die IDE Assistenten startet und die drei Teile der .vsz-Datei auflistet.

- [Assistentenschnittstelle (IDTWizard)](../../extensibility/internals/wizard-interface-idtwizard.md)

 Beschreibt `IDTWizard` die Schnittstelle, die Assistenten implementieren müssen, um in der IDE zu arbeiten.

- [Kontextparameter](../../extensibility/internals/context-parameters.md)

 Erläutert, wie Assistenten implementiert werden und was geschieht, wenn die IDE Kontextparameter an die Implementierung übergibt.

- [Benutzerdefinierte Parameter](../../extensibility/internals/custom-parameters.md)

 Erläutert, wie benutzerdefinierte Parameter verwendet werden, um den Betrieb des Assistenten nach dem Starten des Assistenten zu steuern.

## <a name="related-sections"></a>Verwandte Abschnitte
- [Projekttypen](../../extensibility/internals/project-types.md)

 Enthält Links zu weiteren Themen, die Informationen zum Entwerfen neuer Projekttypen enthalten.

- [Erweitern von Projekten](../../extensibility/extending-projects.md)

 Beschreibt, wie Codedateien und Ressourcendateien mithilfe von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]-Projekten und -Projektmappen organisiert werden und wie die Quellcodeverwaltung implementiert wird.

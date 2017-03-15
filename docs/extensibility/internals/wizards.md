---
title: Assistenten | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], providing wizard support
ms.assetid: 59d9a77f-ee80-474b-a14f-90f477ab717b
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: af0466ea3c11b75090e45cb9b408ed0723cd8a6f
ms.lasthandoff: 02/22/2017

---
# <a name="wizards"></a>Assistenten
Nachdem Sie einen Assistenten erstellen, in der Regel sollen Hinzufügen der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrierte Entwicklungsumgebung (IDE), damit andere es verwenden können. Die hinzugefügten dann erscheint der Assistent die **neues Projekt hinzufügen** oder **neues Element hinzufügen** Dialogfelder. Anzeigen der **neues Projekt hinzufügen** oder **neues Element hinzufügen** Dialogfeld Dialogfelder, mit der rechten Maustaste in einer geöffneten Projektmappe **Projektmappen-Explorer**, zeigen Sie auf **hinzufügen**, und klicken Sie dann auf **neues Projekt** oder **neues Element**.  
  
 Assistenten in implementiert werden können [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Benutzer können auf eine Strukturansicht der verfügbaren Werte beim Öffnen der **neues Projekt hinzufügen** im Dialogfeld oder **neues Element hinzufügen** im Dialogfeld oder wenn sie ein Element in **Projektmappen-Explorer**.  
  
 Im Assistenten Sie bieten die Möglichkeit, den Namen eines neuen Projekts oder einer Ites lokalisieren, und Sie können festlegen, dass das Symbol, das Benutzern angezeigt wird, wenn sie den Assistenten auswählen. Sie können auch die Reihenfolge steuern, in der neuen Elemente relativ zu anderen verfügbaren Elemente angezeigt werden. Elemente müssen nicht alphabetisch angeordnet werden.  
  
 Sie können auch einen Assistenten angeben, der anders beginnt auf der Grundlage benutzerdefinierter Parameter, die an dem Assistenten übergeben werden, wenn sie geöffnet ist.  
  
 Die Themen in diesem Abschnitt erläutern die Dateien, die Sie implementieren, um dazu führen, dass die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **neues Projekt hinzufügen** und **neues Element hinzufügen** Dialogfelder, um die Liste der Assistent zwischen den verfügbaren Assistenten und Vorlagen und die Anforderungen, die der Assistent erfüllen muss, um ordnungsgemäß in der IDE ausgeführt werden.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Beschreibung der Vorlage Verzeichnis (. VSDIR)-Dateien](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)  
 Bietet eine Übersicht über die Vorlage Directory Beschreibungsdateien und erläutert, wie sie funktionieren in der IDE zum Anzeigen von Ordnern, Assistenten VSZ-Dateien und Vorlagendateien, die in den Dialogfeldern Projekt zugeordnet sind.  
  
 [Assistenten (. VSZ)-Datei](../../extensibility/internals/wizard-dot-vsz-file.md)  
 Erläutert, wie dem Assistenten starten der IDE und führt die drei Teile der VSZ-Datei.  
  
 [Assistenten-Benutzeroberfläche (IDTWizard)](../../extensibility/internals/wizard-interface-idtwizard.md)  
 Beschreibt die `IDTWizard` Schnittstelle, Assistenten implementieren müssen, um in der IDE zu arbeiten.  
  
 [Kontextparameter](../../extensibility/internals/context-parameters.md)  
 Erläutert, wie Assistenten implementiert werden und was geschieht, wenn die IDE für die Implementierung von Kontextparametern übergibt.  
  
 [Benutzerdefinierte Parameter](../../extensibility/internals/custom-parameters.md)  
 Erläutert die benutzerdefinierten Parameter verwenden, um den Vorgang des Assistenten gesteuert wird, nachdem der Assistent gestartet wird.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Projekttypen](../../extensibility/internals/project-types.md)  
 Enthält Links zu weiteren Themen, die Informationen zum Entwerfen von neuen Typen zu bieten.  
  
 [Exemplarische Vorgehensweise: Erstellen eines Assistenten](http://msdn.microsoft.com/Library/adb41fe9-fcca-4e87-bf4f-bf2fa68e8b06)  
 Veranschaulicht das Erstellen eines Assistenten.  
  
 [Erweitern von Projekten](../../extensibility/extending-projects.md)  
 Beschreibt, wie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Projekte und Projektmappen zum Organisieren von Codedateien und Ressourcendateien und wie Sie Datenquellen-Steuerelement zu implementieren.

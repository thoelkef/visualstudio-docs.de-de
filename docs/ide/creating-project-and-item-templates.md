---
title: Erstellen von Projekt- und Elementvorlagen | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- templates [Visual Studio], projects
- item templates, about item templates
- templates [Visual Studio], item
- Visual Studio templates, item
- Visual Studio templates, about templates
- project templates [Visual Studio], about project templates
- Visual Studio templates, project
- templates [Visual Studio], about templates
ms.assetid: a6ce501a-699b-4e3e-ade8-c81895645c20
caps.latest.revision: "9"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 43b45f70e8ac7a6eeadfd3fb216b53540ec9a8b8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="creating-project-and-item-templates"></a>Erstellen von Projekt- und Elementvorlagen
Projekt- und Elementvorlagen in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] bieten wiederverwendbare Stubs, die Benutzen grundlegenden Code sowie eine grundlegende Struktur vermitteln, die sie beide zu ihren eigenen Zwecken verwenden können.  
  
## <a name="visual-studio-templates"></a>Visual Studio-Vorlagen  
 Zusammen mit [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] wird eine Reihe vordefinierter Projekt- und Elementvorlagen installiert. Die Windows Forms-Anwendungsvorlagen und Klassenbibliotheksvorlagen in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] und [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)], die über das Dialogfeld **Neues Projekt** verfügbar sind, sind Beispiele für Projektvorlagen. Installierte Elementvorlagen sind im Dialogfeld **Neues Element hinzufügen** verfügbar. Sie umfassen Elemente wie Codedateien, XML-Dateien, HTML-Seiten und Stylesheets.  
  
 Diese Vorlagen stellen einen Ausgangspunkt bereit, von dem aus Benutzer Projekte erstellen oder aktuelle Projekte erweitern können. Projektvorlagen stellen die Dateien bereit, die für einen bestimmten Projekttyp erforderlich sind; sie umfassen standardmäßige Assemblyverweise und legen standardmäßige Projekteigenschaften und Compileroptionen fest. Elementvorlagen können eine unterschiedliche Komplexität aufweisen – angefangen von einer einfachen leeren Datei mit der gewünschten Dateierweiterung bis hin zu einer Elementvorlage mit mehreren Dateien, die beispielsweise Quellcodedateien mit Stubcode, Dateien mit Designerinformationen und eingebettete Ressourcen enthält.  
  
 Zusätzlich zu den installierten Vorlagen in den Dialogfeldern **Neues Projekt** und **Neues Element hinzufügen** können Sie eigene Vorlagen erstellen oder von der Community bereitgestellte Vorlagen herunterladen und verwenden. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen von Projektvorlagen](../ide/how-to-create-project-templates.md) und [Vorgehensweise: Erstellen von Elementvorlagen](../ide/how-to-create-item-templates.md).  
  
## <a name="contents-of-a-template"></a>Inhalt von Vorlagen  
 Alle Projekt- und Elementvorlagen, unabhängig davon, ob diese zusammen mit [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] installiert oder von Ihnen erstellt wurden, funktionieren nach demselben Prinzip und umfassen ähnliche Inhalte. Alle Vorlagen enthalten die folgenden Elemente:  
  
-   Die Dateien, die bei Verwendung der Vorlage erstellt werden sollen. Dazu gehören Quellcodedateien, eingebettete Ressourcen, Projektdateien usw.  
  
-   Eine VSTEMPLATE-Datei. Diese Datei enthält die Metadaten, die von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] benötigt werden, um die Vorlage in den Dialogfeldern **Neues Projekt** und **Neues Element hinzufügen** anzuzeigen und um ein Projekt oder Element von der Vorlage zu erstellen. Weitere Informationen zu VSTEMPLATE-Dateien finden Sie unter [Vorlagenparameter](../ide/template-parameters.md).  
  
 Wenn diese Dateien in einer ZIP-Datei komprimiert sind und sich im richtigen Ordner befinden, werden sie automatisch von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] angezeigt. Projektvorlagen werden im Dialogfeld **Neues Projekt** im Abschnitt **Meine Vorlagen** angezeigt, und Elementvorlagen werden in den Dialogfeldern **Neues Element hinzufügen** angezeigt. Weitere Informationen zu Vorlagenordnern finden Sie unter [Vorgehensweise: Suchen und Organisieren von Vorlagen](../ide/how-to-locate-and-organize-project-and-item-templates.md).  
  
## <a name="starter-kits"></a>Starter Kits  
 Starter Kits sind erweiterte Vorlagen, die mit anderen Mitgliedern der Community gemeinsam genutzt werden können. Ein Starter Kit umfasst kompilierbare Codebeispiele, Dokumentationen und andere Ressourcen, die Benutzern parallel zur Erstellung hilfreicher und realer Anwendungen den Einstieg in neue Tools und Programmiertechniken erleichtern. Der grundlegende Inhalt und die Verfahren für Starter Kits sind identisch mit denen für Vorlagen. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen von Starter Kits](../ide/how-to-create-starter-kits.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Erstellen von Projektvorlagen](../ide/how-to-create-project-templates.md)   
 [Vorgehensweise: Erstellen von Elementvorlagen](../ide/how-to-create-item-templates.md)   
 [Vorlagenparameter](../ide/template-parameters.md)   
 [Anpassen von Vorlagen](../ide/customizing-project-and-item-templates.md)   
 [Gewusst wie: Erstellen von Starter Kits](../ide/how-to-create-starter-kits.md)
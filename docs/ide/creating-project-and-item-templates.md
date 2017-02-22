---
title: "Erstellen von benutzerdefinierten Projekt- und Elementvorlagen in Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Elementvorlagen, Informationen über Elementvorlagen"
  - "Projektvorlagen [Visual Studio], Informationen zu Projektvorlagen"
  - "Vorlagen [Visual Studio], Informationen über Vorlagen"
  - "Vorlagen [Visual Studio], Element"
  - "Vorlagen [Visual Studio], Projekte"
  - "Visual Studio-Vorlagen, Informationen über Vorlagen"
  - "Visual Studio-Vorlagen, Element"
  - "Visual Studio-Vorlagen, Projekt"
ms.assetid: a6ce501a-699b-4e3e-ade8-c81895645c20
caps.latest.revision: 9
caps.handback.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Erstellen von benutzerdefinierten Projekt- und Elementvorlagen in Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Projekt\- und Elementvorlagen in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] bieten wiederverwendbare Stubs, die Benutzen grundlegenden Code sowie eine grundlegende Struktur vermitteln, die sie beide zu ihren eigenen Zwecken verwenden können.  
  
## Visual Studio\-Vorlagen  
 Zusammen mit [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] wird eine Reihe vordefinierter Projekt\- und Elementvorlagen installiert.  Beispiele für Projektvorlagen sind die Windows Forms\-Anwendungs\- und Klassenbibliotheksvorlagen in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] und [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)], die über das Dialogfeld **Neues Projekt** verfügbar sind.  Installierte Elementvorlagen sind im Dialogfeld **Neues Element hinzufügen** verfügbar. Sie umfassen Elemente wie Codedateien, XML\-Dateien, HTML\-Seiten und Stylesheets.  
  
 Diese Vorlagen stellen einen Ausgangspunkt bereit, von dem aus Benutzer Projekte erstellen oder aktuelle Projekte erweitern können.  Projektvorlagen stellen die Dateien bereit, die für einen bestimmten Projekttyp erforderlich sind; sie umfassen standardmäßige Assemblyverweise und legen standardmäßige Projekteigenschaften und Compileroptionen fest.  Elementvorlagen können eine unterschiedliche Komplexität aufweisen – angefangen von einer einfachen leeren Datei mit der gewünschten Dateinamenerweiterung bis hin zu einer Elementvorlage mit mehreren Dateien, die beispielsweise Quellcodedateien mit Stubcode, Dateien mit Designerinformationen und eingebettete Ressourcen enthält.  
  
 Zusätzlich zu den installierten Vorlagen in den Dialogfeldern **Neues Projekt** und **Neues Element hinzufügen** können Sie eigene Vorlagen erstellen oder von der Community bereitgestellte Vorlagen herunterladen und verwenden.  Weitere Informationen finden Sie unter [Gewusst wie: Erstellen von Projektvorlagen](../ide/how-to-create-project-templates.md) und [Gewusst wie: Erstellen von Elementvorlagen](../ide/how-to-create-item-templates.md).  
  
## Inhalt von Vorlagen  
 Alle Projekt\- und Elementvorlagen, unabhängig davon, ob diese zusammen mit [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] installiert oder von Ihnen erstellt wurden, funktionieren nach demselben Prinzip und umfassen ähnliche Inhalte.  Alle Vorlagen enthalten die folgenden Elemente:  
  
-   Die Dateien, die bei Verwendung der Vorlage erstellt werden sollen.  Dazu gehören Quellcodedateien, eingebettete Ressourcen, Projektdateien usw.  
  
-   Eine VSTEMPLATE\-Datei.  Diese Datei enthält die Metadaten, die von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] benötigt werden, um die Vorlage in den Dialogfeldern **Neues Projekt** und **Neues Element hinzufügen** anzuzeigen sowie ein Projekt oder Element von der Vorlage zu erstellen.  Weitere Informationen zu VSTEMPLATE\-Dateien finden Sie unter [Vorlagenparameter](../ide/template-parameters.md).  
  
 Wenn diese Dateien in einer ZIP\-Datei komprimiert sind und sich im richtigen Ordner befinden, werden sie automatisch von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] angezeigt.  Projektvorlagen werden im Dialogfeld **Neues Projekt** im Abschnitt **Meine Vorlagen** angezeigt, und Elementvorlagen in den Dialogfeldern **Neues Element hinzufügen** angezeigt.  Weitere Informationen zu Vorlagenordnern finden Sie unter [Gewusst wie: Suchen und Organisieren von Vorlagen](../ide/how-to-locate-and-organize-project-and-item-templates.md).  
  
## Starter Kits  
 Starter Kits sind erweiterte Vorlagen, die mit anderen Mitgliedern der Community gemeinsam genutzt werden können.  Ein Starter Kit umfasst kompilierbare Codebeispiele, Dokumentationen und andere Ressourcen, die Benutzern parallel zur Erstellung hilfreicher und realer Anwendungen den Einstieg in neue Tools und Programmiertechniken erleichtern.  Der grundlegende Inhalt und die Verfahren für Starter Kits sind identisch mit denen für Vorlagen.  Weitere Informationen finden Sie unter [Gewusst wie: Erstellen von Starter Kits](../ide/how-to-create-starter-kits.md).  
  
## Siehe auch  
 [Gewusst wie: Erstellen von Projektvorlagen](../ide/how-to-create-project-templates.md)   
 [Gewusst wie: Erstellen von Elementvorlagen](../ide/how-to-create-item-templates.md)   
 [Vorlagenparameter](../ide/template-parameters.md)   
 [Anpassen von Vorlagen](../ide/customizing-project-and-item-templates.md)   
 [Gewusst wie: Erstellen von Starter Kits](../ide/how-to-create-starter-kits.md)
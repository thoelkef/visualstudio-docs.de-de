---
title: "Customizing T4 Text Transformation | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "text templates, API"
  - "text templates, custom hosts"
ms.assetid: 62cd9a3c-a6e1-4b29-93f5-f2a0cf47dc92
caps.latest.revision: 28
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 28
---
# Customizing T4 Text Transformation
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Textvorlagen sind eine Funktion von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], die es Ihnen ermöglicht, Programmcode oder andere Textdateien mithilfe eines Transformationsprozesses zu generieren.  Mit dem [!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)] können Sie den standardmäßigen Vorlagentransformationsprozess erweitern, indem Sie den Textvorlagen\-Direktivenprozessor oder den Textvorlagenhost anpassen.  
  
## In diesem Abschnitt  
 [The Text Template Transformation Process](../modeling/the-text-template-transformation-process.md)  
 Beschreibt die Funktionsweise der Texttransformation und erläutert die Rolle des Vorlagenhosts und der Direktivenprozessoren.  
  
 [Creating Custom T4 Text Template Directive Processors](../modeling/creating-custom-t4-text-template-directive-processors.md)  
 Der Direktivenprozessor verarbeitet Direktiven in der Vorlage, z. B. `<#@template#>.` Er wird während der Kompilierung der Vorlage ausgeführt, und kann Assemblys und andere Ressourcen laden.  Er kann auch Code einfügen, durch den Ressourcen zur Laufzeit geladen werden.  Sie können die Komplexität der Vorlagen reduzieren, indem Sie einen eigenen Direktivenprozessor definieren.  
  
 [Invoking Text Transformation in a VS Extension](../modeling/invoking-text-transformation-in-a-vs-extension.md)  
 Wenn Sie eine [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Erweiterung schreiben, z. B. einen Menübefehl oder einen Ereignishandler, kann für die Erweiterung der Textvorlagendienst zum Transformieren beliebiger Textvorlagen verwendet werden.  Sie können Parameterdaten mit dem Sitzungsobjekt an die Vorlage übergeben und die Werte von der Vorlage mithilfe der `<#@parameter#>`\-Direktive abrufen.  
  
 [Processing Text Templates by using a Custom Host](../modeling/processing-text-templates-by-using-a-custom-host.md)  
 Wenn der Code der Textvorlage ausgeführt wird, stellt der Host den Zugriff auf externe Dateien und den Zustand der Anwendung bereit.  Der Host, der Texttransformationen in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ausführt, kann z. B. Zugriff auf den Projektmappen\-Explorer bieten.  Er zeigt auch Fehler im Fehlermeldungsfenster an.  Wenn Sie Texttransformationen in einem anderen Kontext ausführen möchten, können Sie einen eigenen Host definieren, der Zugriff auf die in diesem Kontext verfügbaren Dienste bietet.  
  
 Wenn Sie eine [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Erweiterung schreiben, verwenden Sie ggf. den vorhandenen Texttransformationsdienst, anstatt einen eigenen Host zu schreiben.  Weitere Informationen finden Sie unter [Invoking Text Transformation in a VS Extension](../modeling/invoking-text-transformation-in-a-vs-extension.md).  
  
## Referenz  
 [Writing a T4 Text Template](../modeling/writing-a-t4-text-template.md)  
  
 Enthält die Syntax von Textvorlagendirektiven und Kontrollblöcken.
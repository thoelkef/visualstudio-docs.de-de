---
title: Anpassen der T4-TextTransformation | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- text templates, API
- text templates, custom hosts
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 56eb5c11984e60e16374853ef1911ae831476d64
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/13/2018
---
# <a name="customizing-t4-text-transformation"></a>Anpassen der T4-Texttransformation
Textvorlagen sind eine Funktion des [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , mit denen Sie Programmcode oder andere Textdateien mithilfe eines Transformationsprozesses zu generieren. Mithilfe von [!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)], Sie können den Standard-Transformationsprozess ab erweitern, indem Anpassen der Textvorlagen-Direktivenprozessor oder die Textvorlagenhosts.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Textvorlagen-Transformationsprozess](../modeling/the-text-template-transformation-process.md)  
 Beschreibt die Funktionsweise der TextTransformation und erläutert die Rolle des Vorlagenhosts und Direktivenprozessoren.  
  
 [Erstellen von benutzerdefinierten T4-Anweisungsprozessoren für Textvorlagen](../modeling/creating-custom-t4-text-template-directive-processors.md)  
 Der Direktivenprozessor verarbeitet Direktiven in der Vorlage aus, wie z. B. `<#@template#>.` es während der Kompilierung der Vorlage ausgeführt wird und Assemblys und andere Ressourcen laden können. Sie können auch Code einfügen, durch die Ressourcen zur Laufzeit geladen wird. Definieren Sie eigene Direktivenprozessors komplizierter, können Sie die Komplexität der Vorlagen reduzieren.  
  
 [Aufrufen von Texttransformation in einer VS-Erweiterung](../modeling/invoking-text-transformation-in-a-vs-extension.md)  
 Wenn Sie schreiben eine [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Erweiterungstypen, z. B. ein Befehl oder im Menü der Ereignishandler, die Erweiterung kann mithilfe des Textvorlagendiensts jeder Textvorlage transformieren. Sie können übergeben Parameterdaten in die Vorlage über das Sitzungsobjekt und rufen Sie die Werte aus in der Vorlage mithilfe der `<#@parameter#>` Richtlinie.  
  
 [Verarbeiten von Textvorlagen mithilfe eines benutzerdefinierten Hosts](../modeling/processing-text-templates-by-using-a-custom-host.md)  
 Wenn der Code der Textvorlage ausgeführt wird, stellt der Host den Zugriff auf externe Dateien und der Zustand der Anwendung bereit. Z. B. auf dem Host, der Texttransformationen ausgeführt, in wird [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Zugriff ermöglichen dem Projektmappen-Explorer. Es zeigt auch Fehler in das Fenster mit der Fehlermeldung. Wenn Sie Texttransformationen in einem anderen Kontext ausführen möchten, können Sie einen eigenen Host definieren, der Zugriff auf die Dienste verfügbar sind, in diesem Kontext ermöglicht.  
  
 Wenn Sie schreiben eine [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Erweiterung, erwägen Sie die vorhandene Transformation Textdienst, anstatt Ihre eigenen Host zu schreiben. Weitere Informationen finden Sie unter [Aufrufen von Texttransformation in einer VS-Erweiterung](../modeling/invoking-text-transformation-in-a-vs-extension.md).  
  
## <a name="reference"></a>Verweis  
 [Schreiben einer T4-Textvorlage](../modeling/writing-a-t4-text-template.md)  
  
 Stellt die Syntax von Textvorlagendirektiven und Kontrollblöcken bereit.
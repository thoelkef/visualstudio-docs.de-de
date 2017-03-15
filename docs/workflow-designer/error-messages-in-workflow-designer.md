---
title: "Fehlermeldungen im Workflow-Designer | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "WFDErrorMessages.UI"
  - "System.Activities.Presentation.ErrorActivity.UI"
  - "System.Activities.Presentation.View.ErrorView.UI"
ms.assetid: 4d8bbc2e-34fc-477f-9140-4adfd70c34a0
caps.latest.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# Fehlermeldungen im Workflow-Designer
In diesem Thema die Arten von Fehlermeldungen beschrieben, die beim Arbeiten mit [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] auftreten können.  
  
## Situationen, in denen Fehler im Workflow\-Designer auftreten  
 In den folgenden Situationen treten Fehler im [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] auf:  
  
1.  In einem Ausdruck liegt ein Fehler vor.  
  
2.  Die Validierungseinschränkungen einer Aktivität wurden nicht erfüllt.  
  
3.  Die XAML\-Datei enthält Fehler, die bewirken, dass eine Aktivität nicht geladen werden kann.  
  
4.  Die XAML\-Datei enthält Fehler, die bewirken, dass der Workflow nicht geladen werden kann.  
  
 Ungültige Ausdrücke und nicht erfüllte Validierungseinschränkungen bewirken nicht, dass der Workflow nicht erstellt wird.Der Workflow wird erfolgreich erstellt, zur Laufzeit wird jedoch eine Ausnahme vom Typ <xref:System.Activities.InvalidWorkflowException> ausgelöst.Wenn die XAML\-Datei Fehler enthält, schlägt die Erstellung fehl.  
  
 Wenn in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ein Workflow geladen wird, werden seine Fehler in der **Fehlerliste** angezeigt.Um zur Aktivität zu navigieren, die die Fehlerquelle ist, doppelklicken Sie in der **Fehlerliste** auf den Fehler.  
  
### Ausdrucksfehler  
 Ein ungültiger Ausdruck wird durch einen roten Kreis mit einem weißen Ausrufezeichen neben dem Ausdruck gekennzeichnet.Wenn Sie den Mauszeiger über dieses Symbol bewegen, wird ein QuickInfo angezeigt, in der die Fehlerquelle beschrieben wird.Klicken Sie in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] auf den Ausdruck, um die Fehlerquelle mit einer Unterstreichung anzuzeigen.Wenn Sie den Mauszeiger über den unterstrichenen Text halten, wird ein QuickInfo mit einer Beschreibung der Fehlerquelle angezeigt.  
  
### Aktivitätsvalidierungsfehler  
 Wenn die Validierungseinschränkungen einer Aktivität nicht erfüllt wurden, wird ein roter Kreis mit einem weißen Ausrufezeichen in der obersten richtigen Ecke der Aktivität angezeigt.Wenn Sie den Mauszeiger über dieses Symbol bewegen, wird ein QuickInfo angezeigt, in der die Fehlerquelle beschrieben wird.  
  
### XAML\-Ladefehler  
 Wenn eine Aktivität nicht geladen werden kann, wird ein rotes Feld mit dem Text "Aktivität konnte wegen Fehlern im XAML nicht geladen werden" angezeigt.Dies tritt in der Regel auf, wenn der Typ der Aktivität nicht aufgelöst werden kann.Die ungültige Aktivität kann im Designer gelöscht werden, indem das rote Feld markiert und gelöscht wird.  
  
### Workflow\-Ladefehler  
 Wenn ein Workflow nicht geladen werden kann, werden in der Designeroberfläche der Text "In Workflow Designer wurden Probleme mit dem Dokument erkannt" sowie Informationen zu der Ausnahme angezeigt, die bewirkt hat, dass der Workflow nicht geladen werden konnte.Dies tritt in der Regel auf, wenn die XAML\-Datei nicht analysiert werden kann.
---
title: Fehlermeldungen im Workflow-Designer | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- WFDErrorMessages.UI
- System.Activities.Presentation.ErrorActivity.UI
- System.Activities.Presentation.View.ErrorView.UI
ms.assetid: 4d8bbc2e-34fc-477f-9140-4adfd70c34a0
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 748893d7e08ca72140fad31c4546f4166636b8de
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/12/2018
---
# <a name="error-messages-in-workflow-designer"></a>Fehlermeldungen im Workflow-Designer
Dieses Thema beschreibt die Arten von Fehlermeldungen, die bei der Arbeit mit Windows Workflow-Designer gefunden werden können.

## <a name="situations-in-which-errors-in-the-workflow-designer-occur"></a>Situationen, in denen Fehler im Workflow-Designer auftreten
 In den folgenden Situationen treten Fehler im [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] auf:

1.  In einem Ausdruck liegt ein Fehler vor.

2.  Die Validierungseinschränkungen einer Aktivität wurden nicht erfüllt.

3.  Die XAML-Datei enthält Fehler, die bewirken, dass eine Aktivität nicht geladen werden kann.

4.  Die XAML-Datei enthält Fehler, die bewirken, dass der Workflow nicht geladen werden kann.

 Ungültige Ausdrücke und nicht erfüllte Validierungseinschränkungen bewirken nicht, dass der Workflow nicht erstellt wird. Der Workflow wird erfolgreich erstellt, zur Laufzeit wird jedoch eine Ausnahme vom Typ <xref:System.Activities.InvalidWorkflowException> ausgelöst. Wenn die XAML-Datei Fehler enthält, schlägt die Erstellung fehl.

 In [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], wenn ein Workflow geladen wird, werden seine Fehler angezeigt, der **Fehlerliste**. Um auf die Aktivität zu navigieren, die die Quelle des Fehlers ist, doppelklicken Sie auf den Fehler in der **Fehlerliste**.

### <a name="expression-errors"></a>Ausdrucksfehler
 Ein ungültiger Ausdruck wird durch einen roten Kreis mit einem weißen Ausrufezeichen neben dem Ausdruck gekennzeichnet. Wenn Sie den Mauszeiger über dieses Symbol bewegen, wird ein QuickInfo angezeigt, in der die Fehlerquelle beschrieben wird. Klicken Sie in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] auf den Ausdruck, um die Fehlerquelle mit einer Unterstreichung anzuzeigen. Wenn Sie den Mauszeiger über den unterstrichenen Text halten, wird ein QuickInfo mit einer Beschreibung der Fehlerquelle angezeigt.

### <a name="activity-validation-errors"></a>Aktivitätsvalidierungsfehler
 Wenn die Validierungseinschränkungen einer Aktivität nicht erfüllt wurden, wird ein roter Kreis mit einem weißen Ausrufezeichen in der obersten richtigen Ecke der Aktivität angezeigt. Wenn Sie den Mauszeiger über dieses Symbol bewegen, wird ein QuickInfo angezeigt, in der die Fehlerquelle beschrieben wird.

### <a name="xaml-load-errors"></a>XAML-Ladefehler
 Wenn eine Aktivität nicht geladen werden kann, wird ein rotes Feld mit dem Text "Aktivität nicht aufgrund von Fehlern in der XAML geladen werden konnte" angezeigt. Dies tritt normalerweise auf, wenn der Typ der Aktivität nicht aufgelöst werden kann. Die ungültige Aktivität kann im Designer gelöscht werden, indem das rote Feld markiert und gelöscht wird.

### <a name="workflow-load-errors"></a>Workflow-Ladefehler
 Wenn ein Workflow nicht geladen werden kann, wird der Text "Workflow-Designer gefunden Probleme mit dem Dokument" auf der Designeroberfläche, zusammen mit den Informationen zur Ausnahme, die den Fehler beim Laden des Workflows verursacht hat angezeigt. Dies tritt in der Regel auf, wenn die XAML-Datei nicht analysiert werden kann.
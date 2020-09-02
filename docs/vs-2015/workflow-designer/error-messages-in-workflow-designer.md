---
title: Fehlermeldungen in Workflow-Designer | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- WFDErrorMessages.UI
- System.Activities.Presentation.ErrorActivity.UI
- System.Activities.Presentation.View.ErrorView.UI
ms.assetid: 4d8bbc2e-34fc-477f-9140-4adfd70c34a0
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d89c0dcad23a91ec6057311b9afde7d6d4702772
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656755"
---
# <a name="error-messages-in-workflow-designer"></a>Fehlermeldungen im Workflow-Designer
In diesem Thema die Arten von Fehlermeldungen beschrieben, die beim Arbeiten mit [!INCLUDE[wfd1](../includes/wfd1-md.md)] auftreten können.

## <a name="situations-in-which-errors-in-the-workflow-designer-occur"></a>Situationen, in denen Fehler im Workflow-Designer auftreten
 In den folgenden Situationen treten Fehler im [!INCLUDE[wfd2](../includes/wfd2-md.md)] auf:

1. In einem Ausdruck liegt ein Fehler vor.

2. Die Validierungseinschränkungen einer Aktivität wurden nicht erfüllt.

3. Die XAML-Datei enthält Fehler, die bewirken, dass eine Aktivität nicht geladen werden kann.

4. Die XAML-Datei enthält Fehler, die bewirken, dass der Workflow nicht geladen werden kann.

   Ungültige Ausdrücke und nicht erfüllte Validierungseinschränkungen bewirken nicht, dass der Workflow nicht erstellt wird. Der Workflow wird erfolgreich erstellt, zur Laufzeit wird jedoch eine Ausnahme vom Typ <xref:System.Activities.InvalidWorkflowException> ausgelöst. Wenn die XAML-Datei Fehler enthält, schlägt die Erstellung fehl.

   [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Wenn in ein Workflow geladen wird, werden die Fehler in der **Fehlerliste**angezeigt. Um zu der Aktivität zu navigieren, die die Fehlerquelle ist, doppelklicken Sie auf den Fehler in der **Fehlerliste**.

### <a name="expression-errors"></a>Ausdrucksfehler
 Ein ungültiger Ausdruck wird durch einen roten Kreis mit einem weißen Ausrufezeichen neben dem Ausdruck gekennzeichnet. Wenn Sie den Mauszeiger über dieses Symbol bewegen, wird ein QuickInfo angezeigt, in der die Fehlerquelle beschrieben wird. Klicken Sie in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] auf den Ausdruck, um die Fehlerquelle mit einer Unterstreichung anzuzeigen. Wenn Sie den Mauszeiger über den unterstrichenen Text halten, wird ein QuickInfo mit einer Beschreibung der Fehlerquelle angezeigt.

### <a name="activity-validation-errors"></a>Aktivitätsvalidierungsfehler
 Wenn die Validierungseinschränkungen einer Aktivität nicht erfüllt wurden, wird ein roter Kreis mit einem weißen Ausrufezeichen in der obersten richtigen Ecke der Aktivität angezeigt. Wenn Sie den Mauszeiger über dieses Symbol bewegen, wird ein QuickInfo angezeigt, in der die Fehlerquelle beschrieben wird.

### <a name="xaml-load-errors"></a>XAML-Ladefehler
 Wenn eine Aktivität nicht geladen werden kann, wird ein rotes Feld mit dem Text "Aktivität konnte wegen Fehlern im XAML nicht geladen werden" angezeigt. Dies tritt in der Regel auf, wenn der Typ der Aktivität nicht aufgelöst werden kann. Die ungültige Aktivität kann im Designer gelöscht werden, indem das rote Feld markiert und gelöscht wird.

### <a name="workflow-load-errors"></a>Workflow-Ladefehler
 Wenn ein Workflow nicht geladen werden kann, werden in der Designeroberfläche der Text "In Workflow Designer wurden Probleme mit dem Dokument erkannt" sowie Informationen zu der Ausnahme angezeigt, die bewirkt hat, dass der Workflow nicht geladen werden konnte. Dies tritt in der Regel auf, wenn die XAML-Datei nicht analysiert werden kann.
---
title: 'Vorgehensweise: Verwenden der Imports-Designers | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.View.ImportDesigner.UI
ms.assetid: 61328ab6-9b66-4e12-8630-22e30ee8c9d1
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f1c305129a7f46c8d1841f28d8084535ec7e4d9f
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60077575"
---
# <a name="how-to-use-the-imports-designer"></a>Vorgehensweise: Verwenden des Imports-Designers
Der Importe-Designer ermöglicht es Ihnen, Namespaces für die Typen einzugeben, die Sie in den Ausdrücken verwenden. Ähnlich wie die **importiert** oder **mit** Schlüsselwörtern in Visual Basic .NET und c#, Angeben von Namespaces im Importe-Designer können Sie einfach einen Typnamen in den Ausdruck und nicht in einen vollqualifizierten eingeben Version-Typname.  
  
 Der Importe-Designer reagiert sowohl auf Änderungen, die in der Benutzeroberfläche vorgenommen werden, als auch auf Änderungen, die beim Speichern des Workflows gespeichert werden. Wenn der Workflow gespeichert wird, können dem Importe-Designer automatisch Namespaces hinzugefügt werden. Hierzu gehört Folgendes:  
  
- Namespaces für alle Typen, die in Variablen- und Argumentdeklarationen verwendet werden.  
  
- Namespaces für alle Typen, die in Ausdrücken verwendet werden.  
  
- Beliebige andere Namespaces, die zum Serialisieren des Workflows erforderlich sind (z. B., Namespaces, die von benutzerdefinierten Aktivitäten im Workflow verwendet werden).  
  
  Wenn der Workflow gespeichert wird, wird Ihnen möglicherweise auffallen, dass einige Namespaces, die Sie manuell gelöscht haben, wegen der in der vorangehenden Liste beschriebenen Logik automatisch wieder dem Importe-Designer hinzugefügt werden.  
  
### <a name="to-add-a-namespace-to-the-list-of-imported-namespaces"></a>So fügen Sie der Liste der importierten Namespaces einen Namespace hinzu  
  
1. Öffnen Sie eine WCF-Workflowdienstanwendung, die Workflowkonsolenanwendung oder das Aktivitätsbibliotheksprojekt in [!INCLUDE[vs2010](../includes/vs2010-md.md)] oder einer neu gehosteten Workflowanwendung.  
  
2. Klicken Sie auf **Importe** am unteren Rand der hauptarbeitsfläche. Der Import-Designer wird angezeigt.  
  
3. Geben Sie einen Namespace ein, oder wählen Sie einen Namespace im Dropdownlisten-Steuerelement am oberen Rand des Import-Designers aus.  
  
     Während der Eingabe wird eine Liste gültiger Namespaces angezeigt, die mit den eingegebenen Zeichen übereinstimmen.  
  
4. Drücken Sie **EINGABETASTE** den Namespace der Liste hinzufügen.  
  
5. Wenn Sie einen Namespace aus der Liste entfernen möchten, wählen Sie den Namespace, und drücken Sie dann die **löschen** auf der Tastatur die Taste. Beachten Sie, dass ein Namespace nur gelöscht werden kann, wenn er nicht gültig ist, z. B., wenn das Projekt nicht mehr auf die Assembly verweist, die den Namespace enthält.
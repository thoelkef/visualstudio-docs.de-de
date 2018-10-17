---
title: 'Vorgehensweise: Verwenden der Imports-Designers | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.View.ImportDesigner.UI
ms.assetid: 61328ab6-9b66-4e12-8630-22e30ee8c9d1
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 776fbd9ba58268adb16957c732b96a7c8303b213
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49278381"
---
# <a name="how-to-use-the-imports-designer"></a>Vorgehensweise: Verwenden des Imports-Designers
Der Importe-Designer ermöglicht es Ihnen, Namespaces für die Typen einzugeben, die Sie in den Ausdrücken verwenden. Ähnlich wie die **importiert** oder **mit** Schlüsselwörtern in Visual Basic .NET und c#, Angeben von Namespaces im Importe-Designer können Sie einfach einen Typnamen in den Ausdruck und nicht in einen vollqualifizierten eingeben Version-Typname.  
  
 Der Importe-Designer reagiert sowohl auf Änderungen, die in der Benutzeroberfläche vorgenommen werden, als auch auf Änderungen, die beim Speichern des Workflows gespeichert werden. Wenn der Workflow gespeichert wird, können dem Importe-Designer automatisch Namespaces hinzugefügt werden. Hierzu gehört Folgendes:  
  
-   Namespaces für alle Typen, die in Variablen- und Argumentdeklarationen verwendet werden.  
  
-   Namespaces für alle Typen, die in Ausdrücken verwendet werden.  
  
-   Beliebige andere Namespaces, die zum Serialisieren des Workflows erforderlich sind (z. B., Namespaces, die von benutzerdefinierten Aktivitäten im Workflow verwendet werden).  
  
 Wenn der Workflow gespeichert wird, wird Ihnen möglicherweise auffallen, dass einige Namespaces, die Sie manuell gelöscht haben, wegen der in der vorangehenden Liste beschriebenen Logik automatisch wieder dem Importe-Designer hinzugefügt werden.  
  
### <a name="to-add-a-namespace-to-the-list-of-imported-namespaces"></a>So fügen Sie der Liste der importierten Namespaces einen Namespace hinzu  
  
1.  Öffnen Sie eine WCF-Workflowdienstanwendung, die Workflowkonsolenanwendung oder das Aktivitätsbibliotheksprojekt in [!INCLUDE[vs2010](../includes/vs2010-md.md)] oder einer neu gehosteten Workflowanwendung.  
  
2.  Klicken Sie auf **Importe** am unteren Rand der hauptarbeitsfläche. Der Import-Designer wird angezeigt.  
  
3.  Geben Sie einen Namespace ein, oder wählen Sie einen Namespace im Dropdownlisten-Steuerelement am oberen Rand des Import-Designers aus.  
  
     Während der Eingabe wird eine Liste gültiger Namespaces angezeigt, die mit den eingegebenen Zeichen übereinstimmen.  
  
4.  Drücken Sie **EINGABETASTE** den Namespace der Liste hinzufügen.  
  
5.  Wenn Sie einen Namespace aus der Liste entfernen möchten, wählen Sie den Namespace, und drücken Sie dann die **löschen** auf der Tastatur die Taste. Beachten Sie, dass ein Namespace nur gelöscht werden kann, wenn er nicht gültig ist, z. B., wenn das Projekt nicht mehr auf die Assembly verweist, die den Namespace enthält.
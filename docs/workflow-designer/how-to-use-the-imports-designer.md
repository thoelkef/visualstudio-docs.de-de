---
title: "Vorgehensweise: Verwenden des Imports-Designers | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Presentation.View.ImportDesigner.UI"
ms.assetid: 61328ab6-9b66-4e12-8630-22e30ee8c9d1
caps.latest.revision: 10
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# Vorgehensweise: Verwenden des Imports-Designers
Der Importe\-Designer ermöglicht es Ihnen, Namespaces für die Typen einzugeben, die Sie in den Ausdrücken verwenden.Ähnlich wie das Schlüsselwort **Imports** oder **using** in Visual Basic .NET bzw. C\# ermöglicht die Angabe von Namespaces im Importe\-Designer es Ihnen, einfach einen Typnamen statt eines vollqualifizierten Versionstypnamens in einen Ausdruck einzugeben.  
  
 Der Importe\-Designer reagiert sowohl auf Änderungen, die in der Benutzeroberfläche vorgenommen werden, als auch auf Änderungen, die beim Speichern des Workflows gespeichert werden.Wenn der Workflow gespeichert wird, können dem Importe\-Designer automatisch Namespaces hinzugefügt werden.Hierzu gehört Folgendes:  
  
-   Namespaces für alle Typen, die in Variablen\- und Argumentdeklarationen verwendet werden.  
  
-   Namespaces für alle Typen, die in Ausdrücken verwendet werden.  
  
-   Beliebige andere Namespaces, die zum Serialisieren des Workflows erforderlich sind \(z. B., Namespaces, die von benutzerdefinierten Aktivitäten im Workflow verwendet werden\).  
  
 Wenn der Workflow gespeichert wird, wird Ihnen möglicherweise auffallen, dass einige Namespaces, die Sie manuell gelöscht haben, wegen der in der vorangehenden Liste beschriebenen Logik automatisch wieder dem Importe\-Designer hinzugefügt werden.  
  
### So fügen Sie der Liste der importierten Namespaces einen Namespace hinzu  
  
1.  Öffnen Sie eine WCF\-Workflowdienstanwendung, die Workflowkonsolenanwendung oder das Aktivitätsbibliotheksprojekt in [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)] oder einer neu gehosteten Workflowanwendung.  
  
2.  Klicken Sie am unteren Rand der Hauptarbeitsfläche auf **Importe**.Der Import\-Designer wird angezeigt.  
  
3.  Geben Sie einen Namespace ein, oder wählen Sie einen Namespace im Dropdownlisten\-Steuerelement am oberen Rand des Import\-Designers aus.  
  
     Während der Eingabe wird eine Liste gültiger Namespaces angezeigt, die mit den eingegebenen Zeichen übereinstimmen.  
  
4.  Drücken Sie die **EINGABETASTE**, um den Namespace der Liste hinzuzufügen.  
  
5.  Wenn Sie einen Namespace aus der Liste entfernen möchten, wählen den Namespace aus, und drücken Sie dann auf die Tastatur die **ENTF**\-Taste.Beachten Sie, dass ein Namespace nur gelöscht werden kann, wenn der Namespace aus irgendeinem Grund nicht gültig ist, z. B. wenn auf die Assembly, die den Namespace enthält, nicht mehr vom Projekt verwiesen wird.
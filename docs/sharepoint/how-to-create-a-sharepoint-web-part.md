---
title: "Gewusst wie: Erstellen eines SharePoint-Webparts"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Webparts [SharePoint-Entwicklung in Visual Studio], Hinzufügen"
  - "Webparts [SharePoint-Entwicklung in Visual Studio], Erstellen"
ms.assetid: 0d037522-c25e-4c24-93b7-518db0f791b7
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# Gewusst wie: Erstellen eines SharePoint-Webparts
  Sie können ein Webpart erstellen und anpassen, indem Sie ein **Webpart**\-Element zu einem SharePoint\-Projekt hinzufügen. Sie können dann die Codedatei für das Webpart bearbeiten oder einen Designer verwenden.  Weitere Informationen finden Sie unter [Gewusst wie: Erstellen eines SharePoint-Webparts mithilfe eines Designers](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md).  
  
### So erstellen Sie ein SharePoint\-Webpart  
  
1.  Erstellen oder öffnen Sie ein SharePoint\-Projekt.  
  
     Weitere Informationen finden Sie unter [Vorlagen für SharePoint-Projekte und Projektelemente](../sharepoint/sharepoint-project-and-project-item-templates.md).  
  
2.  Wählen Sie im **Projektmappen\-Explorer** den SharePoint\-Projektknoten und anschließend im Menü **ProjektNeues Element hinzufügen** aus.  
  
3.  Erweitern Sie im Dialogfeld **Neues Element hinzufügen** den **SharePoint**\-Knoten und wählen Sie anschließend den Knoten **2010** aus.  
  
4.  Wählen Sie in der Liste der SharePoint\-Vorlagen **Webpart** aus.  
  
5.  Geben Sie im Feld **Name** einen Namen für das Webpart an und wählen Sie dann die Schaltfläche **Hinzufügen** aus.  
  
     Das Webpart wird im **Projektmappen\-Explorer** angezeigt.  Weitere Informationen zu den Dateien, die ein Webpart\-Element enthält, finden Sie unter [Erstellen von Webparts für SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md).  
  
6.  Öffnen Sie im **Projektmappen\-Explorer** die Codedatei für das soeben erstellte Webpart.  
  
     Wenn der Name des Webparts z. B. WebPart1 lautet, öffnen Sie WebPart1.vb \(in Visual Basic\) oder WebPart1.cs \(in C\#\).  
  
7.  Fügen Sie in der Codedatei der <xref:System.Web.UI.Control.CreateChildControls%2A>\-Methode Steuerelemente hinzu.  
  
     Ein Beispiel finden Sie unter [Exemplarische Vorgehensweise: Erstellen eines Webparts für SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md).  
  
## Siehe auch  
 [Erstellen von Webparts für SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [Gewusst wie: Erstellen eines SharePoint-Webparts mithilfe eines Designers](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)   
 [Exemplarische Vorgehensweise: Erstellen eines Webparts für SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)   
 [Exemplarische Vorgehensweise: Erstellen eines Webparts für SharePoint mithilfe eines Designers](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)  
  
  
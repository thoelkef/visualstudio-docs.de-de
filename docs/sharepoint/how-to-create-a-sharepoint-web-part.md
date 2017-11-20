---
title: 'Vorgehensweise: Erstellen eines SharePoint-Webparts | Microsoft Docs'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- Web Parts [SharePoint development in Visual Studio], adding
- Web Parts [SharePoint development in Visual Studio], creating
ms.assetid: 0d037522-c25e-4c24-93b7-518db0f791b7
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 847124dc9a7e4cd80993df5b50c5d3d3b752f228
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-create-a-sharepoint-web-part"></a>Gewusst wie: Erstellen eines SharePoint-Webparts
  Sie können erstellen und Anpassen von einem Webpart durch Hinzufügen einer **Webpart** Element zu einem SharePoint-Projekt, und klicken Sie dann die Codedatei für das Webpart oder mithilfe eines Designers bearbeiten. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen einer SharePoint-Webpart mithilfe eines Designers](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md).  
  
### <a name="to-create-a-sharepoint-web-part"></a>So erstellen Sie ein SharePoint-Webpart  
  
1.  Erstellen oder öffnen Sie ein SharePoint-Projekt.  
  
     Weitere Informationen finden Sie unter [SharePoint-Projekte und Projektelementvorlagen](../sharepoint/sharepoint-project-and-project-item-templates.md).  
  
2.  Wählen Sie den SharePoint-Projektknoten im **Projektmappen-Explorer** und wählen Sie dann **Projekt**, **neues Element hinzufügen**.  
  
3.  In der **neues Element hinzufügen** Dialogfeld erweitern Sie die **SharePoint** Knoten, und wählen Sie dann die **2010** Knoten.  
  
4.  Wählen Sie in der Liste der SharePoint-Vorlagen **Webpart**.  
  
5.  In der **Namen** Feld Geben Sie einen Namen für das Webpart, und wählen Sie dann die **hinzufügen** Schaltfläche.  
  
     Das Webpart wird im **Projektmappen-Explorer**. Weitere Informationen zu den Dateien, die ein Webpart enthält, finden Sie unter [Erstellen von Webparts für SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md).  
  
6.  In **Projektmappen-Explorer**, öffnen Sie die Codedatei für das Webpart, das Sie gerade erstellt haben.  
  
     Wenn der Name des Webparts z. B. WebPart1 lautet, öffnen Sie WebPart1.vb (in Visual Basic) oder WebPart1.cs (in C#).  
  
7.  Fügen Sie in der Codedatei der <xref:System.Web.UI.Control.CreateChildControls%2A>-Methode Steuerelemente hinzu.  
  
     Ein Beispiel finden Sie unter [Exemplarische Vorgehensweise: Erstellen eines Webparts für SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen von Webparts für SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [Vorgehensweise: erstellen ein SharePoint-Webparts mithilfe eines Designers](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)   
 [Exemplarische Vorgehensweise: Erstellen eines Webparts für SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)   
 [Exemplarische Vorgehensweise: Erstellen eines Webparts für SharePoint mithilfe eines Designers](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)  
  
  
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
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 27826859d2bac9b247132e7fcb2c3721b6d38092
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2018
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
  
  
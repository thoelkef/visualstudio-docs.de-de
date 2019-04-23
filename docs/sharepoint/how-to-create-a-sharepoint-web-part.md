---
title: 'Vorgehensweise: Erstellen eines SharePoint-Webparts | Microsoft-Dokumentation'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Web Parts [SharePoint development in Visual Studio], adding
- Web Parts [SharePoint development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 304e9f29d317a5258467e4ff45248d0dd2066d4f
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60041120"
---
# <a name="how-to-create-a-sharepoint-web-part"></a>Vorgehensweise: Erstellen eines SharePoint-Webparts
  Sie können das Erstellen und Anpassen von einem Webpart durch Hinzufügen einer **Webpart** Element zu einem SharePoint-Projekt aus, und bearbeiten Sie dann die Codedatei für das Webpart oder mithilfe eines Designers. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen Sie einen SharePoint-Webpart mithilfe eines Designers](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md).

### <a name="to-create-a-sharepoint-web-part"></a>Zum Erstellen eines SharePoint-Webparts

1. Erstellen oder öffnen Sie ein SharePoint-Projekt.

     Weitere Informationen finden Sie unter [SharePoint-Projekt und Projekt Elementvorlagen](../sharepoint/sharepoint-project-and-project-item-templates.md).

2. Wählen Sie den SharePoint-Projektknoten im **Projektmappen-Explorer** und wählen Sie dann **Projekt** > **neues Element hinzufügen**.

3. In der **neues Element hinzufügen** Dialogfeld erweitern Sie die **SharePoint** Knoten, und wählen Sie dann die **2010** Knoten.

4. Wählen Sie in der Liste der SharePoint-Vorlagen, **Webpart**.

5. In der **Namen** Feld Geben Sie einen Namen für das Webpart, und wählen Sie dann die **hinzufügen** Schaltfläche.

     Das Webpart wird angezeigt, **Projektmappen-Explorer**. Weitere Informationen zu den Dateien, die ein Webpart enthält, finden Sie unter [Webparts für SharePoint erstellen](../sharepoint/creating-web-parts-for-sharepoint.md).

6. In **Projektmappen-Explorer**, öffnen Sie die Codedatei für das Webpart, das Sie gerade erstellt haben.

     Wenn der Name des Webparts ist z. B. *WebPart1*öffnen *WebPart1.vb* (in Visual Basic) oder *WebPart1.cs* (in C# -Referenz).

7. Fügen Sie in der Codedatei der <xref:System.Web.UI.Control.CreateChildControls%2A>-Methode Steuerelemente hinzu.

     Ein Beispiel finden Sie unter [Exemplarische Vorgehensweise: Erstellen Sie ein Webpart für SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md).

## <a name="see-also"></a>Siehe auch
- [Erstellen von Webparts für SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)
- [Vorgehensweise: Erstellen Sie einen SharePoint-Webpart mithilfe eines Designers](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)
- [Exemplarische Vorgehensweise: Erstellen Sie ein Webpart für SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)
- [Exemplarische Vorgehensweise: Erstellen Sie ein Webpart für SharePoint mithilfe eines Designers](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)

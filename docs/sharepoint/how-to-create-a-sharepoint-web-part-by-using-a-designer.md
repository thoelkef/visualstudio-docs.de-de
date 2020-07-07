---
title: 'Vorgehensweise: Erstellen eines SharePoint-Webparts mithilfe eines Designers | Microsoft-Dokumentation'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Web Parts [SharePoint development in Visual Studio], designer
- Web Parts [SharePoint development in Visual Studio], adding
- Web Parts [SharePoint development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0830cec748d68f010397c42334a5ed83365ee6b7
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: de-DE
ms.lasthandoff: 07/06/2020
ms.locfileid: "86016484"
---
# <a name="how-to-create-a-sharepoint-web-part-by-using-a-designer"></a>Vorgehensweise: Erstellen eines SharePoint-Webparts mithilfe eines Designers
  Sie können ein Webpart erstellen, indem Sie einem SharePoint-Projekt ein Element für ein **visuelles Webpart** hinzufügen. Dadurch wird der Visual Web Developer-Designer in Visual Studio geöffnet, in dem Sie Steuerelemente und Code zum Webpart hinzufügen können. Visuelle Webparts funktionieren genauso wie Webparts. Der einzige Unterschied ist, dass Sie visuelle Webparts im Visual Web Developer-Designer entwerfen.

### <a name="to-create-a-project-for-visual-web-parts"></a>So erstellen Sie ein Projekt für visuelle Webparts

1. Klicken Sie in der Menüleiste auf **Datei** >**Neu** > **Projekt**.

     Das Dialogfeld **Neues Projekt** wird angezeigt.

2. Erweitern Sie im Dialogfeld **Neues Projekt** unter **Visual c#** oder **Visual Basic**den Knoten **Office/SharePoint** , und wählen Sie dann die Kategorie **SharePoint-Lösungen** aus.

3. Wählen Sie in der Liste der Projektvorlagen die Option **SharePoint 2013-visuelles Webpart**aus, und klicken Sie dann auf die Schaltfläche **OK** .

     Der Assistent zum Anpassen von **SharePoint** wird angezeigt.

4. Geben Sie auf der Seite **Standort und Sicherheitsebene für Debugging angeben** die URL einer SharePoint-Website an, die sich auf dem lokalen Computer befindet, und klicken Sie dann auf die Schaltfläche **Fertig** stellen.

     In **Projektmappen-Explorer**wird ein Webpart angezeigt. Nachdem Sie das Webpart im Visual Web Developer-Designer entworfen haben, testen Sie es auf der Site, die Sie angeben.

### <a name="to-add-a-visual-web-part-to-an-existing-sharepoint-project"></a>So fügen Sie einem vorhandenen SharePoint-Projekt ein visuelles Webpart hinzu

1. Wählen Sie in der Menüleiste **Projekt**  >  **Neues Element hinzufügen**aus.

2. Wählen Sie im Dialogfeld **Neues Element hinzufügen** den Knoten **Office/SharePoint** aus.

3. Wählen Sie in der Liste der Projektvorlagen die Option **visuelles Webpart**aus, benennen Sie Sie, und wählen Sie dann die Schaltfläche **Hinzufügen** aus.

     In **Projektmappen-Explorer**wird Ihr Webpart angezeigt. Nachdem Sie das Webpart im Visual Web Developer-Designer entworfen haben, testen Sie es auf der Site, die Sie angeben.

## <a name="see-also"></a>Weitere Informationen
- [Erstellen von Webparts für SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)
- [Vorgehensweise: Erstellen eines SharePoint-Webparts](../sharepoint/how-to-create-a-sharepoint-web-part.md)
- [Exemplarische Vorgehensweise: Erstellen eines Webparts für SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)
- [Exemplarische Vorgehensweise: Erstellen eines Webparts für SharePoint mithilfe eines Designers](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)

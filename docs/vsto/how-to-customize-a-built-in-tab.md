---
title: 'Vorgehensweise: Anpassen einer integrierten Registerkarte | Microsoft Docs'
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
helpviewer_keywords:
- Ribbon [Office development in Visual Studio], tabs
- built-in tabs [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 251c1cf70ab1d528f65d558208f0f2d43e10388a
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-customize-a-built-in-tab"></a>Gewusst wie: Anpassen einer integrierten Registerkarte
  Einer integrierten Registerkarte können Gruppen und Steuerelemente hinzugefügt werden. Eine integrierte Registerkarte ist eine Registerkarte, die sich bereits auf dem Menüband einer Microsoft Office-Anwendung befindet. Z. B. die **Daten** Registerkarte ist eine integrierte Registerkarte in Excel. Wenn Sie eine benutzerdefinierte Gruppe erstellen, wird diese auf der Registerkarte an letzter Stelle angezeigt. Sie können die Gruppe aber an eine beliebige Position auf der Registerkarte verschieben.  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
> [!NOTE]  
>  Sie können einer integrierten Registerkarte Gruppen hinzufügen, die integrierten Gruppen jedoch nicht von einer integrierten Registerkarte entfernen.  
  
### <a name="to-add-groups-to-a-built-in-tab"></a>So fügen Sie einer integrierten Registerkarte Gruppen hinzu  
  
1.  Mit der rechten Maustaste in der Menüband-Codedatei **Projektmappen-Explorer**, und klicken Sie dann auf **Sicht-Designer**.  
  
    > [!NOTE]  
    >  Wenn in der Menüband-Codedatei angezeigt wird **Projektmappen-Explorer**, müssen Sie hinzufügen, eine **Element "Menüband"** zu Ihrem Projekt. Finden Sie unter [wie: Erste Schritte beim Anpassen des Menübands](../vsto/how-to-get-started-customizing-the-ribbon.md).  
  
2.  Maustaste auf eine beliebige Registerkarte im Menüband-Designer, und klicken Sie dann auf **Eigenschaften**.  
  
3.  In der **Eigenschaften** Fenster, erweitern Sie die **ControlId** -Eigenschaft, und legen die **ControlIdType** Eigenschaft **Office**.  
  
4.  Legen Sie die **OfficeId** Eigenschaft, um die *Steuerelement-ID* der integrierten Registerkarte, die Sie anpassen möchten.  
  
     Die Steuerelement-ID ist der Name, mit dem Registerkarten, Gruppen und Steuerelemente eindeutig identifiziert werden, die in Microsoft Office-Anwendungen integriert sind.  
  
     Eine Liste der Steuerelement-IDs, finden Sie unter [Office 2010 Help Files: Office Fluent User Interface Control Identifiers](http://go.microsoft.com/fwlink/?LinkID=181052).  
  
5.  Aus der **Steuerelemente für Office-Menübänder** auf der Registerkarte die **Toolbox**, ziehen Sie Gruppen auf der Registerkarte ".  
  
    > [!NOTE]  
    >  Integrierte Gruppen werden im Designer nicht angezeigt. Daher ist die einzige Möglichkeit, zu bestimmen, ob Sie mit einer integrierten Registerkarte arbeiten, überprüfen Sie die **ControlId** -Eigenschaft auf der Registerkarte.  
  
### <a name="to-position-groups-on-a-built-in-tab"></a>So ordnen Sie Gruppen auf einer integrierten Registerkarte an  
  
1.  Wählen Sie im Menüband-Designer eine benutzerdefinierte Gruppe aus.  
  
2.  In der **Eigenschaften** Fenster, erweitern Sie die **Position** Eigenschaft.  
  
3.  Legen Sie die **PositionType** Eigenschaft auf den entsprechenden Wert:  
  
    -   **BeforeOfficeId** wird die Gruppe vor einer angegebenen integrierten Gruppe.  
  
    -   **AfterOfficeId** wird die Gruppe hinter einer angegebenen integrierten Gruppe.  
  
4.  Legen Sie die **OfficeId** Eigenschaft, um die Steuerelement-ID einer integrierten Gruppe.  
  
     Eine Liste der Steuerelement-IDs, finden Sie unter [Office 2010 Help Files: Office Fluent User Interface Control Identifiers](http://go.microsoft.com/fwlink/?LinkID=181052).  
  
## <a name="see-also"></a>Siehe auch  
 [Übersicht über das Menüband](../vsto/ribbon-overview.md)   
 [Menüband-Designer](../vsto/ribbon-designer.md)   
 [Menüband-XML](../vsto/ribbon-xml.md)   
 [Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Registerkarte mit Menüband-Designer](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Registerkarte mit Menüband-XML](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)   
 [Vorgehensweise: Erste Schritte beim Anpassen des Menübands](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [Vorgehensweise: Ändern der Position einer Registerkarte auf dem Menüband](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)   
 [Vorgehensweise: Hinzufügen von Steuerelementen zur Backstage-Ansicht](../vsto/how-to-add-controls-to-the-backstage-view.md)   
 [Vorgehensweise: Anzeigen von Add-In-Benutzeroberflächenfehlern](../vsto/how-to-show-add-in-user-interface-errors.md)  
  
  
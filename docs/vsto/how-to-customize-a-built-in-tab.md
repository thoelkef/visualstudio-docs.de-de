---
title: "Gewusst wie: Anpassen einer integrierten Registerkarte"
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
helpviewer_keywords: 
  - "Integrierte Registerkarten [Office-Entwicklung in Visual Studio]"
  - "Menüband [Office-Entwicklung in Visual Studio], Registerkarten"
ms.assetid: 197a7aaa-a51d-496c-b904-b9421849fad9
caps.latest.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 27
---
# Gewusst wie: Anpassen einer integrierten Registerkarte
  Einer integrierten Registerkarte können Gruppen und Steuerelemente hinzugefügt werden.  Eine integrierte Registerkarte ist eine Registerkarte, die sich bereits auf dem Menüband einer Microsoft Office\-Anwendung befindet.  Die Registerkarte **Daten** ist z. B. eine integrierte Registerkarte in Excel.  Wenn Sie eine benutzerdefinierte Gruppe erstellen, wird diese auf der Registerkarte an letzter Stelle angezeigt. Sie können die Gruppe aber an eine beliebige Position auf der Registerkarte verschieben.  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
> [!NOTE]  
>  Sie können einer integrierten Registerkarte Gruppen hinzufügen, die integrierten Gruppen jedoch nicht von einer integrierten Registerkarte entfernen.  
  
### So fügen Sie einer integrierten Registerkarte Gruppen hinzu  
  
1.  Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf die Menüband\-Codedatei, und klicken Sie danach auf **Ansicht\-Designer**.  
  
    > [!NOTE]  
    >  Wenn die Menüband\-Codedatei nicht im **Projektmappen\-Explorer** angezeigt wird, müssen Sie dem Projekt ein **Menübandelement** hinzufügen.  Weitere Informationen finden Sie unter [Gewusst wie: Erste Schritte beim Anpassen der Multifunktionsleiste](../vsto/how-to-get-started-customizing-the-ribbon.md).  
  
2.  Klicken Sie mit der rechten Maustaste auf eine beliebige Registerkarte im Menüband\-Designer, und klicken Sie anschließend auf **Eigenschaften**.  
  
3.  Erweitern Sie im Fenster **Eigenschaften** die Eigenschaft **ControlId**, und legen Sie die Eigenschaft **ControlIdType** auf **Office** fest.  
  
4.  Legen Sie die **OfficeId**\-Eigenschaft auf die *Steuerelement\-ID* der integrierten Registerkarte fest, die Sie anpassen möchten.  
  
     Die Steuerelement\-ID ist der Name, mit dem Registerkarten, Gruppen und Steuerelemente eindeutig identifiziert werden, die in Microsoft Office\-Anwendungen integriert sind.  
  
     Eine Liste der Steuerelement\-IDs finden Sie unter [Office 2010\-Hilfedateien: Steuerelement\-IDs für die Office Fluent\-Benutzeroberfläche](http://go.microsoft.com/fwlink/?LinkID=181052).  
  
5.  Ziehen Sie Gruppen von der Registerkarte **Steuerelemente für Office\-Menübänder**  der **Toolbox** auf die Registerkarte.  
  
    > [!NOTE]  
    >  Integrierte Gruppen werden im Designer nicht angezeigt.  Sie können daher nur durch Prüfen der **ControlId**\-Eigenschaft auf der Registerkarte bestimmen, ob Sie mit einer integrierten Registerkarte arbeiten.  
  
### So ordnen Sie Gruppen auf einer integrierten Registerkarte an  
  
1.  Wählen Sie im Menüband\-Designer eine benutzerdefinierte Gruppe aus.  
  
2.  Erweitern Sie im Fenster **Eigenschaften** die Eigenschaft **Position**.  
  
3.  Legen Sie die **PositionType**\-Eigenschaft auf den entsprechenden Wert fest:  
  
    -   Mit **BeforeOfficeId** wird die Gruppe vor einer angegebenen integrierten Gruppe angeordnet.  
  
    -   Mit **AfterOfficeId** wird die Gruppe hinter einer angegebenen integrierten Gruppe angeordnet.  
  
4.  Legen Sie die **OfficeId**\-Eigenschaft auf die Steuerelement\-ID einer integrierten Gruppe fest.  
  
     Eine Liste der Steuerelement\-IDs finden Sie unter [Office 2010\-Hilfedateien: Steuerelement\-IDs für die Office Fluent\-Benutzeroberfläche](http://go.microsoft.com/fwlink/?LinkID=181052).  
  
## Siehe auch  
 [Übersicht über die Multifunktionsleiste](../vsto/ribbon-overview.md)   
 [Multifunktionsleisten-Designer](../vsto/ribbon-designer.md)   
 [Multifunktionsleisten-XML](../vsto/ribbon-xml.md)   
 [Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Registerkarte mit dem Multifunktionsleisten-Designer](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Registerkarte mit Multifunktionsleisten-XML](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)   
 [Gewusst wie: Erste Schritte beim Anpassen der Multifunktionsleiste](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [Gewusst wie: Ändern der Position einer Registerkarte im Menüband](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)   
 [Gewusst wie: Hinzufügen von Steuerelementen zur Backstage-Ansicht](../vsto/how-to-add-controls-to-the-backstage-view.md)   
 [Gewusst wie: Anzeigen von Add-In-Benutzeroberflächenfehlern](../vsto/how-to-show-add-in-user-interface-errors.md)  
  
  
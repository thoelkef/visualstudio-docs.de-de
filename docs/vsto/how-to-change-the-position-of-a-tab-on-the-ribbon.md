---
title: "Gewusst wie: &#196;ndern der Position einer Registerkarte im Men&#252;band"
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
  - "Menüband [Office-Entwicklung in Visual Studio], Registerkarten"
ms.assetid: 3f0906e3-9708-4136-ac49-986bc4c92ea4
caps.latest.revision: 26
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 25
---
# Gewusst wie: &#196;ndern der Position einer Registerkarte im Men&#252;band
  Sie können die Reihenfolge der benutzerdefinierten Registerkarten auf einem Menüband mithilfe von **Registerkartenauflistungs\-Editor** ändern.  Benutzerdefinierte Registerkarten können vor oder nach einer integrierten Registerkarte auf dem Menüband angeordnet werden.  Eine integrierte Registerkarte ist eine Registerkarte, die sich bereits auf dem Menüband einer Microsoft Office\-Anwendung befindet.  Die Registerkarte **Daten** ist z. B. eine integrierte Registerkarte in Excel.  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### So ändern Sie die Reihenfolge der Registerkarten auf dem Menüband  
  
1.  Wählen Sie die Codedatei für das Menüband \(VB\- oder CS\-Datei\) im **Projektmappen\-Explorer** aus.  
  
2.  Klicken Sie im Menü **Ansicht** auf **Designer**.  
  
3.  Klicken Sie mit der rechten Maustaste auf den Menüband\-Designer, und klicken Sie anschließend auf **Eigenschaften**.  
  
4.  Wählen Sie im Fenster **Eigenschaften** die **Tabs**\-Eigenschaft, und klicken Sie auf die Schaltfläche mit den Auslassungszeichen \(![Auslassungszeichen im ASP.NET Mobile-Designer](../sharepoint/media/mwellipsis.png "Auslassungszeichen im ASP.NET Mobile-Designer")\).  
  
     Der **Registerkartenauflistungs\-Editor** wird angezeigt.  
  
5.  Wählen Sie im **Registerkartenauflistungs\-Editor** in der **Member**\-Liste die zu verschiebende Registerkarte, und klicken Sie auf den Aufwärts\- bzw. den Abwärtspfeil, um die Reihenfolge der Registerkarten zu ändern.  
  
### So positionieren Sie eine Registerkarte vor oder nach einer integrierten Registerkarte auf dem Menüband  
  
1.  Wählen Sie im Menüband\-Designer eine benutzerdefinierte Registerkarte aus.  
  
2.  Im **Eigenschaften** erweitern Sie die Eigenschaft **ControlId**, und überprüfen Sie, ob der Wert der \- Eigenschaft **ControlIdType** zu **Benutzerdefiniert** festgelegt ist.  
  
3.  Erweitern Sie im Fenster **Eigenschaften** die Eigenschaft **Position**.  
  
4.  Legen Sie die **PositionType**\-Eigenschaft auf den entsprechenden Wert fest:  
  
    -   Mit **BeforeOfficeId** wird die Gruppe vor einer angegebenen integrierten Registerkarte angeordnet.  
  
    -   Mit **AfterOfficeId** wird die Gruppe nach einer angegebenen integrierten Registerkarte angeordnet.  
  
5.  Legen Sie die **OfficeId**\-Eigenschaft auf die Steuerelement\-ID einer integrierten Registerkarte fest.  
  
     Eine Liste der Steuer\-IDs, finden Sie unter [Office 2010\-Hilfedateien: Benutzeroberflächen\-Identitätskennzeichen Office fließende](http://go.microsoft.com/fwlink/?LinkID=181052).  
  
## Siehe auch  
 [Übersicht über die Multifunktionsleiste](../vsto/ribbon-overview.md)   
 [Multifunktionsleisten-Designer](../vsto/ribbon-designer.md)   
 [Multifunktionsleisten-XML](../vsto/ribbon-xml.md)   
 [Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Registerkarte mit dem Multifunktionsleisten-Designer](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Registerkarte mit Multifunktionsleisten-XML](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)  
  
  
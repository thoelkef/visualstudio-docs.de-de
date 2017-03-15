---
title: "Gewusst wie: Erstellen von parametrisierten TableAdapter-Abfragen | Microsoft Docs"
ms.custom: ""
ms.date: "09/21/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "Daten [Visual Studio], Suchen nach Daten"
  - "Daten [Visual Studio], TableAdapters"
  - "Abfragen [Visual Studio], Erstellen"
  - "Abfragen [Visual Studio], TableAdapters"
  - "TableAdapters, Parametrisierte Abfragen"
  - "TableAdapters, Suchen nach Daten"
ms.assetid: 104d1d19-b5a9-4071-b81e-1b3af08e9c7b
caps.latest.revision: 20
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Gewusst wie: Erstellen von parametrisierten TableAdapter-Abfragen
Eine parametrisierte Abfrage gibt Daten zurück, die den Bedingungen einer WHERE\-Klausel in der Abfrage entsprechen.  Sie können beispielsweise eine Kundenliste parametrisieren, sodass nur Kunden in einem bestimmten Ort angezeigt werden. Fügen Sie dazu `WHERE City = @City` am Ende der SQL\-Anweisung hinzu, was eine Liste von Kunden ausgibt.  
  
 Parametrisierte TableAdapter\-Abfragen im [Dataset\-Designer](../data-tools/creating-and-editing-typed-datasets.md) oder während des Erstellens von datengebundenen Formularen in einer Windows\-Anwendung erstellen Sie mit dem Befehl **Parametrisierte Datenquelle** im Menü **Daten**.  Der Befehl **Parametrisierte Datenquelle** erstellt außerdem Steuerelemente auf dem Formular für die Eingabe von Parameterwerten und das Ausführen der Abfrage.  Weitere Informationen finden Sie unter [Dialogfeld "Suchkriterien\-Generator"](../Topic/Search%20Criteria%20Builder%20Dialog%20Box.md).  
  
> [!NOTE]
>  Wenn Sie eine parametrisiere Abfrage konstruieren, verwenden Sie Parameter, die notationsspezifisch für die Datenbank sind, für die Sie den Code schreiben.  Zum Beispiel verwenden Access\- und OleDb\-Datenquellen das Fragezeichen \(?\) zur Angabe von Parametern, sodass die WHERE\-Klausel wie folgt aussieht: `WHERE City = ?`.  
  
> [!NOTE]
>  Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen.  Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren**, um die Einstellungen zu ändern.  Weitere Informationen finden Sie unter [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/de-de/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Erstellen einer parametrisieren TableAdapter\-Abfrage  
  
#### So erstellen Sie parametrisierte Abfrage im DataSet\-Designer  
  
-   Erstellen Sie einen neuen TableAdapter und fügen Sie eine WHERE\-Klausel mit den gewünschten Parametern zur SQL\-Anweisung hinzu.  Weitere Informationen finden Sie unter [Gewusst wie: Erstellen von TableAdapters](../data-tools/create-and-configure-tableadapters.md).  
  
     \- oder \-  
  
-   Fügen Sie eine Abfrage zu einem vorhandenen TableAdapter hinzu und dann eine WHERE\-Klausel mit den gewünschten Parametern für die SQL\-Anweisung.  Weitere Informationen finden Sie unter [Gewusst wie: Erstellen von TableAdapter\-Abfragen](../data-tools/how-to-create-tableadapter-queries.md).  
  
#### So erstellen Sie eine parametrisierte Abfrage beim Entwerfen eines datengebundenen Formulars  
  
1.  Wählen Sie ein Steuerelement auf dem Formular, das bereits an ein Dataset gebunden ist.  Weitere Informationen finden Sie unter [Binden von Windows Forms\-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md).  
  
2.  Klicken Sie auf dem Menü **Daten** auf **Abfrage hinzufügen**.  
  
3.  Füllen Sie das Dialogfeld **Suchkriterien\-Generator** aus und fügen Sie dann eine WHERE\-Klausel mit den gewünschten Parametern für die SQL\-Anweisung hinzu.  Weitere Informationen finden Sie unter [Dialogfeld "Suchkriterien\-Generator"](../Topic/Search%20Criteria%20Builder%20Dialog%20Box.md).  
  
## Siehe auch  
 [TableAdapters](../Topic/TableAdapters.md)   
 [Herstellen von Datenverbindungen in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Vorbereiten der Anwendung auf den Empfang von Daten](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Abrufen von Daten für die Anwendung](../data-tools/fetching-data-into-your-application.md)   
 [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Bearbeiten von Daten in der Anwendung](../data-tools/editing-data-in-your-application.md)   
 [Überprüfen von Daten](../Topic/Validating%20Data.md)   
 [Speichern von Daten](../data-tools/saving-data.md)   
 [Exemplarische Vorgehensweisen zur Arbeit mit Daten](../Topic/Data%20Walkthroughs.md)
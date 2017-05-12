---
title: "Gewusst wie: Ausf&#252;hren eines Bildlaufs durch Datenbankdatens&#228;tze in einem Arbeitsblatt"
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
  - "Daten [Office-Entwicklung in Visual Studio], Scrollen durch Datenbankdatensätzen"
  - "Datenbanken [Office-Entwicklung in Visual Studio], Scrollen von Datensätzen"
  - "Datensätze [Office-Entwicklung in Visual Studio], Scrollen"
  - "Arbeitsblätter [Office-Entwicklung in Visual Studio], Scrollen von Datensätzen"
ms.assetid: aea4c86c-9d6d-47dd-8977-066e21945dab
caps.latest.revision: 33
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 32
---
# Gewusst wie: Ausf&#252;hren eines Bildlaufs durch Datenbankdatens&#228;tze in einem Arbeitsblatt
  Im folgenden Verfahren wird veranschaulicht, wie mit dem Designer ein einziges Feld aus einer Datenbanktabelle in einem Microsoft Office Excel\-Arbeitsblatt mit Steuerelementen angezeigt wird, mit deren Hilfe Endbenutzer einen Bildlauf durch alle Datensätze durchführen können.  
  
 Sie können den Designer nur in Projekten auf Dokumentebene verwenden.  Sie können jedoch auch Steuerelemente hinzufügen und diese zur Laufzeit programmgesteuert an Daten binden.  Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Einfache Datenbindung in einem VSTO-Add-In-Projek](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md).  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
### So führen Sie einen Bildlauf durch Datenbankdatensätze in einem Arbeitsblatt aus  
  
1.  Öffnen Sie in Visual Studio ein Excel\-Anwendungsprojekt.  
  
2.  Öffnen Sie das **Datenquellenfenster**, und erstellen Sie eine Datenquelle aus der Datenbank.  Weitere Informationen finden Sie unter [Gewusst wie: Herstellen einer Verbindung zu Daten in einer Datenbank](~/data-tools/how-to-connect-to-data-in-a-database.md).  
  
3.  Erweitern Sie die Tabelle, in der die anzuzeigenden Daten enthalten sind, und wählen Sie die entsprechende Spalte aus.  
  
4.  Öffnen Sie die Liste der Steuerelemente, und wählen Sie **NamedRange** aus.  
  
5.  Ziehen Sie das <xref:Microsoft.Office.Tools.Excel.NamedRange>\-Steuerelement auf die Zelle, in der die Daten angezeigt werden sollen.  
  
6.  Fügen Sie dem Arbeitsblatt ein <xref:System.Windows.Forms.BindingNavigator>\-Steuerelement von der Registerkarte **Windows Forms** in der **Toolbox** hinzu, und legen Sie die zu verwendenden Steuerelemente fest.  Weitere Informationen finden Sie unter [Übersicht über das BindingNavigator-Steuerelement &#40;Windows Forms&#41;](http://msdn.microsoft.com/library/4423eede-f8d1-4d02-822f-5bf8432680d0).  
  
## Siehe auch  
 [Binden von Daten an Steuerelemente in Office-Projektmappen](../vsto/binding-data-to-controls-in-office-solutions.md)  
  
  
---
title: "Binden von Steuerelementen an Daten in Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "Datenquellenfenster"
  - "Datenquellen, Anzeigen von Daten"
  - "Daten, Anzeigen"
  - "Anzeigen von Daten"
ms.assetid: be8b6623-86a6-493e-ab7a-050de4661fd6
caps.latest.revision: 40
caps.handback.revision: 29
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Binden von Steuerelementen an Daten in Visual Studio
Sie können Daten für Benutzer der Anwendung anzeigen, indem Sie Daten an Steuerelemente binden.  Sie können diese datengebundenen Steuerelemente erstellen, indem Sie Elemente vom Datenquellenfenster auf eine Entwurfsoberfläche in Visual Studio ziehen.  
  
 In diesem Thema werden die Datenquellen, mit denen Sie datengebundene Steuerelemente erstellen können, beschrieben.  Es werden auch einige der allgemeinen Aufgaben beschrieben, die mit der Datenbindung zusammenhängen.  Genauere Informationen zum Erstellen von datengebundenen Steuerelementen finden Sie unter [Binden von Windows Forms\-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md), [Binden von WPF\-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md) und [Binden von Silverlight\-Steuerelementen an Daten in Visual Studio](../Topic/Binding%20Silverlight%20Controls%20to%20Data%20in%20Visual%20Studio.md).  
  
## Datenquellen  
 Eine Datenquelle stellt die Daten dar, die der Anwendung zur Verfügung stehen.  Sie können Datenquellen aus Datenbanken, Diensten oder Objekten erstellen.  Weitere Informationen finden Sie unter [Übersicht über Datenquellen](../data-tools/add-new-data-sources.md).  
  
 Einige Datenquellen ermöglichen es Ihnen, datengebundene Steuerelemente durch Ziehen von Elementen vom Datenquellenfenster zu erstellen. Bei anderen Datenquellen ist dies hingegen nicht der Fall.  Die folgende Tabelle zeigt, welche Datenquellen unterstützt werden.  
  
|Datenquelle|Drag & Drop\-Unterstützung im **Windows Forms\-Designer**|Drag & Drop\-Unterstützung im **WPF\-Designer**|Drag & Drop\-Unterstützung im **Silverlight\-Designer**|  
|-----------------|---------------------------------------------------------------|-----------------------------------------------------|-------------------------------------------------------------|  
|DataSet|Ja|Ja|Nein|  
|Entity Data Model|Nein<sup>1</sup>|Ja|Ja|  
|LINQ to SQL\-Klassen|Nein<sup>2</sup>|Nein<sup>2</sup>|Nein<sup>2</sup>|  
|Dienste \(einschließlich [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)], WCF\-Diensten und Webdiensten\)|Ja|Ja|Ja|  
|Objekt|Ja|Ja|Ja|  
|SharePoint|Ja|Ja|Ja|  
  
 1.  Wenn der **Windows Forms\-Designer** geöffnet ist, sind Entitäten im Datenquellenfenster schreibgeschützt, und sie können nicht in den Designer gezogen werden.  Sie können jedoch nach wie vor datengebundene Steuerelemente erstellen, indem Sie eine neue Objektdatenquelle hinzufügen, die auf dem Entity Data Model basiert, und diese Objekte anschließend in den Designer ziehen.  
  
 2.  LINQ to SQL\-Klassen werden nicht im Datenquellenfenster angezeigt.  Sie können jedoch eine neue Objektdatenquelle hinzufügen, die auf LINQ to SQL\-Klassen basiert und anschließend diese Objekte in den Designer ziehen, um datengebundene Steuerelemente zu erstellen.  Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Erstellen von LINQ to SQL\-Klassen \(O\/R\-Designer\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md).  
  
## Datenquellenfenster  
 Datenquellen stehen dem Projekt als Elemente im Datenquellenfenster zur Verfügung.  Sie können Elemente aus diesem Fenster ziehen, um Steuerelemente zu erstellen, die an die zugrunde liegenden Daten gebunden werden.  Weitere Informationen finden Sie unter [Datenquellenfenster](../Topic/Data%20Sources%20Window.md).  
  
 Für jeden Datentyp, der im Datenquellenfenster angezeigt wird, wird ein standardmäßiges Steuerelement erstellt, wenn das Element in den Designer gezogen wird.  Bevor Sie ein Element aus dem Datenquellenfenster ziehen, können Sie das Steuerelement, das erstellt wird, ändern.  Weitere Informationen finden Sie unter [Festlegen des Steuerelements, das beim Ziehen aus dem Datenquellenfenster erstellt werden soll](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
## Aufgaben beim Binden von Steuerelementen an Daten  
 In der folgenden Tabelle sind einige der häufigsten Aufgaben aufgeführt, die bei der Bindung von Steuerelementen an Daten ausgeführt werden müssen.  
  
|Aufgabe|Weitere Informationen|  
|-------------|---------------------------|  
|Öffnen Sie das **Datenquellenfenster**.|[Gewusst wie: Öffnen des Datenquellenfensters](../data-tools/how-to-open-the-data-sources-window.md)|  
|Fügen Sie dem Projekt eine Datenquelle hinzu.|[Gewusst wie: Herstellen einer Verbindung zu Daten in einer Datenbank](../data-tools/how-to-connect-to-data-in-a-database.md)<br /><br /> [Gewusst wie: Herstellen einer Verbindung mit Daten in Objekten](../Topic/How%20to:%20Connect%20to%20Data%20in%20Objects.md)<br /><br /> [Gewusst wie: Herstellen einer Verbindung mit Daten in einem Dienst](../data-tools/how-to-connect-to-data-in-a-service.md)|  
|Legen Sie das Steuerelement fest, das erstellt wird, wenn Sie ein Element vom Datenquellenfenster in den Designer ziehen.|[Festlegen des Steuerelements, das beim Ziehen aus dem Datenquellenfenster erstellt werden soll](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)|  
|Ändern Sie die Liste der Steuerelemente, die Elementen im Datenquellenfenster zugeordnet sind.|[Hinzufügen benutzerdefinierter Steuerelemente zum Datenquellenfenster](../data-tools/add-custom-controls-to-the-data-sources-window.md)|  
|Erstellen Sie datengebundene Steuerelemente.|[Binden von Windows Forms\-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)<br /><br /> [Binden von WPF\-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)<br /><br /> [Binden von Silverlight\-Steuerelementen an Daten in Visual Studio](../Topic/Binding%20Silverlight%20Controls%20to%20Data%20in%20Visual%20Studio.md)|  
  
 Nach dem Erstellen von Steuerelementen, die an Daten gebunden sind, möchten Sie eventuell eine der folgenden Aufgaben ausführen:  
  
|Aufgabe|Weitere Informationen|  
|-------------|---------------------------|  
|Bearbeiten der Daten in der zugrunde liegenden Datenquelle|[Bearbeiten von Daten in der Anwendung](../data-tools/editing-data-in-your-application.md)|  
|Überprüfen der an den Daten vorgenommenen Änderungen|[Überprüfen von Daten](../Topic/Validating%20Data.md)|  
|Speichern der aktualisierten Daten in der Datenbank|[Speichern von Daten](../data-tools/saving-data.md)|  
  
## Siehe auch  
 [Binden von Windows Forms\-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Binden von WPF\-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)   
 [Binden von Silverlight\-Steuerelementen an Daten in Visual Studio](../Topic/Binding%20Silverlight%20Controls%20to%20Data%20in%20Visual%20Studio.md)   
 [Gewusst wie: Binden von Steuerelementen an Bilder aus einer Datenbank](../data-tools/bind-controls-to-pictures-from-a-database.md)   
 [Übersicht über Datenanwendungen in Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Herstellen von Datenverbindungen in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Bearbeiten von Daten in der Anwendung](../data-tools/editing-data-in-your-application.md)   
 [Überprüfen von Daten](../Topic/Validating%20Data.md)   
 [Speichern von Daten](../data-tools/saving-data.md)   
 [Tools zum Arbeiten mit Datenquellen in Visual Studio](../Topic/Tools%20for%20Working%20with%20Data%20Sources%20in%20Visual%20Studio.md)
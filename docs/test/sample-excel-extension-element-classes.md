---
title: "Sample Excel Extension: Element Classes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7c251098-00aa-49cf-9e37-5717c0c6b3f1
caps.latest.revision: 9
ms.author: "mlearned"
manager: "douge"
caps.handback.revision: 9
---
# Sample Excel Extension: Element Classes
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die Erweiterung verwendet von <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement> abgeleitete Klassen und stellt das Arbeitsblattsteuerelement und Zellensteuerelement in [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)] dar.  
  
 Das Basiselement für diese Erweiterung ist `ExcelElement`.  Die `ExcelWorksheetElement`\-Klasse und die `ExcelCellElement`\-Klasse erben von diesem Element.  
  
## Element\- und ElementInformation\-Klassen  
 `Element`  ist die Basisklasse für alle Benutzeroberflächenelemente für die Excel\-Erweiterung und erbt von der <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement>\-Klasse.  `ElementInformation` ist die Basisklasse für die Elementinformationsklassen im Beispiel und verfügt nicht über Member.  
  
#### Einfache Eigenschaften und Methoden  
 Diese Member geben einfache Werte zurück, z. B. den Wert der `Name`\-Eigenschaft oder den Wert der `ClassName`\-Eigenschaft. Der Code ist einfach zu verstehen und zu lesen.  Einige Werte werden mit der `Utility`\-Klasse zurückgegeben, die weiter unten in diesem Thema erläutert wird.  Andere geben `null` zurück, da sie in dieser Beispielerweiterung nicht relevant sind.  Zwei Member sind dabei besonders interessant: die <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A>\-Eigenschaft und die <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.CacheProperties%2A>\-Methode.  
  
#### QueryId\-Eigenschaft  
 Diese Eigenschaft gibt eine aus Name\-Wert\-Paaren von Eigenschaften bestehende Bedingung zurück, die das Steuerelement während der Wiedergabe eindeutig identifizieren.  Der Entwickler muss diese Eigenschaft für jede abgeleitete Steuerelementklasse überschreiben, um ein <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IQueryElement>\-Objekt zurückzugeben, mit dessen Hilfe das Framework das Steuerelement in der Benutzeroberfläche finden kann.  
  
#### CacheProperties\-Methode  
 Diese Methode wird während des Aufzeichnungsprozesses vom Testframework aufgerufen, um das Element anzuweisen, eine Momentaufnahme wichtiger Eigenschaften zu speichern.  Dadurch sind die Eigenschaften auch dann verfügbar, wenn das eigentliche UI\-Steuerelement nicht mehr auf dem Bildschirm angezeigt wird.  
  
## WorksheetElement\- und WorksheetInformation\-Klassen  
 Die `WorksheetElement`\-Klasse stellt ein Excel\-Arbeitsblatt im Testframework dar und erbt von der `Element`\-Basisklasse.  Drei Eigenschaften werden überschrieben, um spezifische Informationen zum Excel\-Arbeitsblattobjekt bereitzustellen: <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.ClassName%2A>, <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.ControlTypeName%2A> und <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.Name%2A>.  
  
 <xref:System.Runtime.InteropServices.ComVisibleAttribute> wird ebenfalls auf diese Klasse angewendet, um sie für COM sichtbar zu machen.  
  
 Die `WorksheetInformation`\-Klasse stellt Informationen zu einem Excel\-Arbeitsblatt dar.  Sie besitzt nur einen Member, die `SheetName`\-Eigenschaft, was für dieses Beispiel ausreichend ist.  
  
## CellElement\- und CellInformation\-Klassen  
 Die `CellElement`\-Klasse stellt eine Excel\-Zelle dar und erbt von der `Element`\-Basisklasse.  Der einzige überschriebene Member ist die <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A>\-Eigenschaft. Diese Eigenschaft gibt ein <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IQueryElement> zurück, in dem die Zelle mit den `RowIndex`\- und `ColumnIndex`\-Eigenschaften identifiziert wird.  
  
## Utilities\- und ExcelUtilities\-Klassen  
 Die interne `ExcelUtilities`\-Klasse stellt einige Konstantenwerte \(z. B. den Technologienamen\) und eine Methode bereit, die bestimmt, ob das bereitgestellte Fensterhandle ein Excel\-Arbeitsblatt darstellt.  
  
 Die `Utilities`\-Klasse verfügt über Hilfsmethoden, die verschiedene Informationen zur Benutzeroberfläche zurückgeben.  Einige Methoden verwenden direkte Aufrufe externer System\-DLLs wie **USER32.DLL** und **OLEACC.DLL**, um Fensterhandles aus der UI abzurufen**.**  
  
## Siehe auch  
 <xref:System.Runtime.InteropServices.ComVisibleAttribute>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IQueryElement>   
 [Extending Coded UI Tests and Action Recordings to Support Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
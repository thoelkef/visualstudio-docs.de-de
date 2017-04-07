---
title: "Beispiel für Excel-Erweiterung: Element-Klassen | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7c251098-00aa-49cf-9e37-5717c0c6b3f1
caps.latest.revision: 9
ms.author: douge
manager: douge
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 5ab78b6b8eaa8156ed2c8a807b1d8a80e75afa84
ms.openlocfilehash: 396960f31c60318833b8171a4e17595db6ff9fca
ms.lasthandoff: 04/04/2017

---
# <a name="sample-excel-extension-element-classes"></a>Sample Excel Extension: Element Classes
Die Erweiterung verwendet von <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement> abgeleitete Klassen, die das Arbeitsblattsteuerelement und Zellensteuerelement in [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)] darstellen.  
  
 Das Basiselement für diese Erweiterung ist `ExcelElement`. Die `ExcelWorksheetElement`-Klasse und die `ExcelCellElement`-Klasse erben von diesem Element  
  
## <a name="element-and-elementinformation-classes"></a>Element- und ElementInformation-Klasse  
 `Element` ist die Basisklasse für alle Benutzeroberflächenelemente für die Excel-Erweiterung und erbt von der <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement>-Klasse. `ElementInformation` ist die Basisklasse für die Elementinformationsklassen im Beispiel und verfügt nicht über Member.  
  
#### <a name="simple-properties-and-methods"></a>Einfache Eigenschaften und Methoden  
 Diese Member geben einfache Werte zurück, z.B. den Wert der `Name`-Eigenschaft oder den Wert der `ClassName`-Eigenschaft. Der Code ist einfach zu verstehen und zu lesen. Einige Werte werden mit der `Utility`-Klasse zurückgegeben, die weiter unten in diesem Thema erläutert wird. Andere geben `null` zurück, da sie in dieser Beispielerweiterung nicht relevant sind. Zwei Member sind dabei besonders interessant: die <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A>-Eigenschaft und die <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.CacheProperties%2A>-Methode.  
  
#### <a name="queryid-property"></a>QueryId-Eigenschaft  
 Diese Eigenschaft gibt eine Bedingung, die Name-Wert-Paare an, die das Steuerelement während der Wiedergabe eindeutig zu identifizieren. Der Entwickler muss diese Eigenschaft für jede abgeleitete Steuerelementklasse überschreiben, um ein <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IQueryElement>-Objekt zurückzugeben, mit dessen Hilfe das Framework das Steuerelement in der Benutzeroberfläche finden kann.  
  
#### <a name="cacheproperties-method"></a>CacheProperties-Methode  
 Diese Methode wird während des Aufzeichnungsprozesses vom Testframework aufgerufen, um das Element anzuweisen, eine Momentaufnahme wichtiger Eigenschaften zu speichern. Dadurch sind die Eigenschaften auch dann verfügbar, wenn das eigentliche UI-Steuerelement nicht mehr auf dem Bildschirm angezeigt wird.  
  
## <a name="worksheetelement-and-worksheetinformation-classes"></a>WorksheetElement- und WorksheetInformation-Klasse  
 Die `WorksheetElement`-Klasse stellt ein Excel-Arbeitsblatt im Testframework dar und erbt von der `Element`-Basisklasse. Drei Eigenschaften werden überschrieben, um spezifische Informationen zum Excel-Arbeitsblattobjekt bereitzustellen: <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.ClassName%2A>, <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.ControlTypeName%2A> und <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.Name%2A>.  
  
 Das <xref:System.Runtime.InteropServices.ComVisibleAttribute> wird ebenfalls auf diese Klasse angewendet, um sie für COM sichtbar zu machen.  
  
 Die `WorksheetInformation`-Klasse stellt Informationen zu einem Excel-Arbeitsblatt dar. Sie besitzt nur einen Member, die `SheetName`-Eigenschaft, was für dieses Beispiel ausreichend ist.  
  
## <a name="cellelement-and-cellinformation-classes"></a>CellElement- und CellInformation-Klasse  
 Die `CellElement`-Klasse stellt eine `Element`-Zelle dar und erbt von der Element-Basisklasse. Der einzige überschriebene Member ist die <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A> Eigenschaft. Diese Eigenschaft gibt ein <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IQueryElement> zurück, in dem die Zelle mit der `RowIndex`- und der `ColumnIndex`-Eigenschaft identifiziert wird.  
  
## <a name="utilities-and-excelutilities-classes"></a>Utilities- und ExcelUtilities-Klasse  
 Die interne `ExcelUtilities`-Klasse stellt einige Konstantenwerte (z.B. den Technologienamen) und eine Methode bereit, die bestimmt, ob das bereitgestellte Fensterhandle ein Excel-Arbeitsblatt darstellt.  
  
 Die `Utilities`-Klasse verfügt über Hilfsmethoden, die verschiedene Informationen zur Benutzeroberfläche zurückgeben. Einige Methoden verwenden direkte Aufrufe externer System-DLLs wie **USER32.DLL** und **OLEACC.DLL**, um Fensterhandles aus der UI abzurufen**.**  
  
## <a name="see-also"></a>Siehe auch  
 <xref:System.Runtime.InteropServices.ComVisibleAttribute>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IQueryElement>   
 [Extending Coded UI Tests and Action Recordings to Support Microsoft Excel (Erweitern von Tests der programmierten UI und Aktionsaufzeichnungen zur Unterstützung von Microsoft Excel)](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)


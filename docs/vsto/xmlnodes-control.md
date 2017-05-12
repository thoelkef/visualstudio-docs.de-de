---
title: "XMLNodes-Steuerelement"
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
  - "XMLNodes-Steuerelement"
  - "XMLNodes-Steuerelement, Ereignisse"
ms.assetid: 25ba7a21-aabb-4cce-b0d7-57b4add3b485
caps.latest.revision: 36
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 36
---
# XMLNodes-Steuerelement
  **Wichtig** die Informationen, die in diesem Thema bezüglich Microsoft Word erläutert werden, wird ausschließlich für den Nutzen und die Verwendung von Personen und Organisationen, die außerhalb der USA und ihrer Außengebiete befinden, oder die verwenden, oder entwickeln Programme, die auf ausgeführt werden, Microsoft Word\-Produkte dargestellt, die von Microsoft vor Januar 2010 lizenziert wurden, als Microsoft eine Implementierung der bestimmte Funktionen Beziehung zur benutzerdefinierten XML aus Microsoft Word entfernt wurde.  Diese Informationen bezüglich Microsoft Word dürfen nicht von Personen oder Organisationen in den Vereinigten Staaten oder ihren Außengebieten verwendet werden, die Programme verwenden oder entwickeln, die unter Microsoft Word\-Produkten ausgeführt werden, die von Microsoft nach dem 10. Januar 2010 lizenziert wurden. Diese Produkte verhalten sich nicht wie Produkte, die vor diesem Datum lizenziert oder für die Verwendung außerhalb der Vereinigten Staaten erworben und lizenziert wurden.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Das <xref:Microsoft.Office.Tools.Word.XMLNodes>\-Steuerelement ist eine Auflistung zugeordneter XML\-Knotenobjekte, die Ereignisse verfügbar macht.  Das <xref:Microsoft.Office.Tools.Word.XMLNodes>\-Steuerelement wird nur erstellt, wenn ein sich wiederholendes Schemaelement einem Microsoft Office Word\-Dokument zugeordnet wird.  Falls das sich wiederholende Element untergeordnete Elemente enthält, werden diese ebenfalls als <xref:Microsoft.Office.Tools.Word.XMLNodes>\-Steuerelemente erstellt.  
  
 Nachdem Visual Studio die Auflistung von XML\-Knoten erstellt hat, können Sie das Steuerelement sofort zum Programmieren verwenden, ohne das Word\-Objektmodell durchlaufen zu müssen.  Das <xref:Microsoft.Office.Tools.Word.XMLNodes>\-Steuerelement kann nur gelöscht werden, indem die Elementzuordnung aus dem Dokument entfernt wird.  
  
> [!NOTE]  
>  Wenn Sie über die <xref:Microsoft.Office.Tools.Word.XMLNodes.Item%2A>\-Eigenschaft auf ein untergeordnetes Element des <xref:Microsoft.Office.Tools.Word.XMLNodes>\-Steuerelements zugreifen, wird ein <xref:Microsoft.Office.Interop.Word.XMLNode>\-Objekt und kein <xref:Microsoft.Office.Tools.Word.XMLNode>\-Steuerelement zurückgegeben.  Weitere Informationen finden Sie unter [Programmgesteuerte Einschränkungen von Hostelementen und Hoststeuerelementen](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).  
  
## Binden von Daten an das Steuerelement  
 Ein <xref:Microsoft.Office.Tools.Word.XMLNodes>\-Steuerelement unterstützt keine Datenbindung.  Dies verhält sich deshalb so, weil das <xref:Microsoft.Office.Tools.Word.XMLNodes>\-Steuerelement keine komplexe Datenbindungsfähigkeiten besitzt und durch einfache Datenbindungen sich wiederholende Daten nicht dargestellt werden können.  
  
## Formatierung  
 Alle Formatierungen für Text innerhalb eines Dokuments können auch auf das <xref:Microsoft.Office.Tools.Word.XMLNodes>\-Steuerelement angewendet werden.  
  
## Ereignisse  
 Die folgenden Ereignisse sind für das <xref:Microsoft.Office.Tools.Word.XMLNodes>\-Steuerelement verfügbar:  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.AfterInsert>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.BeforeDelete>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextLeave>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.Deselect>  
  
-   <xref:System.ComponentModel.IComponent.Disposed>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.Select>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.ValidationError>  
  
## Vergleichen von Ereignissen  
 Sie können ein Ereignis erfassen, wenn der Benutzer den Cursor im Kontext eines bestimmten <xref:Microsoft.Office.Tools.Word.XMLNodes>\-Steuerelements bewegt.  Beispielsweise haben Sie wie folgend ein <xref:Microsoft.Office.Tools.Word.XMLNodes>\-Steuerelement mit dem Namen `Customer` mit einem untergeordneten <xref:Microsoft.Office.Tools.Word.XMLNodes>\-Steuerelement mit dem Namen `Company`, wobei `Company` zwei untergeordnete <xref:Microsoft.Office.Tools.Word.XMLNodes>\-Steuerelemente mit dem Namen `CompanyName` und `CompanyRegion` hat:  
  
```  
<Customer>  
    <Company>  
        <CompanyName>  
        <CompanyRegion>  
```  
  
 Wenn Sie im Aktionsbereich ein Steuerelement anzeigen möchten, sobald der Cursor auf den `Company`\-Knoten bewegt wird, sollte es keine Rolle spielen, ob der Cursor über `CompanyName` oder `CompanyRegion` platziert wird, da beide im Kontext von `Company` liegen.  In diesem Fall können Sie den Code in das <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter>\-Ereignis von `Company` schreiben.  
  
 Sobald sich der Cursor in ein <xref:Microsoft.Office.Tools.Word.XMLNodes>\-Steuerelement hineinbewegt, werden in den meisten Fällen sowohl das <xref:Microsoft.Office.Tools.Word.XMLNodes.Select>\-Ereignis als auch das <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter>\-Ereignis ausgelöst.  In der folgenden Tabelle werden Unterschiede zwischen diesen Ereignissen aufgeführt.  
  
|Select\-Ereignis|ContextEnter\-Ereignis|  
|----------------------|----------------------------|  
|Tritt auf, wenn der Cursor auf einem der Knoten der <xref:Microsoft.Office.Tools.Word.XMLNodes>\-Auflistung platziert wird.|Tritt auf, wenn der Cursor außerhalb eines Bereichs des Knotenkontexts, in einem der Knoten oder der nachfolgenden Knoten der <xref:Microsoft.Office.Tools.Word.XMLNodes>\-Auflistung platziert wird.  Mit anderen Worten: Es wird nur ausgelöst, wenn sich der Kontext ändert, und kann für mehrere geschachtelte <xref:Microsoft.Office.Tools.Word.XMLNodes>\-Steuerelemente ausgelöst werden.|  
  
 Wenn Sie beispielsweise den Cursor außerhalb von `Customer` in `CompanyName` hineinbewegen, werden die <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter>\-Ereignisse für `Customer`, `Company` und `CompanyName` ausgelöst.  Wenn Sie anschließend den Cursors von `CompanyName` zu `CompanyRegion` bewegen, wird das <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter>\-Ereignis nur für `CompanyRegion` ausgelöst, da der Kontext für `Company` und `Customer` gleich ist.  Es können mehrere `Company`\-Knoten im Dokument vorhanden sein.  Wenn Sie den Cursor vom `CompanyName`\-Knoten einer `Company` zum `CompanyName`\-Knoten einer anderen `Company` bewegen, ist der Kontext gleich, sodass nur das <xref:Microsoft.Office.Tools.Word.XMLNodes.Select>\-Ereignis ausgelöst wird.  
  
 Die gleichen Unterschiede bestehen zwischen dem <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextLeave>\-Ereignis und dem <xref:Microsoft.Office.Tools.Word.XMLNodes.Deselect>\-Ereignis.  
  
## Siehe auch  
 [Übersicht über Hostelemente und Hoststeuerelemente](../vsto/host-items-and-host-controls-overview.md)   
 [Automatisieren von Word mithilfe von erweiterten Objekten](../vsto/automating-word-by-using-extended-objects.md)   
 [XMLNode-Steuerelement](../vsto/xmlnode-control.md)   
 [Gewusst wie: Hinzufügen von XMLNodes-Steuerelementen zu Word-Dokumenten](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)   
 [Gewusst wie: Zuordnen von Schemas zu Word-Dokumenten in Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)   
 [Programmgesteuerte Einschränkungen von Hostelementen und Hoststeuerelementen](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  
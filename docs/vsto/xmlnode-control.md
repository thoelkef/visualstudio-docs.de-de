---
title: "XMLNode-Steuerelement | Microsoft Docs"
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
  - "XMLNode-Steuerelement"
ms.assetid: 4f5c7f17-62aa-483c-ab0d-b04614ab065d
caps.latest.revision: 39
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 38
---
# XMLNode-Steuerelement
  **Wichtig** die Informationen, die in diesem Thema bezüglich Microsoft Word erläutert werden, wird ausschließlich für den Nutzen und die Verwendung von Personen und Organisationen, die außerhalb der USA und ihrer Außengebiete befinden, oder die verwenden, oder entwickeln Programme, die auf ausgeführt werden, Microsoft Word\-Produkte dargestellt, die von Microsoft vor Januar 2010 lizenziert wurden, als Microsoft eine Implementierung der bestimmte Funktionen Beziehung zur benutzerdefinierten XML aus Microsoft Word entfernt wurde.  Diese Informationen bezüglich Microsoft Word dürfen nicht von Personen oder Organisationen in den Vereinigten Staaten oder ihren Außengebieten verwendet werden, die Programme verwenden oder entwickeln, die unter Microsoft Word\-Produkten ausgeführt werden, die von Microsoft nach dem 10. Januar 2010 lizenziert wurden. Diese Produkte verhalten sich nicht wie Produkte, die vor diesem Datum lizenziert oder für die Verwendung außerhalb der Vereinigten Staaten erworben und lizenziert wurden.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Das <xref:Microsoft.Office.Tools.Word.XMLNode>\-Steuerelement ist ein zugeordnetes XML\-Knotenobjekt, das Ereignisse verfügbar macht und an Daten gebunden werden kann.  Das <xref:Microsoft.Office.Tools.Word.XMLNode>\-Steuerelement wird nur erstellt, wenn ein sich nicht wiederholendes Schemaelement einem Microsoft Office Word\-Dokument zugeordnet wird.  Nachdem Visual Studio den XML\-Knoten erstellt hat, können Sie beim Programmieren direkt darauf zugreifen, ohne das Word\-Objektmodell durchlaufen zu müssen.  
  
 Das <xref:Microsoft.Office.Tools.Word.XMLNode>\-Steuerelement kann nur gelöscht werden, indem die Elementzuordnung in Word entfernt wird.  
  
## Binden von Daten an das Steuerelement  
 Ein <xref:Microsoft.Office.Tools.Word.XMLNode>\-Steuerelement unterstützt die einfache Datenbindung.  Der XML\-Knoten sollte mit der <xref:System.Windows.Forms.IBindableComponent.DataBindings%2A>\-Eigenschaft an eine Datenquelle gebunden werden.  Wenn die Daten im gebundenen Dataset aktualisiert werden, werden diese Änderungen vom <xref:Microsoft.Office.Tools.Word.XMLNode>\-Steuerelement nachvollzogen.  
  
## Formatierung  
 Die Formatierung für das <xref:Microsoft.Office.Interop.Word.XMLNode>\-Objekt kann auch auf das <xref:Microsoft.Office.Tools.Word.XMLNode>\-Steuerelement angewendet werden.  Das schließt Schriftarten, Unterstreichungsstile und Zeichenformatvorlagen ein.  
  
## Ereignisse  
 Die folgenden Ereignisse sind für das <xref:Microsoft.Office.Tools.Word.XMLNode>\-Steuerelement verfügbar:  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.AfterInsert>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.BeforeDelete>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.BindingContextChanged>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.ContextLeave>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.Deselect>  
  
-   <xref:System.ComponentModel.IComponent.Disposed>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.Select>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.ValidationError>  
  
## Vergleichen von Ereignissen  
 Sie können ein Ereignis erfassen, wenn der Benutzer den Cursor im Kontext eines bestimmten <xref:Microsoft.Office.Tools.Word.XMLNode>\-Steuerelements bewegt.  Gehen wir im folgenden Beispiel davon aus, dass Sie ein <xref:Microsoft.Office.Tools.Word.XMLNode>\-Steuerelement mit dem Namen `Customer` mit einem untergeordneten <xref:Microsoft.Office.Tools.Word.XMLNode>\-Steuerelement mit dem Namen `Company` haben, wobei `Company` zwei untergeordnete <xref:Microsoft.Office.Tools.Word.XMLNode>\-Steuerelemente mit dem Namen `CompanyName` und `CompanyRegion` hat:  
  
```  
<Customer>  
    <Company>  
        <CompanyName>  
        <CompanyRegion>  
```  
  
 Wenn Sie im Aktionsbereich ein Steuerelement anzeigen möchten, sobald der Cursor auf den `Company`\-Knoten bewegt wird, sollte es keine Rolle spielen, ob der Cursor über `CompanyName` oder `CompanyRegion` platziert wird, da beide im Kontext von `Company` liegen.  In diesem Fall können Sie den Code in das <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter>\-Ereignis von `Company` schreiben.  
  
 Sobald sich der Cursor in ein <xref:Microsoft.Office.Tools.Word.XMLNode>\-Steuerelement hineinbewegt, werden in den meisten Fällen sowohl das <xref:Microsoft.Office.Tools.Word.XMLNode.Select>\-Ereignis und als auch das <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter>\-Ereignis ausgelöst.  In der folgenden Tabelle werden die Unterschiede zwischen diesen Ereignissen aufgeführt.  
  
|Select\-Ereignis|ContextEnter\-Ereignis|  
|----------------------|----------------------------|  
|Wird ausgelöst, wenn der Cursor in einen <xref:Microsoft.Office.Tools.Word.XMLNode> platziert wird.|Wird ausgelöst, wenn der Cursor ausgehend von einem Bereich außerhalb des Knotenkontexts in einen <xref:Microsoft.Office.Tools.Word.XMLNode> oder von ihm abgeleiteten Knoten platziert wird.  In anderen Worten: Das Ereignis wird nur ausgelöst, wenn sich der Kontext ändert.|  
  
 Wenn Sie beispielsweise den Cursor außerhalb von `Customer` in `CompanyName` hineinbewegen, wird das <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter>\-Ereignis für `Customer`, `Company` und `CompanyName` ausgelöst.  Beim anschließenden Bewegen des Cursors von `CompanyName` nach `CompanyRegion`, wird das <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter>\-Ereignis nur für `CompanyRegion` ausgelöst, da sich der Cursor immer noch im Kontext von `Company` und `Customer` befindet.  
  
 Die gleichen Unterschiede bestehen zwischen dem <xref:Microsoft.Office.Tools.Word.XMLNode.ContextLeave>\-Ereignis und dem <xref:Microsoft.Office.Tools.Word.XMLNode.Deselect>\-Ereignis.  
  
## Siehe auch  
 [Übersicht über Hostelemente und Hoststeuerelemente](../vsto/host-items-and-host-controls-overview.md)   
 [Automatisieren von Word mithilfe von erweiterten Objekten](../vsto/automating-word-by-using-extended-objects.md)   
 [XMLNodes-Steuerelement](../vsto/xmlnodes-control.md)   
 [Gewusst wie: Hinzufügen von XMLNode-Steuerelementen zu Word-Dokumenten](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)   
 [Gewusst wie: Zuordnen von Schemas zu Word-Dokumenten in Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)   
 [Programmgesteuerte Einschränkungen von Hostelementen und Hoststeuerelementen](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  
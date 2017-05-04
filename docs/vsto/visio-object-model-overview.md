---
title: "&#220;bersicht &#252;ber das Visio-Objektmodell | Microsoft Docs"
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
  - "Visio [Office-Entwicklung in Visual Studio], Objektmodell"
  - "Objektmodelle [Office-Entwicklung in Visual Studio], Office"
  - "Objektmodelle [Office-Entwicklung in Visual Studio], Visio"
  - "Objekte [Office-Entwicklung in Visual Studio], Office-Objektmodelle"
  - "Office-Objektmodelle"
  - "Visio-Objektmodelle"
ms.assetid: 11f0ae0c-feff-46c7-9885-b968391718f7
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# &#220;bersicht &#252;ber das Visio-Objektmodell
  Zur Entwicklung von Office\-Projektmappen für Microsoft Office Visio können Sie mit dem Visio\-Objektmodell interagieren. Dieses Objektmodell besteht aus Klassen und Schnittstellen, die in der primären Interopassembly für Visio bereitgestellt und im Microsoft.Office.Interop.Visio\-Namespace definiert werden.  
  
 Dieses Thema enthält eine kurze Übersicht über das Visio\-Objektmodell. Informationen zur Verwendung des Visio\-Objektmodells für bestimmte Aufgaben in Office\-Projekten finden Sie unter den folgenden Themen:  
  
-   [Arbeiten mit Visio-Dokumenten](../vsto/working-with-visio-documents.md)  
  
-   [Arbeiten mit Visio-Shapes](../vsto/working-with-visio-shapes.md)  
  
## Informationen zum Visio\-Objektmodell  
 Visio stellt zahlreiche Objekte bereit, mit denen Sie interagieren können. Diese Objekte werden in einer Hierarchie angeordnet, die eng an die Benutzeroberfläche angelehnt ist. Oben in der Hierarchie befindet sich das [Microsoft.Office.Interop.Visio.Application](HV10077088)\-Objekt. Dieses Objekt stellt die aktuelle Instanz von Visio dar. Das Microsoft.Office.Interop.Visio.Application\-Objekt enthält die Objekte Microsoft.Office.Interop.Visio.Document und Microsoft.Office.Interop.Visio.Page  sowie die Auflistungen Microsoft.Office.Interop.Visio.Documents und Microsoft.Office.Interop.Visio.Pages. Jedes dieser Objekte bzw. jede dieser Auflistungen verfügt über zahlreiche Methoden und Eigenschaften, auf die Sie zwecks Bearbeitung und Interaktion zugreifen können.  
  
 Weitere Informationen finden Sie in der VBA\-Referenzdokumentation für die Objekte [Microsoft.Office.Interop.Visio.Application](HV10077088), [Microsoft.Office.Interop.Visio.Document](HV10077095) und [Microsoft.Office.Interop.Visio.Page](HV10077063) sowie für die Auflistungen [Microsoft.Office.Interop.Visio.Documents](HV10077062) und [Microsoft.Office.Interop.Visio.Pages](HV10077074).  
  
 In den folgenden Abschnitten werden die Objekte der obersten Ebene und ihre Interaktion miteinander kurz beschrieben. Dazu gehören die folgenden Objekte:  
  
-   Application\-Objekt  
  
-   Document\-Objekt  
  
-   Page\-Objekt  
  
### Application\-Objekt  
 Das Microsoft.Office.Interop.Visio.Application\-Objekt stellt die Visio\-Anwendung dar. Es ist allen anderen Objekten übergeordnet. Seine Elemente gelten normalerweise für Visio als Ganzes. Sie können die Eigenschaften und Methoden des Microsoft.Office.Interop.Visio.Application\-Objekts und des Microsoft.Office.Interop.Visio.ApplicationSettings\-Objekts zur Steuerung der Visio\-Umgebung verwenden.  
  
 In VSTO\-Add\-In\-Projekten können Sie mithilfe des `Application`\-Felds der `ThisAddIn`\-Klasse auf das Microsoft.Office.Interop.Visio.Application\-Objekt zugreifen. Weitere Informationen finden Sie unter [Programmieren von VSTO-Add-Ins](../vsto/programming-vsto-add-ins.md).  
  
### Document\-Objekt  
 Das Microsoft.Office.Interop.Visio.Document\-Objekt ist von entscheidender Bedeutung für die Visio\-Programmierung. Es stellt eine Zeichnungs\-, Schablonen\- oder Vorlagendatei dar. Wenn Sie ein Visio\-Dokument öffnen oder ein neues Dokument erstellen, legen Sie ein neues Microsoft.Office.Interop.Visio.Document\-Objekt an, das der Microsoft.Office.Interop.Visio.Documents\-Auflistung des Microsoft.Office.Interop.Visio.Application\-Objekts hinzugefügt wird.  
  
 Das Dokument, das den Fokus besitzt, wird als das aktive Dokument bezeichnet. Es wird durch die Microsoft.Office.Interop.Visio.Application.ActiveDocument\-Eigenschaft des Microsoft.Office.Interop.Visio.Application\-Objekts dargestellt.  
  
### Page\-Objekt  
 Das Microsoft.Office.Interop.Visio.Page\-Objekt stellt den Zeichnungsbereich einer Vordergrund\- oder Hintergrundseite dar. Mithilfe der Microsoft.Office.Interop.Visio.Page.Background\-Eigenschaft können Sie feststellen, ob es sich bei der Seite um eine Vorder\- oder Hintergrundseite handelt.  
  
 Zum Erstellen von Shapes können Sie Methoden wie die Microsoft.Office.Interop.Visio.Page.DrawSpline\-Methode und die Microsoft.Office.Interop.Visio.Page.DrawOval\-Methode verwenden. Darüber hinaus können Sie Masters aus Schablonen abrufen und die Shapes mithilfe der Microsoft.Office.Interop.Visio.Page.Drop\-Methode oder Microsoft.Office.Interop.Visio.Page.DropMany\-Methode auf einer Seite platzieren.  
  
## Verwenden der Dokumentation zum Visio\-Objektmodell  
 Ausführliche Informationen zum Visio\-Objektmodell finden Sie in der VBA\-Objektmodellreferenz für Visio. Die VBA\-Objektmodellreferenz dokumentiert das Visio\-Objektmodell, das für VBA \(Visual Basic for Applications\) verfügbar gemacht wird. Weitere Informationen finden Sie unter [Visio 2010\-Objektmodellreferenz](http://go.microsoft.com/fwlink/?LinkId=199775).  
  
 Alle Objekte und Member in der VBA\-Objektmodellreferenz entsprechen Typen und Membern in der primären Interopassembly \(PIA\) für Visio. Das Document\-Objekt in der VBA\-Objektmodellreferenz entspricht z. B. dem Microsoft.Office.Interop.Visio.Document\-Typ in der Visio\-PIA. Obwohl die VBA\-Objektmodellreferenz Codebeispiele für die meisten Eigenschaften, Methoden und Ereignisse enthält, müssen Sie den VBA\-Code in dieser Referenz in Visual Basic oder Visual C\# übersetzen, wenn Sie ihn in einem mit Visual Studio erstellten Visio VSTO\-Add\-In\-Projekt verwenden möchten.  
  
> [!NOTE]  
>  Derzeit ist keine Referenzdokumentation für die primäre Interopassembly für Visio verfügbar.  
  
 Verwandte Codebeispiele und weitere Tools zum Erstellen von Visio\-Projektmappen finden Sie unter [Visio 2010 Software Development Kit](http://go.microsoft.com/fwlink/?LinkId=196501).  
  
### Zusätzliche Typen in primären Interopassemblys  
 Primäre Interopassemblys können Typen enthalten, die aufgrund von Unterschieden bei der Implementierung nicht für VBA sichtbar sind. VBA bietet eine Ansicht des Visio\-Objektmodells, das nur die Objekte und Member enthält, die Sie direkt verwenden können. Die primären Interopassemblys machen das gleiche Objektmodell verfügbar, enthalten zusätzlich aber weitere Schnittstellen, Klassen und Member, die Objekte im COM\-Objektmodell in verwalteten Code übersetzen. Diese zusätzlichen Elemente sollten nicht direkt im Code verwendet werden.  
  
 Weitere Informationen finden Sie in der [Übersicht über Klassen und Schnittstellen in den primären Interopassemblys für Office](http://go.microsoft.com/fwlink/?LinkId=189592) und [Primäre Interopassemblys in Office](../vsto/office-primary-interop-assemblies.md).  
  
## Siehe auch  
 [Visio-Projektmappen](../vsto/visio-solutions.md)   
 [Arbeiten mit Visio-Dokumenten](../vsto/working-with-visio-documents.md)   
 [Arbeiten mit Visio-Shapes](../vsto/working-with-visio-shapes.md)  
  
  
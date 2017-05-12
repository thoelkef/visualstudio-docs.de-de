---
title: "&#220;bersicht &#252;ber benutzerdefinierte XML-Abschnitte"
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
  - "Benutzerdefinierte XML-Teile [Office-Entwicklung in Visual Studio]"
  - "Benutzerdefinierte XML-Teile [Office-Entwicklung in Visual Studio], Informationen über"
  - "Daten [Office-Entwicklung in Visual Studio], Benutzerdefinierte XML-Teile"
  - "Dokumente [Office-Entwicklung in Visual Studio], Benutzerdefinierte XML-Teile"
  - "Einbetten von XML-Daten in Dokumente [Office-Entwicklung in Visual Studio]"
  - "Excel [Office-Entwicklung in Visual Studio], Benutzerdefinierte XML-Teile"
  - "Office-Dokumente [Office-Entwicklung in Visual Studio], Benutzerdefinierte XML-Teile"
  - "Office Open XML-Formate [Office-Entwicklung in Visual Studio]"
  - "Word [Office-Entwicklung in Visual Studio], Benutzerdefinierte XML-Teile"
  - "XML [Office-Entwicklung in Visual Studio], Benutzerdefinierte XML-Teile"
  - "XML-Dateiformate [Office-Entwicklung in Visual Studio]"
  - "XML-Teile [Office-Entwicklung in Visual Studio]"
ms.assetid: a14119dc-59e8-4614-94f1-08c92bdf7300
caps.latest.revision: 33
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 32
---
# &#220;bersicht &#252;ber benutzerdefinierte XML-Abschnitte
  Sie können XML\-Daten für einige Microsoft Office\-Anwendungen in Dokumente einbetten.  Wenn Sie XML\-Daten in ein Dokument einbetten, werden die Daten als ein *benutzerdefiniertes XML\-Element* bezeichnet.  
  
 Sie können benutzerdefinierte XML\-Elemente in einem Dokument mithilfe eines VSTO\-Add\-Ins oder einer Projektmappe auf Dokumentebene in Visual Studio erstellen und ändern.  Sie müssen nicht die Microsoft Office\-Anwendung starten, um benutzerdefinierte XML\-Elemente zu erstellen und zu ändern.  
  
 **Betrifft:** Die Informationen in diesem Thema betreffen Projekte auf Dokumentebene und VSTO\-Add\-In\-Projekte für Excel, PowerPoint und Word.  Weitere Informationen finden Sie unter [Verfügbare Funktionen nach Office-Anwendung und Projekttyp](../vsto/features-available-by-office-application-and-project-type.md).  
  
> [!NOTE]  
>  Visual Studio ermöglicht es Ihnen außerdem, Datenobjekte in Anpassungen auf Dokumentebene zwischenzuspeichern.  Dieses Feature unterscheidet sich von benutzerdefinierten XML\-Elementen, obwohl es einige Ähnlichkeiten gibt.  Weitere Informationen finden Sie unter [Zwischengespeicherte Daten in Anpassungen auf Dokumentebene](../vsto/cached-data-in-document-level-customizations.md).  
  
## Informationen zum Verständnis von benutzerdefinierten XML\-Elementen  
 Benutzerdefinierte XML\-Elemente wurden in Microsoft Office System 2007 zusammen mit den Open XML\-Formaten eingeführt.  Diese Formate umfassen neue XML\-basierte Dateiformate für Excel, PowerPoint und Word \(z. B. XLSX, PPTX und DOCX\).  Dokumente in diesen Formaten bestehen aus XML\-Dateien \(auch als *XML\-Elemente*\) bezeichnet, die in Ordnern in einem ZIP\-Archiv organisiert sind.  Die meisten der XML\-Elemente sind integrierte Elemente, mit deren Hilfe die Struktur und der Status des Dokuments definiert werden.  Allerdings können Dokumente auch benutzerdefinierte XML\-Elemente enthalten, die Sie verwenden können, um beliebige XML\-Daten in den Dokumenten zu speichern.  
  
 Die XML\-Dateiformate ermöglichen Anwendungen das Arbeiten mit Dokumenten in einer Weise , die mit den älteren binären Dateiformaten \(wie XLS, PPT und DOC\) nicht möglich ist.  Jede Anwendung, die ZIP\-Archive lesen kann, kann den Inhalt der Dokumente untersuchen und ändern, auch wenn Microsoft Office nicht installiert ist.  
  
 Weitere Informationen zur Struktur von Open XML und benutzerdefinierten XML\-Elementen finden Sie in den folgenden Artikeln:  
  
-   [Einführung in die Microsoft Office \(2007\) Open XML\-Dateiformate](http://msdn.microsoft.com/de-de/96018532-f62c-4da7-bbff-16b96a483fbf)  
  
-   [Gewusst wie: Bearbeiten von Dokumenten im Open XML\-Format](http://msdn.microsoft.com/de-de/c989d4e2-053d-4e1f-83be-257c608b343f)  
  
-   [Exemplarische Vorgehensweise: XML\-Format von Word 2007](http://msdn.microsoft.com/de-de/fc1afcb2-27fb-4608-9f29-11b7bd23ea4a)  
  
-   [Erstellen von Word 2007\-Dokumenten mit Open XML\-Formaten](http://msdn.microsoft.com/de-de/59a46f4e-5a5a-4dac-86e5-7dfd43330766)  
  
> [!NOTE]  
>  Excel, Word und PowerPoint ermöglichen auch die Verwendung benutzerdefinierter XML\-Elemente in Dokumenten, die in den binären Dateiformaten gespeichert werden.  Wenn ein Dokument in einem binären Format gespeichert wird, können Sie benutzerdefinierte XML\-Elemente jedoch nicht hinzufügen oder ändern, ohne die jeweilige Microsoft Office\-Anwendung zu starten.  
  
## Erstellen und Ändern von benutzerdefinierten XML\-Elementen  
 Sie können benutzerdefinierte XML\-Elemente erstellen oder ändern, wenn das Dokument in der Office\-Anwendung geöffnet ist oder wenn das Dokument geschlossen ist – selbst dann, wenn Microsoft Office nicht installiert ist.  
  
### Ändern von XML\-Elementen, während die Office\-Anwendung ausgeführt wird  
 Sie können mit benutzerdefinierten XML\-Elementen arbeiten, indem Sie eine Anpassung auf Dokumentebene oder ein VSTO\-Add\-In verwenden.  Wenn Sie eine Anpassung auf Dokumentebene verwenden, arbeiten Sie in der Regel mit benutzerdefinierten XML\-Elementen, die sich im angepassten Dokument befinden.  Wenn Sie ein VSTO\-Add\-In verwenden, können Sie benutzerdefinierte XML\-Elemente in Dokumenten erstellen oder ändern, die in der Anwendung geöffnet sind.  
  
 Wenn Sie ein benutzerdefiniertes XML\-Element mit Visual Studio erstellen möchten, fügen Sie der Auflistung  <xref:Microsoft.Office.Core.CustomXMLParts> im Dokument ein neues <xref:Microsoft.Office.Core.CustomXMLPart>\-Objekt hinzu.  Weitere Informationen finden Sie unter den folgenden Themen:  
  
-   [Gewusst wie: Hinzufügen von benutzerdefinierten XML-Abschnitten zu Anpassungen auf Dokumentebene](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md)  
  
-   [Gewusst wie: Hinzufügen von benutzerdefinierten XML-Elementen zu Dokumenten mithilfe von VSTO-Add-Ins](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)  
  
### Ändern von XML\-Elementen, ohne die Office\-Anwendung zu starten  
 Sie können ein benutzerdefiniertes XML\-Element hinzufügen oder ändern, ohne Excel, PowerPoint oder Word zu starten.  Dies ist hilfreich, wenn Sie mit XML\-Daten in einem Dokument auf einem Computer arbeiten möchten, auf dem keine Microsoft Office\-Anwendungen installiert sind \(z. B. auf einem Server\).  
  
 Wenn Sie ein benutzerdefiniertes XML\-Element hinzufügen möchten, ohne Microsoft Office zu starten, verwenden Sie Klassen im Open XML SDK.  Diese Klassen bieten Zugriff auf Open XML\-Inhalt, der für Office\-Dokumente spezifisch ist.  Wenn Sie z. B. einer Excel\-Arbeitsmappe ein benutzerdefiniertes XML\-Element hinzufügen möchten, verwenden Sie die Methode [AddNewPart \< T \>](http://msdn.microsoft.com/de-de/47c348c0-77ab-a504-5097-bcd6a213921a) eines [WorkbookPart](http://msdn.microsoft.com/de-de/d011e6f4-77dd-d02d-66ef-dc4a9e7b26f2)\-Objekts.  Weitere Informationen finden Sie unter [Open XML SDK 2.0](http://msdn.microsoft.com/de-de/f6a9ae68-7989-4208-97f5-3c945137a0ab).  
  
## Binden von benutzerdefinierten XML\-Elementen an Word\-Inhaltssteuerelemente  
 Sie können Inhaltssteuerelemente in einer Word\-Projektmappe an Elemente in einem benutzerdefinierten XML\-Element binden.  Wenn ein Inhaltssteuerelement an ein benutzerdefiniertes XML\-Element gebunden ist, werden die Daten im benutzerdefinierten XML\-Element in der Benutzeroberfläche \(User Interface, UI\) des Inhaltssteuerelements angezeigt.  Wenn ein Benutzer Text im Steuerelement bearbeitet, werden die entsprechenden XML\-Elemente automatisch aktualisiert.  Wenn Elementwerte in den benutzerdefinierten XML\-Elementen geändert werden, zeigen die Inhaltssteuerelemente, die an die XML\-Elemente gebunden sind, auf ähnliche Weise die neuen Daten an.  Weitere Informationen finden Sie unter [Inhaltssteuerelemente](../vsto/content-controls.md).  
  
## Siehe auch  
 [XML-Schemas und -Daten in Anpassungen auf Dokumentebene](../vsto/xml-schemas-and-data-in-document-level-customizations.md)   
 [Gewusst wie: Hinzufügen von benutzerdefinierten XML-Abschnitten zu Anpassungen auf Dokumentebene](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md)   
 [Gewusst wie: Hinzufügen von benutzerdefinierten XML-Elementen zu Dokumenten mithilfe von VSTO-Add-Ins](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)   
 [Inhaltssteuerelemente](../vsto/content-controls.md)   
 [Exemplarische Vorgehensweise: Binden von Inhaltssteuerelementen an benutzerdefinierte XML-Abschnitte](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md)  
  
  
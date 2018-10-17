---
title: Übersicht über benutzerdefinierte XML-Teile
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom XML parts [Office development in Visual Studio], about
- Office Open XML Formats [Office development in Visual Studio]
- custom XML parts [Office development in Visual Studio]
- embedding XML data in documents [Office development in Visual Studio]
- XML parts [Office development in Visual Studio]
- XML file formats [Office development in Visual Studio]
- data [Office development in Visual Studio], custom XML parts
- Office documents [Office development in Visual Studio, custom XML parts
- XML [Office development in Visual Studio], custom XML parts
- Word [Office development in Visual Studio], custom XML parts
- Excel [Office development in Visual Studio], custom XML parts
- documents [Office development in Visual Studio], custom XML parts
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: b31ce44c458f7f376d98fac83670595b8a163d65
ms.sourcegitcommit: 48bc8492973e93612e5afaba3b47d0f98aecf97c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2018
ms.locfileid: "49325002"
---
# <a name="custom-xml-parts-overview"></a>Übersicht über benutzerdefinierte XML-Teile
  Sie können XML-Daten für einige Microsoft Office-Anwendungen in Dokumente einbetten. Wenn Sie XML-Daten in ein Dokument einbetten, werden die Daten als eine *benutzerdefinierten XML-Abschnitt*.  
  
 Sie können benutzerdefinierte XML-Elemente in einem Dokument mithilfe eines VSTO-Add-Ins oder einer Projektmappe auf Dokumentebene in Visual Studio erstellen und ändern. Sie müssen nicht die Microsoft Office-Anwendung starten, um benutzerdefinierte XML-Elemente zu erstellen und zu ändern.  
  
 **Gilt für:** die Informationen in diesem Thema bezieht sich auf die Projekte auf Dokumentebene und VSTO-Add-in-Projekte für Excel, PowerPoint und Word. Weitere Informationen finden Sie unter [verfügbare Funktionen nach Office-Anwendung und Projekt Typ](../vsto/features-available-by-office-application-and-project-type.md).  
  
> [!NOTE]  
>  Visual Studio ermöglicht es Ihnen außerdem, Datenobjekte in Anpassungen auf Dokumentebene zwischenzuspeichern. Diese Funktion unterscheidet sich von benutzerdefinierten XML-Elementen, obwohl es einige Ähnlichkeiten gibt. Weitere Informationen finden Sie unter [zwischengespeicherten Daten in Anpassungen auf Dokumentebene](../vsto/cached-data-in-document-level-customizations.md).  
  
## <a name="understand-custom-xml-parts"></a>Verstehen Sie benutzerdefinierte XML-Elemente  
 Benutzerdefinierte XML-Elemente wurden in Microsoft Office System 2007 zusammen mit den Open XML-Formaten eingeführt. Diese Formate umfassen neue XML-basierte Dateiformate für Excel, PowerPoint und Word (z. B. *XLSX*, *PPTX*, und *".docx"*). Dokumente in diesen Formaten bestehen aus XML-Dateien (auch als *XML-Elementen*), die in einem ZIP-Archiv in Ordnern organisiert sind. Die meisten der XML-Elemente sind integrierte Elemente, mit deren Hilfe die Struktur und der Status des Dokuments definiert werden. Allerdings können Dokumente auch benutzerdefinierte XML-Elemente enthalten, die Sie verwenden können, um beliebige XML-Daten in den Dokumenten zu speichern.  
  
 Die XML-Dateiformate ermöglichen Anwendungen, die mit Dokumenten in einer Weise arbeiten, die nicht mit den älteren binären Dateiformaten möglich sind (z. B. *xls*, *PPT*, und *.doc*). Jede Anwendung, die ZIP-Archive lesen kann, kann den Inhalt der Dokumente untersuchen und ändern, auch wenn Microsoft Office nicht installiert ist.  
  
 Weitere Informationen zur Struktur von Open XML und benutzerdefinierten XML-Elementen finden Sie in den folgenden Artikeln:  
  
-   [Einführung in die Office (2007) Open XML-Dateiformate](http://msdn.microsoft.com/96018532-f62c-4da7-bbff-16b96a483fbf)  
  
-   [Gewusst wie: Bearbeiten von Dokumenten im Open XML-Formate](http://msdn.microsoft.com/c989d4e2-053d-4e1f-83be-257c608b343f)  
  
-   [Exemplarische Vorgehensweise: Word 2007-XML-format](http://msdn.microsoft.com/fc1afcb2-27fb-4608-9f29-11b7bd23ea4a)  
  
-   [Erstellen von Dokumenten in Word 2007 Open XML-Formaten](http://msdn.microsoft.com/59a46f4e-5a5a-4dac-86e5-7dfd43330766)  
  
> [!NOTE]  
>  Excel, Word und PowerPoint ermöglichen auch die Verwendung benutzerdefinierter XML-Elemente in Dokumenten, die in den binären Dateiformaten gespeichert werden. Wenn ein Dokument in einem binären Format gespeichert wird, können Sie benutzerdefinierte XML-Elemente jedoch nicht hinzufügen oder ändern, ohne die jeweilige Microsoft Office-Anwendung zu starten.  
  
## <a name="create-and-modify-custom-xml-parts"></a>Erstellen und Ändern von benutzerdefinierten XML-Elementen  
 Sie können benutzerdefinierte XML-Elemente erstellen oder ändern, wenn das Dokument in der Office-Anwendung geöffnet ist oder wenn das Dokument geschlossen ist – selbst dann, wenn Microsoft Office nicht installiert ist.  
  
### <a name="modify-xml-parts-while-the-office-application-is-running"></a>XML-Elemente zu ändern, während die Office-Anwendung ausgeführt wird  
 Sie können mit benutzerdefinierten XML-Elementen arbeiten, mit einer Anpassung auf Dokumentebene oder ein VSTO-Add-in. Wenn Sie eine Anpassung auf Dokumentebene verwenden, arbeiten Sie in der Regel mit benutzerdefinierten XML-Elementen, die sich im angepassten Dokument befinden. Wenn Sie ein VSTO-Add-in verwenden, können Sie erstellen oder Ändern von benutzerdefinierten XML-Elemente in Dokumenten, die in der Anwendung geöffnet ist.  
  
 Wenn Sie ein benutzerdefiniertes XML-Element mit Visual Studio erstellen möchten, fügen Sie der Auflistung  <xref:Microsoft.Office.Core.CustomXMLParts> im Dokument ein neues <xref:Microsoft.Office.Core.CustomXMLPart>-Objekt hinzu. Weitere Informationen finden Sie unter den folgenden Themen:  
  
-   [Gewusst wie: Hinzufügen von benutzerdefinierten XML-Abschnitten zu Anpassungen auf Dokumentebene](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md)  
  
-   [Gewusst wie: Hinzufügen von benutzerdefinierten XML-Elementen zu Dokumenten mithilfe von VSTO-Add-ins](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)  
  
### <a name="modify-xml-parts-without-starting-the-office-application"></a>Ändern von XML-Elemente ohne die Office-Anwendung starten  
 Sie können ein benutzerdefiniertes XML-Element hinzufügen oder ändern, ohne Excel, PowerPoint oder Word zu starten. Dies ist hilfreich, wenn Sie mit XML-Daten in einem Dokument auf einem Computer arbeiten möchten, auf dem keine Microsoft Office-Anwendungen installiert sind (z. B. auf einem Server).  
  
 Wenn Sie ein benutzerdefiniertes XML-Element hinzufügen möchten, ohne Microsoft Office zu starten, verwenden Sie Klassen im Open XML SDK. Diese Klassen bieten Zugriff auf Open XML-Inhalt, der für Office-Dokumente spezifisch ist. Um ein benutzerdefiniertes XML-Element mit einer Excel-Arbeitsmappe hinzuzufügen, verwenden Sie z. B. die [AddNewPart\<T >](https://msdn.microsoft.com/library/office/cc562657.aspx) Methode eine [WorkbookPart](https://msdn.microsoft.com/library/office/documentformat.openxml.packaging.workbookpart.aspx) Objekt. Weitere Informationen finden Sie unter [Open XML SDK](/office/open-xml/open-xml-sdk).  
  
## <a name="bind-custom-xml-parts-to-word-content-controls"></a>Binden von benutzerdefinierten XML-Elementen an Word-Inhaltssteuerelementen  
 Sie können Inhaltssteuerelemente in einer Word-Projektmappe an Elemente in einem benutzerdefinierten XML-Element binden. Wenn ein Inhaltssteuerelement an ein benutzerdefiniertes XML-Element gebunden ist, werden die Daten im benutzerdefinierten XML-Element in der Benutzeroberfläche (User Interface, UI) des Inhaltssteuerelements angezeigt. Wenn ein Benutzer Text im Steuerelement bearbeitet, werden die entsprechenden XML-Elemente automatisch aktualisiert. Wenn Elementwerte in den benutzerdefinierten XML-Elementen geändert werden, zeigen die Inhaltssteuerelemente, die an die XML-Elemente gebunden sind, auf ähnliche Weise die neuen Daten an. Weitere Informationen finden Sie unter [Inhaltssteuerelemente](../vsto/content-controls.md).  
  
## <a name="see-also"></a>Siehe auch  
 [XML-Schemas und Daten in Anpassungen auf Dokumentebene](../vsto/xml-schemas-and-data-in-document-level-customizations.md)   
 [Gewusst wie: Hinzufügen von benutzerdefinierten XML-Abschnitten zu Anpassungen auf Dokumentebene](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md)   
 [Gewusst wie: Hinzufügen von benutzerdefinierten XML-Elementen zu Dokumenten mithilfe von VSTO-Add-ins](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)   
 [ContentControl-Elemente](../vsto/content-controls.md)   
 [Exemplarische Vorgehensweise: Binden von Inhaltssteuerelementen an benutzerdefinierte XML-Abschnitte](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md)  
  
  

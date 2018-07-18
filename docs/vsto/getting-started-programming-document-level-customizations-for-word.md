---
title: Erste Schritte zum Programmieren von Anpassungen auf Dokumentebene für Word
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word solutions in Visual Studio
- Word projects [Office development in Visual Studio], getting started
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a5bed5c08e15861840a34960d186b408fb86085d
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/22/2018
ms.locfileid: "34448853"
---
# <a name="get-started-programming-document-level-customizations-for-word"></a>Erste Schritte zum Programmieren von Anpassungen auf Dokumentebene für Word
  Wenn Sie nur die ersten Schritte Erstellen von Anpassungen auf Dokumentebene für Microsoft Office Word mithilfe von Visual Studio machen, ist hier was Sie wissen müssen.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
## <a name="understand-how-document-level-customizations-for-word-work"></a>Verstehen Sie, wie Anpassungen auf Dokumentebene für Word Arbeit  
 Jede Anpassung von Word, die Sie erstellen, basiert auf einem einzelnen Dokument. Um mit der Anpassung zu starten, der Endbenutzer Öffnet das Dokument oder das Dokument aus einer Word-Vorlage erstellt. Ereignisse in das Dokument, z. B. Bewegen des Cursors in bestimmte Bereiche oder durch Klicken auf Schaltflächen und Menüelementen können Ereignisbehandlungsmethoden in der Assembly aufrufen. Wenn das Dokument geschlossen wird, sind die von der Anpassung bereitgestellten Funktionen nicht mehr verfügbar in Word.  
  
 Weitere Informationen finden Sie unter [Architektur von Anpassungen auf Dokumentebene](../vsto/architecture-of-document-level-customizations.md).  
  
## <a name="create-document-level-projects-for-word"></a>Erstellen von Projekten auf Dokumentebene für Word  
 Um eine Anpassung auf Dokumentebene für Word erstellen, verwenden Sie die Word-Dokument oder Word-Vorlagen-Projektvorlage in die **neues Projekt** (Dialogfeld). Diese Vorlagen enthalten erforderliche Assemblyverweise und Projektdateien.  
  
 Weitere Informationen dazu, wie Sie ein Projekt auf Dokumentebene für Word zu erstellen, finden Sie unter [Vorgehensweise: Erstellen von Office-Projekte in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md). Weitere Informationen zu den Projektvorlagen finden Sie unter [Übersicht über Office-Projektvorlagen](../vsto/office-project-templates-overview.md).  
  
## <a name="program-word-documents-by-using-host-items-host-controls"></a>Programm Word-Dokumenten mithilfe von Hostelementen und Hoststeuerelementen  
 *Hostelemente* und *Hoststeuerelemente* sind Klassen, die das Programmiermodell für Anpassungen auf Dokumentebene bereitstellen.  
  
 Hostelemente stellen einen Einstiegspunkt für Ihren Code bereit, und sie können auch dienen als Container für Hoststeuerelemente und Windows Forms-Steuerelemente. In Projekten auf Dokumentebene für Word, wird durch das Hostelement dargestellt die `ThisDocument` Klasse.  
  
 Hoststeuerelemente basieren auf systemeigenen Word-Objekte, wie z. B. Inhaltssteuerelemente und Lesezeichen, XML-Knoten. Hoststeuerelemente stellen ähnliche Funktionen wie die systemeigenen Word-Objekte, jedoch auch über neue Ereignisse, designerunterstützung und Datenbindung Funktion. Sie sind als erstklassige Objekte in Ihrem Projektcode und in IntelliSense zu auf bestimmte Objekte direkt im Code zu verweisen, ohne das Word-Objektmodell zu navigieren.  
  
 Weitere Informationen finden Sie unter den folgenden Themen:  
  
-   [Programmieren von Anpassungen auf Dokumentebene](../vsto/programming-document-level-customizations.md)  
  
-   [Automatisieren von Word mithilfe von erweiterten Objekten](../vsto/automating-word-by-using-extended-objects.md)  
  
-   [Hostelemente und Host-Steuerelemente (Übersicht)](../vsto/host-items-and-host-controls-overview.md)  
  
## <a name="customize-the-user-interface-of-word"></a>Anpassen der Benutzeroberfläche von Word  
 Die meisten Microsoft Office-Projektmappen Anpassen der Benutzeroberfläche (UI) der Office-Anwendung für Benutzer für die Interaktion mit der Lösung einige Möglichkeit bereitstellen. Es gibt viele Möglichkeiten, die in denen Sie die Benutzeroberfläche von Word mithilfe einer Anpassung auf Dokumentebene ändern. Z. B. Hinzufügen von Steuerelementen auf dem Menüband, und Sie können einen Aktionsbereich anzeigen. Weitere Informationen finden Sie unter [Anpassung der Office-Benutzeroberfläche](../vsto/office-ui-customization.md).  
  
 Sie können auch das Dokument öffnen, das das Projekt in Visual Studio direkt zugeordnet ist. Wenn das Dokument in Visual Studio geöffnet ist, können Sie das Dokument mit der Word-Benutzeroberfläche ändern. Sie können auch das Dokument als Entwurfsoberfläche, die Sie Steuerelemente darauf ziehen können. Weitere Informationen finden Sie unter [Office-Projekte in Visual Studio-Umgebung](../vsto/office-projects-in-the-visual-studio-environment.md).  
  
## <a name="bind-controls-to-data"></a>Binden von Steuerelementen an Daten  
 Der Content-Steuerelemente und die <xref:Microsoft.Office.Tools.Word.Bookmark> Steuerelement in der Liste der Steuerelemente, die Sie in ziehen können, sind die **Datenquellen** Fenster. Hinzufügen von Inhaltssteuerelemente und Lesezeichen in dieser Weise automatisch bindet diese an die Datenquelle, die Sie eingerichtet haben, mithilfe des Fensters. Ohne Code schreiben zu müssen, können Sie Daten aus Datenbanken, Diensten und Geschäftsobjekten anzeigen. Weitere Informationen finden Sie unter [Binden von Daten an Steuerelemente in Office-Projektmappen](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
## <a name="next-steps"></a>Nächste Schritte  
 Gewusst wie: erstellen eine Anpassung auf Dokumentebene für Word finden Sie unter [Exemplarische Vorgehensweise: Erstellen der ersten Anpassung auf Dokumentebene für Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md). In dieser exemplarischen Vorgehensweise werden die Office-Entwicklungstools in Visual Studio und dem Programmiermodell für Anpassungen auf Anwendungsebene Word vorgestellt.  
  
 Eine Liste der Themen, in denen Sie einige der allgemeinen Aufgaben in Word-Projekten durchlaufen, finden Sie unter [häufige Aufgaben bei der Programmierung mit Office](../vsto/common-tasks-in-office-programming.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Programmieren von Anpassungen auf Dokumentebene](../vsto/programming-document-level-customizations.md)   
 [Word-Projektmappen](../vsto/word-solutions.md)   
 [Exemplarische Vorgehensweise: Erstellen der ersten Anpassung auf Dokumentebene für Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)   
 [Exemplarische Vorgehensweisen in Word](../vsto/walkthroughs-using-word.md)   
 [Übersicht über das Word-Objektmodell](../vsto/word-object-model-overview.md)   
 [Schreiben von Code in Office-Projektmappen](../vsto/writing-code-in-office-solutions.md)  
  
  
---
title: Automatisieren von Word mithilfe von erweiterten Objekten | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word [Office development in Visual Studio], automating
- extended objects [Office development in Visual Studio], Word
- automation [Office development in Visual Studio], Word
- host items [Office development in Visual Studio], Word
- automating Word
- controls [Office development in Visual Studio], Word host controls
- host controls, Word
- host controls [Office development in Visual Studio], Word
- Word [Office development in Visual Studio], host controls
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: f7452826ed0726f095a2ae6a8add12d8b07bd2e7
ms.sourcegitcommit: 04a717340b4ab4efc82945fbb25dfe58add2ee4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/28/2018
---
# <a name="automating-word-by-using-extended-objects"></a>Automatisieren von Word mithilfe von erweiterten Objekten
  Wenn Sie Word-Projektmappen in Visual Studio entwickeln, können Sie auch *Hostelemente* und *Hoststeuerelemente*in den Projektmappen verwenden. Dies sind Objekte, die bestimmte häufig verwendete Objekte im Word-Objektmodell (das von der primären Interopassembly für Word verfügbar gemacht wird) erweitern. Dazu gehören z. B. die Objekte <xref:Microsoft.Office.Interop.Word.Document> und <xref:Microsoft.Office.Interop.Word.ContentControl> . Die erweiterten Objekte verhalten sich wie die Word-Objekte, auf denen sie basieren, fügen den Objekten jedoch zusätzliche Ereignis- und Datenbindungsfunktionen hinzu.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 Hostelemente und Hoststeuerelemente sind sowohl in VSTO-Add-Ins als auch in Anpassungen auf Dokumentebene verfügbar, obwohl der Kontext, in dem diese verwendet werden können, für jeden Projektmappentyp anders ist. Weitere Informationen finden Sie unter [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md).  
  
## <a name="document-host-item"></a>Dokumenthostelement  
 In Word-Projekten haben Sie Zugriff auf das <xref:Microsoft.Office.Tools.Word.Document> -Hostelement. Das <xref:Microsoft.Office.Tools.Word.Document> -Hostelement dient als Container für andere Steuerelemente, einschließlich Hoststeuerelementen und Windows Forms-Steuerelementen, und es enthält Informationen über die Steuerelemente auf seiner Oberfläche. Das <xref:Microsoft.Office.Tools.Word.Document> -Hostelement stellt auch einen Großteil derselben Member wie die <xref:Microsoft.Office.Interop.Word.Document> -Klasse bereit, die die entsprechende Klasse im Word-Objektmodell ist.  
  
 Weitere Informationen finden Sie unter [Document Host Item](../vsto/document-host-item.md).  
  
## <a name="word-host-controls"></a>Word-Hoststeuerelemente  
 Es gibt mehrere Hoststeuerelemente für Word, mit denen Sie Dokumente erstellen, organisieren und automatisieren können. Zu deren Hauptfunktionen zählen das Importieren, Darstellen und Schützen von Daten. Diese Hoststeuerelemente stellen Ereignisse und Datenbindungsfunktionen bereit, die in ihren Äquivalenten im systemeigenen Word-Objektmodell fehlen.  
  
 In Projekten auf Dokumentebene können Sie dem Dokument zur Entwurfszeit jedes beliebige Hoststeuerelement oder zur Laufzeit Inhaltssteuerelemente und Lesezeichen-Steuerelemente hinzufügen. In VSTO-Add-In-Projekten können Sie einem beliebigen geöffneten Dokument zur Laufzeit Inhaltssteuerelemente und Lesezeichen-Steuerelemente hinzufügen.  
  
 Weitere Informationen zu den Hoststeuerelementen, die Sie in Word-Projekten verwenden können, finden Sie unter den folgenden Themen:  
  
-   [Inhaltssteuerelemente](../vsto/content-controls.md)  
  
-   [Bookmark-Steuerelement](../vsto/bookmark-control.md)  
  
-   [XMLNode-Steuerelement](../vsto/xmlnode-control.md)  
  
-   [XMLNodes-Steuerelement](../vsto/xmlnodes-control.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Hinzufügen von Inhaltssteuerelementen zu Word-Dokumenten](../vsto/how-to-add-content-controls-to-word-documents.md)   
 [Gewusst wie: Hinzufügen von Bookmark-Steuerelementen zu Word-Dokumenten](../vsto/how-to-add-bookmark-controls-to-word-documents.md)   
 [Vorgehensweise: Hinzufügen von XMLNode-Steuerelementen zu Word-Dokumenten](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)   
 [Vorgehensweise: Hinzufügen von XMLNodes-Steuerelementen zu Word-Dokumenten](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)   
 [Vorgehensweise: Ändern der Größe Lesezeichen-Steuerelementen](../vsto/how-to-resize-bookmark-controls.md)   
 [Exemplarische Vorgehensweise: Erstellen einer Vorlage mithilfe von Inhaltssteuerelementen](../vsto/walkthrough-creating-a-template-by-using-content-controls.md)   
 [Exemplarische Vorgehensweise: Binden von Inhaltssteuerelementen an benutzerdefinierte XML-Abschnitte](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md)   
 [Exemplarische Vorgehensweise: Erstellen von Kontextmenüs für Lesezeichen](../vsto/walkthrough-creating-shortcut-menus-for-bookmarks.md)   
 [Word-Projektmappen](../vsto/word-solutions.md)   
 [Übersicht über Hostelemente und Hoststeuerelemente](../vsto/host-items-and-host-controls-overview.md)   
 [Programmgesteuerte Einschränkungen von Hostelementen und Hoststeuerelementen](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Erweitern von Word-Dokumenten und Excel-Arbeitsmappen in VSTO-Add-Ins zur Laufzeit](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)  
  
  
---
title: Zwischengespeicherte Daten in Anpassungen auf Dokumentebene
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data islands [Office development in Visual Studio]
- view [Office development in Visual Studio]
- caching data [Office development in Visual Studio], about caching data
- data caching [Office development in Visual Studio], about data caching
- data [Office development in Visual Studio], cache
- data [Office development in Visual Studio], document-level solutions
- document-level customizations [Office development in Visual Studio], data model
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0710f196e6572cf6bc9851d8a765758fcb43326d
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/06/2018
ms.locfileid: "35673208"
---
# <a name="cached-data-in-document-level-customizations"></a>Zwischengespeicherte Daten in Anpassungen auf Dokumentebene
  Ein primäres Ziel von Anpassungen auf Dokumentebene ist, Daten aus der Ansicht in Office-Dokumenten zu trennen. Daten bezieht sich auf die Informationen, die in das Dokument, einschließlich der Zahlen und Text gespeichert ist. Ansicht bezieht sich auf die Benutzeroberfläche und das Objektmodell der Microsoft Office Word und Microsoft Office Excel.  
  
 Visual Studio trennt die Daten aus der Sicht in Anpassungen auf Dokumentebene zu ermöglichen, die als eingebettet werden eine *Dateninsel*auch Namens der *Datencache*. Sie können die lesen oder ändern die Daten direkt, ohne den Computer neu zu starten, Word- oder Excel. Dies ist nützlich, wenn Daten in Dokumenten auf einem Server zu ändern, die keine für Microsoft Office installiert werden sollen. Word und Excel sind für die Verwendung in Client-Umgebungen vorgesehen; Sie sind nicht für die Ausführung auf einem Server konzipiert.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Weitere Informationen zu Anpassungen auf Dokumentebene, finden Sie unter [Übersicht über die Entwicklung von Office-Projektmappen &#40;VSTO&#41; ](../vsto/office-solutions-development-overview-vsto.md) und [Architektur von Anpassungen auf Dokumentebene](../vsto/architecture-of-document-level-customizations.md).  
  
## <a name="understand-the-cached-data-programming-model"></a>Das Programmiermodell von zwischengespeicherten Daten verstehen  
 Die Dateninsel kann jedes Objekt in der Projektmappe enthalten, die bestimmte Anforderungen erfüllt. Zu diesen Objekten gehören <xref:System.Data.DataSet> Objekte <xref:System.Data.DataTable> Objekte und jedes andere Objekt, das vom serialisiert werden kann die <xref:System.Xml.Serialization.XmlSerializer> Klasse. Weitere Informationen finden Sie unter [Zwischenspeichern von Daten](../vsto/caching-data.md).  
  
 Um die Ansicht für die zwischengespeicherten Daten zu gewährleisten, können Sie Windows Forms-Steuerelemente binden und *Hoststeuerelemente* für das Dokument auf Objekte in der Dateninsel. Die Datenbindung zwischen der Dateninsel und die von datengebundenen Steuerelementen behält die beiden synchronisiert. Sie können auch Code für die Überprüfung auf die Daten hinzufügen, die unabhängig von den Steuerelementen. Weitere Informationen finden Sie unter [Binden von Daten an Steuerelemente in Office-Projektmappen](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
 Hoststeuerelemente sind systemeigene Objekte in den Objektmodellen von Excel und Word-Versionen erweitert. Im Gegensatz zu den systemeigenen Objekten können die Host-Steuerelementen direkt auf verwaltete Objekte gebunden werden. Weitere Informationen finden Sie unter [hosten Elemente und Übersicht zu Steuerelementen](../vsto/host-items-and-host-controls-overview.md) und [Windows Forms-Steuerelemente in Office-Dokumente – Übersicht](../vsto/windows-forms-controls-on-office-documents-overview.md).  
  
## <a name="access-cached-data-on-the-server"></a>Access zwischengespeicherte Daten auf dem server  
 Um zwischengespeicherte Daten in einem Dokument zuzugreifen, können Sie die <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> Klasse. Diese Klasse ist Teil der [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], und es kann auf einem Server ohne ausgeführte Excel oder Word verwendet werden. Wenn öffnet der Benutzer das Dokument, nachdem Sie die zwischengespeicherten Daten ändern, alle Steuerelemente, die an Daten gebunden sind, die Änderungen automatisch synchronisiert werden und der Benutzer mit den aktualisierten Daten erhält. Weitere Informationen finden Sie unter [Zugriff auf Daten in Dokumenten auf dem Server](../vsto/accessing-data-in-documents-on-the-server.md).  
  
 Excel und Word sind nicht erforderlich, um die Daten auf dem Server, nur um es auf dem Client anzeigen. Excel und Word müssen selbst nicht auf dem Server installiert werden. Dies bietet verbesserte Skalierbarkeit und die Möglichkeit zum Ausführen von schnellen Batchverarbeitung von Dokumenten, die Dateninseln enthalten.  
  
## <a name="data-caching-for-offline-use"></a>Für die Offlineverwendung Zwischenspeichern von Daten  
 Speichern von Daten in der Dateninsel kann offline-Szenarien. Wenn ein Benutzer zunächst ein Dokument öffnet oder das Dokument vom Server anfordert, wird die Dateninsel mit den neuesten Daten gefüllt. Die Dateninsel wird im Dokument zwischengespeichert, und es ist dann offline verfügbar. Der Benutzer (und Ihr Code) können die Daten, bearbeitet, obwohl keine live-Verbindung verfügbar ist. Wenn der Benutzer erneut eine Verbindung herstellt, können die Änderungen an den Daten an eine Datenquelle für den Server weitergegeben werden.  
  
## <a name="cached-data-and-custom-xml-parts-compared"></a>Zwischengespeicherte Daten und benutzerdefinierte XML-Elemente, die im Vergleich  
 Benutzerdefinierte XML-Elemente wurden als eine Möglichkeit zum Speichern von beliebigen XML-Elemente in einem Dokument im 2007 Microsoft Office System eingeführt. Obwohl benutzerdefinierte XML-Elemente in vielen dieselben Szenarios wie dem Datencache nützlich sind, gibt es einige Unterschiede zwischen der Dateninsel und benutzerdefinierte XML-Elemente. Weitere Informationen zu benutzerdefinierten XML-Elementen, finden Sie unter [Übersicht über benutzerdefinierte XML-Abschnitte](../vsto/custom-xml-parts-overview.md).  
  
 Die folgende Tabelle enthält einige der Unterschiede und ähnlichkeiten.  
  
||Datencache|Benutzerdefinierte XML-Elemente|  
|-|----------------|----------------------|  
|Welche Office-Anwendungen können diese verwenden?|Anpassungen auf Dokumentebene für die folgenden Anwendungen:<br /><br /> -Excel<br />-Word|Dokument- und Anwendungsebene Lösungen für die folgenden Anwendungen:<br /><br /> -Excel<br />-PowerPoint<br />-Word|  
|Welche Arten von Daten können Sie speichern?|Alle öffentlichen Objekt in der Anpassungsassembly, die bestimmte Anforderungen erfüllt. Weitere Informationen finden Sie unter [Zwischenspeichern von Daten](../vsto/caching-data.md).|Alle XML-Daten.|  
|Können Sie die Daten ohne Starten des Microsoft Office-Anwendungen zugreifen?|Ja, mithilfe der <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> vom bereitgestellten-Klasse die [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].|Ja, mithilfe von Klassen in der <xref:System.IO.Packaging> -Namespace oder mithilfe von Open XML-Format SDK.|  
  
## <a name="see-also"></a>Siehe auch  
 [Daten in Office-Projektmappen](../vsto/data-in-office-solutions.md)   
 [Architektur von Office-Projektmappen in Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)  
  
  
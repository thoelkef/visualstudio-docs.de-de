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
ms.openlocfilehash: bd93d985b72f945e7a1c70199d6ff3aacf5f0229
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
---
# <a name="cached-data-in-document-level-customizations"></a>Zwischengespeicherte Daten in Anpassungen auf Dokumentebene
  Eine primäre Zweck von Anpassungen auf Dokumentebene ist zum Aufteilen von Daten aus der Ansicht in Office-Dokumenten. Daten bezieht sich auf die Informationen, die in das Dokument, einschließlich von Zahlen und Text gespeichert ist. Ansicht bezieht sich auf der Benutzeroberfläche und das Objektmodell der Microsoft Office Word und Microsoft Office Excel.  
  
 Visual Studio trennt die Daten aus der Sicht in Anpassungen auf Dokumentebene durch Aktivieren der Daten, die als eingebettet werden eine *Dateninsel*auch Namens der *Datencache*. Sie können die lesen oder ändern die Daten direkt, ohne den Computer neu zu starten, Word oder Excel. Dies ist hilfreich, wenn Daten in Dokumenten auf einem Server zu ändern, die keine für Microsoft Office installiert werden muss. Word und Excel sind für die Verwendung in Clientumgebungen vorgesehen; Sie dienen nicht auf einem Server ausgeführt werden.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Weitere Informationen zu Anpassungen auf Dokumentebene finden Sie unter [Übersicht über die Entwicklung von Office-Lösungen &#40;VSTO&#41; ](../vsto/office-solutions-development-overview-vsto.md) und [Architektur von Anpassungen auf Dokumentebene](../vsto/architecture-of-document-level-customizations.md).  
  
## <a name="understand-the-cached-data-programming-model"></a>Das Programmiermodell von zwischengespeicherten Daten verstehen  
 Die Dateninsel kann jedes Objekt in der Projektmappe enthalten, die bestimmte Anforderungen erfüllt. Zu diesen Objekten gehören <xref:System.Data.DataSet> Objekte <xref:System.Data.DataTable> Objekte und ein anderes Objekt, das vom serialisiert werden kann die <xref:System.Xml.Serialization.XmlSerializer> Klasse. Weitere Informationen finden Sie unter finden Sie unter [Zwischenspeichern von Daten](../vsto/caching-data.md).  
  
 Um die Ansicht für die zwischengespeicherten Daten zu gewährleisten, können Sie Windows Forms-Steuerelemente binden und *Hoststeuerelemente* auf das Dokument, um Objekte in der Dateninsel. Die Datenbindung zwischen Dateninsel und die datengebundenen Steuerelemente behält die beiden synchronisiert. Sie können auch Validierungscode hinzufügen, die auf die Daten, die von den Steuerelementen unabhängig ist. Weitere Informationen finden Sie unter [Binden von Daten an Steuerelemente in Office-Projektmappen](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
 Hoststeuerelemente sind native Objekte in den Objektmodellen von Excel- und Word-Versionen erweitert. Im Gegensatz zu den systemeigenen Objekten können Hoststeuerelemente direkt an verwaltete Datenobjekte gebunden werden. Weitere Informationen finden Sie unter [Hostelemente und Hosten von Steuerelementen (Übersicht)](../vsto/host-items-and-host-controls-overview.md) und [Windows Forms-Steuerelemente für Office-Dokumente (Übersicht)](../vsto/windows-forms-controls-on-office-documents-overview.md).  
  
## <a name="access-cached-data-on-the-server"></a>Zugriff zwischengespeicherten Daten auf dem server  
 Für den Zugriff auf zwischengespeicherte Daten in einem Dokument, können Sie die <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> Klasse. Diese Klasse ist Teil der [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], und es kann auf einem Server ohne Ausführen von Excel oder Word verwendet werden. Wenn öffnet der Benutzer das Dokument, nachdem Sie die zwischengespeicherten Daten ändern, alle Steuerelemente, die an Daten gebunden sind, automatisch mit den Änderungen synchronisiert werden und der Benutzer mit den neuen Daten erhält. Weitere Informationen finden Sie unter [zugreifen auf Daten in Dokumenten auf dem Server](../vsto/accessing-data-in-documents-on-the-server.md).  
  
 Excel und Word sind nicht erforderlich, auf die Daten auf dem Server nur für die Anzeige auf dem Client zu schreiben. Excel und Word müssen nicht auf dem Server installiert werden. Dies bietet bessere Skalierbarkeit und die Fähigkeit zum Ausführen von schnellen Batchverarbeitung von Dokumenten, die Dateninseln enthalten.  
  
## <a name="data-caching-for-offline-use"></a>Für die Offlineverwendung Zwischenspeichern von Daten  
 Speichern von Daten in der Dateninsel ermöglicht Offlineszenarien unmöglich. Wenn ein Benutzer zuerst ein Dokument öffnet oder das Dokument vom Server anfordert, wird die Dateninsel mit den neuesten Daten gefüllt. Die Dateninsel wird in das Dokument zwischengespeichert und ist dann offline verfügbar. Der Benutzer (und Ihren Code) können die Daten bearbeitet werden, obwohl keine aktive Verbindung verfügbar ist. Wenn der Benutzer erneut eine Verbindung herstellt, können die Änderungen an den Daten an eine Datenquelle für den Server weitergegeben werden.  
  
## <a name="cached-data-and-custom-xml-parts-compared"></a>Zwischengespeicherte Daten und benutzerdefinierte XML-Elemente, die im Vergleich  
 Benutzerdefinierte XML-Elemente wurden im 2007 Microsoft Office System als eine Möglichkeit zum Speichern beliebiger Teile von XML in einem Dokument eingeführt. Obwohl benutzerdefinierte XML-Teile in vielen Szenarien Datencache nützlich sind, gibt es einige Unterschiede zwischen den Dateninseln und benutzerdefinierten XML-Elementen. Weitere Informationen zu benutzerdefinierten XML-Elementen, finden Sie unter [Übersicht über benutzerdefinierte XML-Abschnitte](../vsto/custom-xml-parts-overview.md).  
  
 Die folgende Tabelle enthält einige der Unterschiede und ähnlichkeiten.  
  
||Datencache|Benutzerdefinierte XML-Teile|  
|-|----------------|----------------------|  
|Welche Office-Anwendungen können diese verwenden?|Anpassungen auf Dokumentebene für die folgenden Anwendungen:<br /><br /> -Excel<br />-Word|Auf Dokumentebene und Anwendungsebene Lösungen für die folgenden Anwendungen:<br /><br /> -Excel<br />-PowerPoint<br />-Word|  
|Welche Arten von Daten können Sie speichern?|Alle öffentlichen Objekt in der Anpassungsassembly, die bestimmte Anforderungen erfüllt. Weitere Informationen finden Sie unter [Zwischenspeichern von Daten](../vsto/caching-data.md).|Alle XML-Daten.|  
|Können Sie die Daten ohne Starten des Microsoft Office-Anwendungen zugreifen?|Ja, mithilfe der <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> Klasse bereitgestellt wird, durch die [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].|Ja, mithilfe der Klassen in der <xref:System.IO.Packaging> -Namespace oder mithilfe des Open XML-Format SDK.|  
  
## <a name="see-also"></a>Siehe auch  
 [Daten in Office-Projektmappen](../vsto/data-in-office-solutions.md)   
 [Architektur von Office-Projektmappen in Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)  
  
  
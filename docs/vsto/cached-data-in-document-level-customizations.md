---
title: "Zwischengespeicherte Daten in Anpassungen auf Dokumentebene"
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
  - "Zwischenspeichern von Daten [Office-Entwicklung in Visual Studio], Informationen zum Zwischenspeichern von Daten"
  - "Daten [Office-Entwicklung in Visual Studio], Cache"
  - "Daten [Office-Entwicklung in Visual Studio], Projektmappen auf Dokumentebene"
  - "Zwischenspeichern von Daten [Office-Entwicklung in Visual Studio], Informationen zum Datencaching"
  - "Dateninseln [Office-Entwicklung in Visual Studio]"
  - "Anpassungen auf Dokumentebene [Office-Entwicklung in Visual Studio], Datenmodell"
  - "Ansicht [Office-Entwicklung in Visual Studio]"
ms.assetid: 84808462-2c5d-4dc8-ab69-491d492b4a51
caps.latest.revision: 27
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 26
---
# Zwischengespeicherte Daten in Anpassungen auf Dokumentebene
  Ein Hauptziel von Anpassungen auf Dokumentebene besteht darin, Daten von der Ansicht in Office\-Dokumenten zu trennen.  Mit Daten sind die Informationen gemeint, die im Dokument gespeichert sind. Dazu gehören Zahlen und Text.  Mit Ansicht sind die Benutzeroberfläche und das Objektmodell von Microsoft Office Word und Microsoft Office Excel gemeint.  
  
 Visual Studio trennt die Daten von der Ansicht in Anpassungen auf Dokumentebene, indem es ihre Einbettung als *Dateninsel* ermöglicht, die auch *Datencache* genannt wird.  Sie können die Daten direkt lesen oder ändern, ohne Word oder Excel zu starten.  Dies ist hilfreich, wenn Sie Daten in Dokumenten auf einem Server ohne installiertes Microsoft Office ändern müssen.  Word und Excel sind für die Verwendung in Clientumgebungen vorgesehen, jedoch nicht für die Ausführung auf einem Server.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Weitere Informationen zu Anpassungen auf Dokumentebene finden Sie unter [Übersicht über die Entwicklung von Office-Projektmappen &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md) und unter [Architektur von Anpassungen auf Dokumentebene](../vsto/architecture-of-document-level-customizations.md).  
  
## Das zwischengespeicherte Datenprogrammiermodell  
 Die Dateninsel kann jedes Objekt in der Projektmappe enthalten, das bestimmte Anforderungen erfüllt.  Zu diesen Objekten gehören <xref:System.Data.DataSet>\-Objekte, <xref:System.Data.DataTable>\-Objekte und alle anderen Objekte, die von der <xref:System.Xml.Serialization.XmlSerializer>\-Klasse serialisiert werden können.  Weitere Informationen finden Sie unter [Zwischenspeichern von Daten](../vsto/caching-data.md).  
  
 Um eine Ansicht für die zwischengespeicherten Daten bereitzustellen, können Sie Windows Forms\-Steuerelemente und *Hoststeuerelemente* im Dokument an Objekte in der Dateninsel binden.  Durch die Datenbindung zwischen der Dateninsel und den datengebundenen Steuerelementen bleiben beide synchron.  Sie können den Daten auch Validierungscode hinzufügen, der von den Steuerelementen unabhängig ist.  Weitere Informationen finden Sie unter [Binden von Daten an Steuerelemente in Office-Projektmappen](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
 Hoststeuerelemente sind erweiterte Versionen systemeigener Objekte in Excel\- und Word\-Objektmodellen.  Im Gegensatz zu den systemeigenen Objekten können Hoststeuerelemente direkt an verwaltete Datenobjekte gebunden werden.  Weitere Informationen finden Sie unter [Übersicht über Hostelemente und Hoststeuerelemente](../vsto/host-items-and-host-controls-overview.md) und [Übersicht über Windows Forms-Steuerelemente in Office-Dokumenten](../vsto/windows-forms-controls-on-office-documents-overview.md).  
  
## Zugreifen auf zwischengespeicherte Daten auf dem Server  
 Zum Zugreifen auf zwischengespeicherte Daten in einem Dokument können Sie die <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>\-Klasse verwenden.  Diese Klasse ist Teil von [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] und kann auf einem Server verwendet werden, ohne Excel oder Word auszuführen.  Wenn der Benutzer das Dokument öffnet, nachdem Sie die zwischengespeicherten Daten geändert haben, werden alle Steuerelemente, die an die Daten gebunden sind, automatisch mit den Änderungen synchronisiert, und dem Benutzer werden die aktualisierten Daten angezeigt.  Weitere Informationen finden Sie unter [Zugreifen auf Daten in Dokumenten auf dem Server](../vsto/accessing-data-in-documents-on-the-server.md).  
  
 Excel und Word werden nicht benötigt, um die Daten auf dem Server zu bearbeiten, sondern nur, um sie auf dem Client anzuzeigen.  Excel und Word müssen nicht einmal auf dem Server installiert sein.  Das bietet eine verbesserte Skalierbarkeit und die Möglichkeit, eine schnelle Batchverarbeitung von Dokumenten mit Dateninseln auszuführen.  
  
## Zwischenspeicherung von Daten für die Offlineverwendung  
 Durch das Speichern von Daten in der Dateninsel werden Offlineszenarien aktiviert.  Wenn ein Benutzer ein Dokument erstmals öffnet oder vom Server anfordert, wird die Dateninsel mit den aktuellsten Daten gefüllt.  Die Dateninsel wird im Dokument zwischengespeichert und ist dann offline verfügbar.  Die Daten können vom Benutzer \(und dem Code\) bearbeitet werden, obwohl keine aktive Verbindung verfügbar ist.  Wenn der Benutzer erneut eine Verbindung herstellt, können die Änderungen der Daten an eine Serverdatenquelle zurückgegeben werden.  
  
## Zwischengespeicherte Daten und benutzerdefinierte XML\-Abschnitte im Vergleich  
 Benutzerdefinierte XML\-Abschnitte wurden in 2007 Microsoft Office System zum Speichern beliebiger Teile von XML\-Code in einem Dokument eingeführt.  Obwohl benutzerdefinierte XML\-Abschnitte in vielen Szenarien nützlich sind, die denen des Datencache ähneln, gibt es einige Unterschiede zwischen den Dateninseln und benutzerdefinierten XML\-Abschnitten.  Weitere Informationen zu benutzerdefinierten XML\-Abschnitten finden Sie unter [Übersicht über benutzerdefinierte XML-Abschnitte](../vsto/custom-xml-parts-overview.md).  
  
 In der folgenden Tabelle werden einige der Unterschiede und der Ähnlichkeiten aufgelistet.  
  
||Datencache|Benutzerdefinierte XML\-Abschnitte|  
|-|----------------|----------------------------------------|  
|Welche Office\-Anwendungen können sie verwenden?|Anpassungen auf Dokumentebene für die folgenden Anwendungen:<br /><br /> -   Excel<br />-   Word|Projektmappen auf Dokumentebene und auf Anwendungsebene für die folgenden Anwendungen:<br /><br /> -   Excel<br />-   PowerPoint<br />-   Word|  
|Welche Arten von Daten können Sie speichern?|Ein beliebiges öffentliches Objekt in der Anpassungsassembly, das bestimmte Anforderungen erfüllt.  Weitere Informationen finden Sie unter [Zwischenspeichern von Daten](../vsto/caching-data.md).|Beliebige XML\-Daten.|  
|Können Sie auf die Daten zugreifen, ohne Microsoft Office\-Anwendungen zu starten?|Ja, mithilfe der <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>\-Klasse, die durch [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] bereitgestellt wird.|Ja, mithilfe der Klassen im <xref:System.IO.Packaging>\-Namespace oder mit dem Open XML\-Format\-SDK.|  
  
## Siehe auch  
 [Daten in Office-Lösungen](../vsto/data-in-office-solutions.md)   
 [Architektur von Office-Projektmappen in Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)  
  
  
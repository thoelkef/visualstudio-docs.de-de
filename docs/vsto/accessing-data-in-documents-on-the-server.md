---
title: "Zugreifen auf Daten in Dokumenten auf dem Server | Microsoft Docs"
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
  - "Daten [Office-Entwicklung in Visual Studio], Zugriff auf dem Server"
  - "Datenzugriff [Office-Entwicklung in Visual Studio]"
ms.assetid: 14a42e96-ed2f-48a1-a0c0-e19f9eba4956
caps.latest.revision: 32
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 31
---
# Zugreifen auf Daten in Dokumenten auf dem Server
  Sie können beim Programmieren die Daten einer Anpassung auf Dokumentebene verwenden, ohne dass Sie das Objektmodell von Microsoft Office Word oder Microsoft Office Excel verwenden müssen.  Das bedeutet, dass Sie auf Daten zugreifen können, die in einem Dokument auf einem Server enthalten sind, auf dem Word oder Excel nicht installiert sind.  Beispielsweise können mithilfe von Code auf dem Server \(z. B. auf einer [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]\-Seite\) die Daten in einem Dokument angepasst werden, und das angepasste Dokument kann an einen Endbenutzer gesendet werden.  Wenn der Endbenutzer das Dokument öffnet, bindet der Code für die Datenbindung in der Projektmappenassembly die angepassten Daten in das Dokument.  Dies ist möglich, da die Daten in dem Dokument von der Benutzeroberfläche getrennt sind.  Weitere Informationen finden Sie unter [Zwischengespeicherte Daten in Anpassungen auf Dokumentebene](../vsto/cached-data-in-document-level-customizations.md).  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## Zwischenspeichern von Daten für die Verwendung auf einem Server  
 Sie können ein Datenobjekt in einem Dokument zwischenspeichern, indem Sie es zur Entwurfszeit mit dem <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute>\-Attribut markieren oder zur Laufzeit die `StartCaching`\-Methode eines Hostelements verwenden.  Wenn Sie ein Datenobjekt in einem Dokument zwischenspeichern, serialisiert [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] das Objekt in eine XML\-Zeichenfolge, die im Dokument gespeichert wird.  Objekte müssen bestimmte Anforderungen erfüllen, um für das Zwischenspeichern geeignet zu sein.  Weitere Informationen finden Sie unter [Zwischenspeichern von Daten](../vsto/caching-data.md).  
  
 In serverseitigem Code können alle Datenobjekte im Datencache bearbeitet werden.  Steuerelemente, die an zwischengespeicherte Dateninstanzen gebunden sind, werden mit der Benutzeroberfläche synchronisiert, sodass alle serverseitigen Änderungen der Daten automatisch beim Öffnen des Dokuments auf dem Client angezeigt werden.  
  
## Zugreifen auf Daten im Cache  
 Sie können von Anwendungen außerhalb von Office, z. B. von einer Konsolenanwendung, einer Windows Forms\-Anwendung oder einer Webseite, auf Daten im Cache zugreifen.  Die Anwendung, die auf die zwischengespeicherten Daten zugreift, muss als vollständig vertrauenswürdig eingestuft sein. Eine nur teilweise vertrauenswürdige Webanwendung kann Daten, die in einem Office\-Dokument zwischengespeichert sind, nicht einfügen, abrufen oder ändern.  
  
 Auf den Datencache kann mithilfe einer Auflistungshierarchie zugegriffen werden, die durch die <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A>\-Eigenschaft der <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>\-Klasse verfügbar gemacht wird:  
  
-   Die <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A>\-Eigenschaft gibt <xref:Microsoft.VisualStudio.Tools.Applications.CachedData> mit allen zwischengespeicherten Daten in einer Anpassung auf Dokumentebene zurück.  
  
-   Jedes <xref:Microsoft.VisualStudio.Tools.Applications.CachedData> enthält mindestens ein <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem>\-Objekt.  Ein <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem> enthält sämtliche zwischengespeicherten Datenobjekte, die innerhalb einer einzelnen Klasse definiert sind.  
  
-   Jedes <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem> enthält mindestens ein <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem>\-Objekt.  Ein <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> stellt ein einzelnes zwischengespeichertes Datenobjekt dar.  
  
 Das folgende Codebeispiel veranschaulicht, wie Sie auf eine Zeichenfolge im Cache in der `Sheet1`\-Klasse eines Excel\-Arbeitsmappenprojekts zugreifen können.  Dieses Beispiel ist Teil eines umfangreicheren Beispiels für die <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.Save%2A>\-Methode.  
  
 [!code-csharp[Trin_ServerDocument#12](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ServerDocument/CS/Form1.cs#12)]
 [!code-vb[Trin_ServerDocument#12](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ServerDocument/VB/Form1.vb#12)]  
  
## Ändern von Daten im Cache  
 Um ein Datenobjekt im Cache zu ändern, führen Sie normalerweise die folgenden Schritte aus:  
  
1.  Deserialisieren Sie die XML\-Darstellung des zwischengespeicherten Objekts in eine neue Instanz des Objekts.  Sie können über die <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.Xml%2A>\-Eigenschaft des <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem>, das das zwischengespeicherte Datenobjekt darstellt, auf die XML\-Darstellung zugreifen.  
  
2.  Nehmen Sie die Änderungen an dieser Kopie vor.  
  
3.  Serialisieren Sie mithilfe einer der folgenden Optionen das bearbeitete Objekt wieder in den Datencache:  
  
    -   Wenn Sie die Änderungen automatisch serialisieren möchten, verwenden Sie die <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.SerializeDataInstance%2A>\-Methode.  Diese Methode verwendet das **DiffGram**\-Format, um <xref:System.Data.DataSet>, <xref:System.Data.DataTable> und typisierte DataSet\-Objekte in den Datencache zu serialisieren.  Durch das **DiffGram**\-Format wird sichergestellt, dass Änderungen am Datencache in einem Offlinedokument korrekt an den Server gesendet werden.  
  
    -   Wenn Sie eine eigene Serialisierung für Änderungen an zwischengespeicherten Daten durchführen möchten, können Sie direkt in die <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.Xml%2A>\-Eigenschaft schreiben.  Geben Sie das **DiffGram**\-Format an, wenn Sie einen <xref:System.Data.Common.DataAdapter> verwenden, um eine Datenbank mit Änderungen zu aktualisieren, die an Daten in einem <xref:System.Data.DataSet>, einer <xref:System.Data.DataTable> oder einem typisierten DataSet vorgenommen wurden.  Andernfalls aktualisiert der <xref:System.Data.Common.DataAdapter> die Datenbank, indem neue Zeilen hinzugefügt werden, statt vorhandene Zeilen zu ändern.  
  
### Ändern von Daten ohne Deserialisieren des aktuellen Werts  
 In einigen Fällen ist es zweckmäßig, den Wert des zwischengespeicherten Objekts zu ändern, ohne zuvor den aktuellen Wert zu deserialisieren.  Dies kann sinnvoll sein, wenn Sie den Wert eines Objekt ändern, das einem einfachen Typ angehört, z. B. eine Zeichenfolge oder eine Ganzzahl, oder wenn Sie ein zwischengespeichertes <xref:System.Data.DataSet> in einem Dokument auf einem Server initialisieren.  In diesen Fällen können Sie die <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.SerializeDataInstance%2A>\-Methode verwenden, ohne zuerst den aktuellen Wert des zwischengespeicherten Objekts zu deserialisieren.  
  
 Das folgende Codebeispiel veranschaulicht, wie Sie den Wert einer Zeichenfolge im Cache in der `Sheet1`\-Klasse eines Excel\-Arbeitsmappenprojekts ändern können.  Dieses Beispiel ist Teil eines umfangreicheren Beispiels für die <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.Save%2A>\-Methode.  
  
 [!code-csharp[Trin_ServerDocument#11](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ServerDocument/CS/Form1.cs#11)]
 [!code-vb[Trin_ServerDocument#11](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ServerDocument/VB/Form1.vb#11)]  
  
### Ändern von NULL\-Werten im Datencache  
 Im Datencache werden keine Objekte gespeichert, die beim Speichern und Schließen des Dokuments den Wert **null** haben.  Diese Einschränkung hat mehrere Folgen, wenn Sie zwischengespeicherte Daten ändern:  
  
-   Wenn Sie für ein Objekt im Datencache den Wert **null** festlegen, wird für alle Objekte im Datencache beim Öffnen des Dokuments automatisch der Wert **null** festgelegt, und der gesamte Datencache wird geleert, wenn das Dokument gespeichert und geschlossen wird.  Das bedeutet, dass alle zwischengespeicherten Objekte aus dem Datencache entfernt werden und die <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A>\-Auflistung leer ist.  
  
-   Wenn Sie eine Projektmappe mit **null**\-Objekten im Datencache erstellen und diese Objekte mithilfe der <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>\-Klasse initialisieren möchten, bevor das Dokument das erste Mal geöffnet wird, müssen Sie sicherstellen, dass Sie alle Objekte im Datencache initialisieren.  Wenn Sie nur einige der Objekte initialisieren, wird für alle Objekte im Datencache beim Öffnen des Dokuments der Wert **null** festgelegt, und der gesamte Datencache wird geleert, wenn das Dokument gespeichert und geschlossen wird.  
  
## Zugreifen auf typisierte DataSets im Cache  
 Wenn Sie auf die Daten in einem typisierten DataSet sowohl aus einer Office\-Lösung als auch einer Anwendung außerhalb von Office, z. B. einer Windows Forms\-Anwendung oder einem [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]\-Projekt, zugreifen möchten, müssen Sie das typisierte DataSet in einer separaten Assembly definieren, auf die in beiden Projekten verwiesen wird.  Wenn Sie beiden Projekten das typisierte DataSet mithilfe des **Assistenten zum Konfigurieren von Datenquellen** oder des **DataSet\-Designers** hinzufügen, behandelt .NET Framework die typisierten DataSets in beiden Projekten als unterschiedliche Typen.  Weitere Informationen über das Erstellen von typisierten DataSets finden Sie unter [Gewusst wie: Erstellen eines typisierten Datasets](../Topic/Creating%20and%20configuring%20datasets%20in%20Visual%20Studio.md).  
  
## Siehe auch  
 [Accessing Data in Documents on the Server](../vsto/accessing-data-in-documents-on-the-server.md)   
 [Zwischengespeicherte Daten in Anpassungen auf Dokumentebene](../vsto/cached-data-in-document-level-customizations.md)  
  
  
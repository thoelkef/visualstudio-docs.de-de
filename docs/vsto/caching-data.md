---
title: "Zwischenspeichern von Daten"
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
  - "Daten [Office-Entwicklung in Visual Studio], Zwischenspeichern"
  - "Zwischenspeichern von Daten [Office-Entwicklung in Visual Studio]"
  - "Zwischenspeichern von Daten [Office-Entwicklung in Visual Studio], Informationen zum Zwischenspeichern von Daten"
ms.assetid: 6f34251e-7d31-4f2b-ac17-42fd2837c626
caps.latest.revision: 36
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 35
---
# Zwischenspeichern von Daten
  Sie können Datenobjekte in einer Anpassung auf Dokumentebene zwischenspeichern, sodass Sie auf diese Daten zugreifen können, ohne online zu sein oder Microsoft Office Excel oder Microsoft Office Word zu starten.  Damit ein Objekt zwischengespeichert werden kann, muss es über einen Datentyp verfügen, der bestimmte Anforderungen erfüllt.  Viele allgemeine Datentypen in .NET Framework erfüllen diese Anforderungen, einschließlich <xref:System.String>, <xref:System.Data.DataSet> und <xref:System.Data.DataTable>.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Es gibt zwei Möglichkeiten, dem Datencache ein Objekt hinzuzufügen:  
  
-   Legen Sie das <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute>\-Attribut für die Objektdeklaration fest, um ein Objekt dem Datencache beim Erstellen der Projektmappe hinzuzufügen.  Weitere Informationen finden Sie unter [Gewusst wie: Zwischenspeichern von Daten zur Offlineverwendung oder zur Verwendung auf einem Server](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md).  
  
-   Verwenden Sie die `StartCaching`\-Methode eines Hostelements wie der `ThisDocument`\-Klasse oder der `ThisWorkbook`\-Klasse, um dem Datencache zur Laufzeit programmgesteuert ein Objekt hinzuzufügen.  Weitere Informationen finden Sie unter [Gewusst wie: Programmgesteuertes Zwischenspeichern von Datenquellen in einem Office-Dokument](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md).  
  
 Nachdem Sie dem Datencache ein Objekt hinzugefügt haben, können Sie auf die zwischengespeicherten Daten zugreifen und diese ändern, ohne Word oder Excel zu starten.  Weitere Informationen finden Sie unter [Zugreifen auf Daten in Dokumenten auf dem Server](../vsto/accessing-data-in-documents-on-the-server.md).  
  
## Anforderungen an Datenobjekte, die zwischengespeichert werden sollen  
 Um ein Datenobjekt in der Lösung zwischenzuspeichern, muss das Objekt die folgenden Anforderungen erfüllen:  
  
-   Es muss sich um ein öffentliches Feld oder eine öffentliche Eigenschaft eines Hostelements mit Lese\-\/Schreibzugriff handeln, beispielsweise die `ThisDocument`\-Klasse oder die `ThisWorkbook`\-Klasse.  
  
-   Es darf sich dabei nicht um einen Indexer oder eine andere parametrisierte Eigenschaft handeln.  
  
 Zudem muss das Datenobjekt durch die <xref:System.Xml.Serialization.XmlSerializer>\-Klasse serialisierbar sein. Der Typ des Objekts muss also folgende Eigenschaften aufweisen:  
  
-   Es muss sich um einen öffentlichen Typ handeln.  
  
-   Es muss über einen öffentlichen Konstruktor ohne Parameter verfügen.  
  
-   Es darf kein Code ausgeführt werden, der zusätzliche Sicherheitsberechtigungen erfordert.  
  
-   Es dürfen nur öffentliche Lese\-\/Schreibeigenschaften verfügbar gemacht werden \(andere Eigenschaften werden ignoriert\).  
  
-   Es dürfen keine mehrdimensionalen Arrays verfügbar gemacht werden \(geschachtelte Arrays sind zulässig\).  
  
-   Es dürfen keine Schnittstellen von Eigenschaften und Feldern zurückgegeben werden.  
  
-   <xref:System.Collections.IDictionary> darf nicht implementiert werden, wenn es sich um eine Auflistung handelt.  
  
 Wenn Sie ein Datenobjekt zwischenspeichern, serialisiert die [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] das Objekt in eine XML\-Zeichenfolge, die im Dokument in einem *benutzerdefinierten XML\-Abschnitt* gespeichert wird.  Weitere Informationen finden Sie unter [Übersicht über benutzerdefinierte XML-Abschnitte](../vsto/custom-xml-parts-overview.md).  
  
## Größenbeschränkungen für zwischengespeicherte Daten  
 Es gibt bestimmte Beschränkungen für die Gesamtmenge von Daten, die Sie dem Datencache in einem Dokument hinzufügen können, und für die Größe eines einzelnen Objekts im Datencache.  Wenn Sie diese Beschränkungen überschreiten, wird die Anwendung möglicherweise unerwartet geschlossen, wenn die Daten im Datencache gespeichert werden.  
  
 Um diese Beschränkungen zu vermeiden, befolgen Sie diese Richtlinien:  
  
-   Fügen Sie dem Datencache kein Objekt größer als 10 MB hinzu.  
  
-   Fügen Sie dem Datencache in einem einzelnen Dokument keine Datenmenge vom mehr als 100 MB hinzu.  
  
 Dies sind ungefähre Werte.  Die genauen Beschränkungen hängen von mehreren Faktoren ab, einschließlich des verfügbaren RAM und der Anzahl der laufenden Prozesse.  
  
## Steuern des Verhaltens zwischengespeicherter Objekte  
 Wenn Sie mehr Kontrolle über das Verhalten des zwischengespeicherten Objekts erhalten möchten, können Sie die <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType>\-Schnittstelle für den Typ des zwischengespeicherten Objekts implementieren.  Sie können diese Schnittstelle z. B. implementieren, um die Art der Benachrichtigung von Benutzern über Änderungen im Objekt zu steuern.  Codebeispiele, die veranschaulichen, wie <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> implementiert wird, finden Sie in der `ControlCollection`\-Klasse im Beispiel für dynamische Excel\-Steuerelemente und im Beispiel für dynamische Steuerelemente in Word unter [Beispiele und exemplarische Vorgehensweisen für die Programmierung mit Office](../vsto/office-development-samples-and-walkthroughs.md).  
  
## Beibehalten von Änderungen an zwischengespeicherten Daten in kennwortgeschützten Dokumenten  
 Wenn Sie Datenobjekte in einem kennwortgeschützten Dokument zwischenspeichern, werden Änderungen an den zwischengespeicherten Daten nicht gespeichert.  Sie können Änderungen an den zwischengespeicherten Daten speichern, indem Sie zwei Methoden überschreiben.  Überschreiben Sie diese Methoden, um den Schutz beim Speichern des Dokuments vorübergehend aufzuheben, und wenden Sie den Schutz nach Abschluss des Speichervorgangs wieder an.  
  
 Weitere Informationen finden Sie unter [Gewusst wie: Zwischenspeichern von Daten in einem kennwortgeschützten Dokument](../vsto/how-to-cache-data-in-a-password-protected-document.md).  
  
## Verhindern von Datenverlust beim Hinzufügen von NULL\-Werten zum Datencache  
 Wenn Sie dem Datencache Objekte hinzufügen, müssen vor dem Speichern und Schließen des Dokuments alle zwischengespeicherten Objekte mit einem von **null** verschiedenen Wert initialisiert werden.  Wenn ein zwischengespeichertes Objekt beim Speichern und Schließen des Dokuments den Wert **null** hat, werden alle zwischengespeicherten Elemente durch die [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] automatisch aus dem Datencache entfernt.  
  
 Wenn Sie dem Datencache zur Entwurfszeit mit dem <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute>\-Attribut ein Objekt mit dem Wert **null** hinzufügen, können Sie die zwischengespeicherten Datenobjekte mithilfe der <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>\-Klasse vor dem Öffnen des Dokuments initialisieren.  Dies ist hilfreich, wenn Sie die zwischengespeicherten Daten vor dem Öffnen durch den Endbenutzer auf einem Server initialisieren möchten, auf dem weder Word noch Excel installiert ist.  Weitere Informationen finden Sie unter [Zugreifen auf Daten in Dokumenten auf dem Server](../vsto/accessing-data-in-documents-on-the-server.md).  
  
## Siehe auch  
 [Gewusst wie: Zwischenspeichern von Daten zur Offlineverwendung oder zur Verwendung auf einem Server](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)   
 [Gewusst wie: Programmgesteuertes Zwischenspeichern von Datenquellen in einem Office-Dokument](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)   
 [Gewusst wie: Zwischenspeichern von Daten in einem kennwortgeschützten Dokument](../vsto/how-to-cache-data-in-a-password-protected-document.md)   
 [Exemplarische Vorgehensweise: Erstellen einer Master&#47;Detail-Beziehung mithilfe eines zwischengespeicherten Datasets](../vsto/walkthrough-creating-a-master-detail-relation-using-a-cached-dataset.md)  
  
  
---
title: Zwischenspeichern von Daten | Microsoft Docs
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data caching [Office development in Visual Studio], about caching data
- data [Office development in Visual Studio], caching
- data caching [Office development in Visual Studio]
ms.assetid: 6f34251e-7d31-4f2b-ac17-42fd2837c626
caps.latest.revision: "36"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0d5f044f1f1d0f36918939a67d9d2e5bb1899929
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="caching-data"></a>Zwischenspeichern von Daten
  Datenobjekte in einer Anpassung auf Dokumentebene können zwischengespeichert werden, sodass die Daten offline oder ohne Öffnen des Microsoft Office Word oder Microsoft Office Excel zugegriffen werden können. Zum Zwischenspeichern eines Objekts muss das Objekt einen Datentyp aufweisen, der bestimmte Anforderungen erfüllt. Viele allgemeine Datentypen in .NET Framework erfüllen diese Anforderungen, einschließlich <xref:System.String>, <xref:System.Data.DataSet>, und <xref:System.Data.DataTable>.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Es gibt zwei Möglichkeiten zum Hinzufügen eines Objekts für den Datencache:  
  
-   Zum Hinzufügen eines Objekts für den Datencache an, wenn die Projektmappe erstellt wird, gelten die <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> -Attribut auf die Deklaration des Objekts. Weitere Informationen finden Sie unter [Vorgehensweise: Zwischenspeichern von Daten für Offline verwenden oder auf einem Server](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md).  
  
-   Verwenden Sie zum programmgesteuerten Hinzufügen ein Objekts für den Datencache zur Laufzeit die `StartCaching` Methode von einem Host-Elements, z. B. die `ThisDocument` oder `ThisWorkbook` Klassen. Weitere Informationen finden Sie unter [wie: Programmgesteuertes Zwischenspeichern von Datenquellen in einem Office-Dokument](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md).  
  
 Nachdem Sie ein Objekt für den Datencache hinzugefügt haben, können Sie Zugriff auf und ändern die zwischengespeicherten Daten ohne Starten des Word- oder Excel. Weitere Informationen finden Sie unter [Accessing Data in Documents on the Server](../vsto/accessing-data-in-documents-on-the-server.md).  
  
## <a name="requirements-for-data-objects-to-be-cached"></a>Anforderungen für die Datenobjekte zwischengespeichert werden soll  
 Um ein Datenobjekt in der Projektmappe zwischenzuspeichern, muss das Objekt die folgenden Anforderungen erfüllen:  
  
-   Wie werden von öffentlichen Lese-/Schreibzugriff-Felds oder einer Eigenschaft eines Hostelements der `ThisDocument` oder `ThisWorkbook` Klassen.  
  
-   Werden Sie nicht nach einem Indexer oder andere parametrisierten Eigenschaft.  
  
 Darüber hinaus muss das Datenobjekt mit serialisierbar der <xref:System.Xml.Serialization.XmlSerializer> -Klasse, die den Typ des Objekts bedeutet muss diese Merkmale aufweisen:  
  
-   Ein öffentlicher Typ sein.  
  
-   Haben Sie einen öffentlichen Konstruktor ohne Parameter.  
  
-   Code, der zusätzliche Sicherheitsberechtigungen erfordert nicht ausgeführt werden.  
  
-   Verfügbar machen Sie nur Lese-/Schreibzugriff öffentlichen Eigenschaften (andere Eigenschaften werden ignoriert).  
  
-   Machen Sie mehrdimensionale Arrays (geschachtelte Arrays sind zulässig) nicht verfügbar.  
  
-   Schnittstellen von Eigenschaften und Felder zurückgegeben.  
  
-   Nicht implementiert <xref:System.Collections.IDictionary> Wenn eine Sammlung.  
  
 Wenn Sie ein Datenobjekt Zwischenspeichern der [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] serialisiert das Objekt in eine XML-Zeichenfolge, die in gespeichert ist ein *benutzerdefinierten XML-Abschnitt* im Dokument. Weitere Informationen finden Sie unter [Custom XML Parts Overview](../vsto/custom-xml-parts-overview.md).  
  
## <a name="cached-data-size-limits"></a>Größenbeschränkungen für zwischengespeicherte Daten  
 Es gibt einige Einschränkungen auf die Gesamtmenge der Daten, die Sie für den Datencache in einem Dokument, und klicken Sie auf die Größe jedes einzelnen Objekts im Datencache hinzufügen können. Wenn Sie diese Grenzwerte überschreiten, möglicherweise die Anwendung unerwartet beendet, wenn die Daten für den Datencache gespeichert werden.  
  
 Um diese Einschränkungen zu vermeiden, beachten Sie Folgendes:  
  
-   Fügen Sie für den Datencache keines Objekt größer als 10 MB.  
  
-   Fügen Sie für den Datencache in einem einzelnen Dokument nicht mehr als 100 MB an Daten insgesamt.  
  
 Hierbei handelt es sich um ungefähre Werte. Die genaue Grenzwerte richten sich nach mehreren Faktoren ab, einschließlich der verfügbare Arbeitsspeicher und der Anzahl der ausgeführten Prozesse.  
  
## <a name="controlling-the-behavior-of-cached-objects"></a>Steuern des Verhaltens von zwischengespeicherten Objekten  
 Um mehr Kontrolle über das Verhalten eines zwischengespeicherten Objekts zu erhalten, können Sie implementieren die <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> Schnittstelle für den Typ des zwischengespeicherten Objekts. Beispielsweise können Sie diese Schnittstelle implementieren, wenn Sie steuern möchten, wie Benutzer benachrichtigt wird, wenn das Objekt geändert wurde. Codebeispiele, die veranschaulichen, wie implementiert <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType>, finden Sie unter der `ControlCollection` Klasse im Beispiel für dynamische Steuerelemente in Word und Excel-Beispiel für dynamische Steuerelemente [Office Development Samples and Walkthroughs](../vsto/office-development-samples-and-walkthroughs.md).  
  
## <a name="persisting-changes-to-cached-data-in-password-protected-documents"></a>Beibehalten von Änderungen an der zwischengespeicherten Daten in Dokumenten kennwortgeschützte  
 Wenn Sie Datenobjekte in einem Dokument, die mit einem Kennwort geschützt ist zwischenspeichern, werden Änderungen an den zwischengespeicherten Daten nicht gespeichert. Überschreiben von zwei Methoden, um Änderungen auf die zwischengespeicherten Daten zu speichern. Überschreiben Sie diese Methoden, um den Schutz vorübergehend zu entfernen, wenn das Dokument gespeichert wird, und wenden Sie den Schutz nach dem Speichern erneut abgeschlossen ist.  
  
 Weitere Informationen finden Sie unter [Vorgehensweise: Zwischenspeichern von Daten in einem Dokument Password-Protected](../vsto/how-to-cache-data-in-a-password-protected-document.md).  
  
## <a name="preventing-data-loss-when-adding-null-values-to-the-data-cache"></a>Verhinderung von Datenverlust beim Hinzufügen von Null-Werte für den Datencache  
 Wenn Sie für den Datencache Objekte hinzufügen, müssen alle zwischengespeicherten Objekte nicht initialisiert werden**null** -Wert vor das Dokument gespeichert und geschlossen wird. Wenn ein zwischengespeichertes Objekt verfügt über eine **null** Wert, wenn das Dokument gespeichert und geschlossen, die [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] entfernt alle zwischengespeicherten Objekte automatisch aus dem Datencache.  
  
 Wenn Sie ein Objekt mit Hinzufügen einer **null** Wert für den Datencache mithilfe der <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> Attribut zur Entwurfszeit können Sie die <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> Klasse initialisiert werden, die zwischengespeicherten Daten Objekte, bevor das Dokument geöffnet wird. Dies ist hilfreich, wenn Sie die zwischengespeicherten Daten auf einem Server ohne Word- oder Excel installiert haben, bevor das Dokument, von einem Endbenutzer geöffnet wird initialisieren möchten. Weitere Informationen finden Sie unter [Accessing Data in Documents on the Server](../vsto/accessing-data-in-documents-on-the-server.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Zwischenspeichern von Daten für die Verwendung Offline ist oder auf einem Server](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)   
 [Vorgehensweise: Programmgesteuertes Zwischenspeichern von Datenquellen in einem Office-Dokument](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)   
 [Vorgehensweise: Zwischenspeichern von Daten in einem kennwortgeschützten Dokument](../vsto/how-to-cache-data-in-a-password-protected-document.md)   
 [Exemplarische Vorgehensweise: Erstellen einer Master-Detail-Beziehung mithilfe eines zwischengespeicherten Datasets](../vsto/walkthrough-creating-a-master-detail-relation-using-a-cached-dataset.md)  
  
  
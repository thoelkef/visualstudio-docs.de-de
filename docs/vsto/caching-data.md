---
title: Zwischenspeichern von Daten
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data caching [Office development in Visual Studio], about caching data
- data [Office development in Visual Studio], caching
- data caching [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: b46fa8b0138eff03757a7bd7828053cee039090f
ms.sourcegitcommit: 20c0991d737c540750c613c380cd4cf5bb07de51
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "53248118"
---
# <a name="cache-data"></a>Zwischenspeichern von Daten
  Datenobjekte in einer Anpassung auf Dokumentebene können zwischengespeichert werden, damit die Daten offline oder ohne Öffnen Microsoft Office Word oder Microsoft Office Excel zugegriffen werden können. Zum Zwischenspeichern eines Objekts, muss das Objekt über einen Datentyp aufweisen, der bestimmte Anforderungen erfüllt. Viele allgemeine Datentypen in .NET Framework erfüllen diese Anforderungen, einschließlich der <xref:System.String>, <xref:System.Data.DataSet>, und <xref:System.Data.DataTable>.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Es gibt zwei Möglichkeiten, ein Objekt, das dem Datencache hinzuzufügen:  
  
- Um ein Objekt, das dem Datencache hinzuzufügen, wenn die Projektmappe erstellt wird, gelten die <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> -Attribut auf die Deklaration des Objekts. Weitere Informationen finden Sie unter [Vorgehensweise: Zwischenspeichern von Daten für die Verwendung, offline ist oder auf einem Server](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md).  
  
- Verwenden Sie zum programmgesteuerten Hinzufügen ein Objekts, das dem Datencache zur Laufzeit die `StartCaching` Methode von einem Host-Elements, z. B. die `ThisDocument` oder `ThisWorkbook` Klassen. Weitere Informationen finden Sie unter [Vorgehensweise: Programmgesteuertes Zwischenspeichern von Datenquellen in einem Office-Dokument](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md).  
  
  Nachdem Sie ein Objekt, das dem Datencache hinzugefügt haben, können Sie Zugriff auf und ändern die zwischengespeicherten Daten ohne Starten des Word- oder Excel. Weitere Informationen finden Sie unter [Zugriff auf Daten in Dokumenten auf dem Server](../vsto/accessing-data-in-documents-on-the-server.md).  
  
## <a name="requirements-for-data-objects-to-be-cached"></a>Anforderungen für Datenobjekte, die zwischengespeichert werden  
 Um ein Datenobjekt in der Projektmappe zwischenzuspeichern, muss das Objekt die folgenden Anforderungen erfüllen:  
  
- Ein öffentliches Feld Lese-/Schreibzugriff oder-Eigenschaft eines Hostelements, z. B. werden die `ThisDocument` oder `ThisWorkbook` Klassen.  
  
- Nicht, einen Indexer oder andere parametrisierten Eigenschaft.  
  
  Darüber hinaus das Datenobjekt, das von serialisierbar sein muss die <xref:System.Xml.Serialization.XmlSerializer> -Klasse, die bedeutet, den Typ des Objekts dass muss diese Merkmale aufweisen:  
  
- Ein öffentlicher Typ sein.  
  
- Haben Sie einen öffentlichen Konstruktor ohne Parameter.  
  
- Code, der erfordert zusätzliche Sicherheitsberechtigungen nicht ausgeführt werden.  
  
- Machen Sie nur lesend und schreibend öffentlichen Eigenschaften (andere Eigenschaften werden ignoriert).  
  
- Machen Sie mehrdimensionale Arrays (geschachtelte Arrays werden akzeptiert) nicht verfügbar.  
  
- Schnittstellen von Eigenschaften und Felder zurückgegeben.  
  
- Nicht implementiert <xref:System.Collections.IDictionary> Wenn eine Sammlung.  
  
  Wenn Sie ein Datenobjekt Zwischenspeichern der [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] serialisiert das Objekt in eine XML-Zeichenfolge, die in gespeichert ist eine *benutzerdefinierte XML-Element* im Dokument. Weitere Informationen finden Sie unter [Übersicht über die benutzerdefinierte XML-Abschnitte](../vsto/custom-xml-parts-overview.md).  
  
## <a name="cached-data-size-limits"></a>Grenzwerte für die zwischengespeicherten Daten  
 Es gibt einige Einschränkungen auf die Gesamtmenge der Daten an, das dem Datencache in einem Dokument, und klicken Sie auf die Größe jedes einzelnen Objekts im Datencache hinzugefügt werden können. Wenn Sie diese Grenzwerte überschreiten, kann die Anwendung unerwartet beendet, wenn die Daten in Datencache gespeichert werden.  
  
 Um diese Einschränkungen zu vermeiden, führen Sie die folgenden Richtlinien:  
  
- Fügen Sie ein Objekt größer als 10 MB nicht, das dem Datencache.  
  
- Fügen Sie dem Datencache in einem einzelnen Dokument nicht mehr als 100 MB insgesamt.  
  
  Hierbei handelt es sich um ungefähre Werte. Die genaue Grenzwerte hängen von verschiedenen Faktoren wie der verfügbare Arbeitsspeicher und die Anzahl der ausgeführten Prozesse ab.  
  
## <a name="control-the-behavior-of-cached-objects"></a>Kontrollieren des Verhaltens von zwischengespeicherten Objekten  
 Um mehr Kontrolle über das Verhalten eines zwischengespeicherten Objekts zu erhalten, können Sie implementieren die <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> Schnittstelle für den Typ des zwischengespeicherten Objekts. Beispielsweise können Sie diese Schnittstelle implementieren, wenn Sie steuern möchten, wie der Benutzer benachrichtigt wird, wenn das Objekt geändert wurde. Codebeispiele, die veranschaulichen, wie Sie implementieren <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType>, finden Sie unter den `ControlCollection` Klasse im Beispiel für dynamische Steuerelemente in Word und Excel-Beispiel für dynamische Steuerelemente [Office-Entwicklungsbeispiele und exemplarische Vorgehensweisen](../vsto/office-development-samples-and-walkthroughs.md).  
  
## <a name="persist-changes-to-cached-data-in-password-protected-documents"></a>Beibehalten von Änderungen an der zwischengespeicherten Daten in Dokumenten kennwortgeschützte  
 Wenn Sie Datenobjekte in einem Dokument, die mit einem Kennwort geschützt ist zwischenspeichern, werden Änderungen an den zwischengespeicherten Daten nicht gespeichert werden. Sie können Änderungen an den zwischengespeicherten Daten speichern, durch zwei Methoden überschreiben. Überschreiben Sie diese Methoden, um den Schutz vorübergehend zu entfernen, wenn das Dokument gespeichert wird, und wenden Sie erneut den Schutz nach dem Speichern an Vorgang abgeschlossen ist.  
  
 Weitere Informationen finden Sie unter [Vorgehensweise: Zwischenspeichern von Daten in einem kennwortgeschützten Dokument](../vsto/how-to-cache-data-in-a-password-protected-document.md).  
  
## <a name="prevent-data-loss-when-adding-null-values-to-the-data-cache"></a>Verhindern von Datenverlust, wenn null-Werte, das dem Datencache hinzugefügt.  
 Wenn Sie Objekte, das dem Datencache hinzufügen, müssen alle zwischengespeicherten Objekte nicht initialisiert werden**null** -Wert vor das Dokument gespeichert und geschlossen wird. Wenn ein zwischengespeichertes Objekt verfügt über eine **null** Wert, wenn das Dokument gespeichert und geschlossen wird, die [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] entfernt alle zwischengespeicherten Objekte automatisch aus dem Datencache.  
  
 Wenn Sie ein Objekt mit Hinzufügen einer **null** Wert für den Datencache mithilfe der <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> Attribut zur Entwurfszeit können Sie die <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> Klasse, um die zwischengespeicherten Daten zu Objekten, bevor das Dokument geöffnet wird. Dies ist hilfreich, wenn Sie die zwischengespeicherten Daten auf einem Server ohne Word- oder Excel installiert haben, bevor das Dokument, von einem Endbenutzer geöffnet wird initialisieren möchten. Weitere Informationen finden Sie unter [Zugriff auf Daten in Dokumenten auf dem Server](../vsto/accessing-data-in-documents-on-the-server.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Zwischenspeichern von Daten für die Verwendung, offline ist oder auf einem server](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)   
 [Vorgehensweise: Programmgesteuertes Zwischenspeichern von Datenquellen in einem Office-Dokument](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)   
 [Vorgehensweise: Zwischenspeichern von Daten in einem kennwortgeschützten Dokument](../vsto/how-to-cache-data-in-a-password-protected-document.md)   
 [Exemplarische Vorgehensweise: Erstellen Sie eine master-Detail-Beziehung mithilfe eines zwischengespeicherten Datasets](../vsto/walkthrough-creating-a-master-detail-relation-using-a-cached-dataset.md)  
  
  
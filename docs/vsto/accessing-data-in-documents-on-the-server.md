---
title: Zugreifen auf Daten in Dokumenten auf dem server
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Office development in Visual Studio], accessing on server
- data access [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 70c00a9c0de4afd9f54062e1c2ffabcc2911a538
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/26/2018
ms.locfileid: "52305571"
---
# <a name="access-data-in-documents-on-the-server"></a>Zugreifen auf Daten in Dokumenten auf dem server
  Sie können die Daten in einer Anpassung auf Dokumentebene programmieren, ohne das Objektmodell von Microsoft Office Word oder Microsoft Office Excel verwenden. Dies bedeutet, Sie können Daten in einem Dokument auf einem Server, die nicht Word oder Excel installiert. Code wird z. B. auf einem Server (beispielsweise eine [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] Seite) die Daten in einem Dokument angepasst und angepasste Dokument kann an einen Endbenutzer gesendet. Wenn der Endbenutzer das Dokument öffnet, bindet Datenbindungscode in die Projektmappenassembly benutzerdefinierten Daten in das Dokument. Dies ist möglich, da die Daten im Dokument von der Benutzeroberfläche getrennt sind. Weitere Informationen finden Sie unter [zwischengespeicherten Daten in Anpassungen auf Dokumentebene](../vsto/cached-data-in-document-level-customizations.md).  

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  

## <a name="cache-data-for-use-on-a-server"></a>Daten Sie für die Verwendung auf einem server  
 Um ein Datenobjekt in einem Dokument zwischenspeichern, kennzeichnen Sie ihn mit der <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> -Attribut zur Entwurfszeit, oder verwenden Sie die `StartCaching` -Methode eines Hostelements zur Laufzeit. Wenn Sie ein Objekt in einem Dokument Zwischenspeichern der [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] serialisiert das Objekt in eine XML-Zeichenfolge, die im Dokument gespeichert ist. Objekte müssen Anforderungen für Zwischenspeichern. Weitere Informationen finden Sie unter [Zwischenspeichern von Daten](../vsto/caching-data.md).  

 Serverseitigen Code kann alle Datenobjekte im Datencache bearbeitet werden. Instanzen von zwischengespeicherten Daten gebundenen Steuerelemente sind mit der Benutzeroberfläche synchronisiert serverseitige Änderungen an den Daten werden automatisch angezeigt, wenn auf dem Client öffnen.  

## <a name="access-data-in-the-cache"></a>Zugriff auf Daten im cache  
 Sie können Clientanwendungen Office, z. B. eine Windows Forms-Anwendung oder eine Webseite im Cache zugreifen. Die Anwendung, die zwischengespeicherten Daten zugreift, muss vollständig vertrauenswürdig sein; eine Web-Anwendung mit teilweiser Vertrauenswürdigkeit kann einfügen, Abrufen oder Ändern von Daten in einem Office-Dokument zwischengespeichert.  

 Datencache ist eine Hierarchie von Sammlungen von verfügbar gemacht über die <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> -Eigenschaft des der <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> Klasse:  

- Die <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> gibt eine <xref:Microsoft.VisualStudio.Tools.Applications.CachedData>, enthält alle zwischengespeicherten Daten in einer Anpassung auf Dokumentebene.  

- Jede <xref:Microsoft.VisualStudio.Tools.Applications.CachedData> enthält eine oder mehrere <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem> Objekte. Ein <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem> enthält alle zwischengespeicherten Datenobjekte, die innerhalb einer einzelnen Klasse definiert sind.  

- Jede <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem> enthält eine oder mehrere <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> Objekte. Eine <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> stellt ein einzelnes zwischengespeichertes Datenobjekt.  

  Im folgenden Codebeispiel wird veranschaulicht, wie auf eine zwischengespeicherte Zeichenfolge in der `Sheet1` -Klasse ein Excel-Arbeitsmappenprojekt. Dieses Beispiel ist Teil eines umfangreicheren Beispiels für die <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.Save%2A> Methode.  

  [!code-csharp[Trin_ServerDocument#12](../vsto/codesnippet/CSharp/Trin_ServerDocument/Form1.cs#12)]
  [!code-vb[Trin_ServerDocument#12](../vsto/codesnippet/VisualBasic/Trin_ServerDocument/Form1.vb#12)]  

## <a name="modify-data-in-the-cache"></a>Ändern von Daten im cache  
 Ändern Sie ein zwischengespeichertes Datenobjekt führen Sie normalerweise die folgenden Schritte aus:  

1.  Die XML-Darstellung des zwischengespeicherten Objekts in eine neue Instanz des Objekts zu deserialisieren. Zugriff XML mithilfe der <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.Xml%2A> -Eigenschaft des der <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> , der das zwischengespeicherte Objekt darstellt.  

2.  Ändern Sie diese Kopie.  

3.  Zum Serialisieren des bearbeiteten Objekts in den Datencache mithilfe einer der folgenden Optionen:  

    -   Die Änderung automatisch serialisiert, verwenden Sie die <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.SerializeDataInstance%2A> Methode. Diese Methode verwendet die **DiffGram** Format für die Serialisierung <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, und typisierte Dataset-Objekte in den Datencache. Die **DiffGram** wird sichergestellt, dass dem Datencache in einem Dokument offline geändert korrekt an den Server gesendet werden.  

    -   Wenn Sie eigene Serialisierung Änderungen zwischengespeicherten Daten ausführen möchten, können Sie direkt zu schreiben die <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.Xml%2A> Eigenschaft. Angeben der **DiffGram** format verwenden Sie ein <xref:System.Data.Common.DataAdapter> zum Aktualisieren einer Datenbank mit Daten in einem <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, oder einem typisierten Dataset. Andernfalls die <xref:System.Data.Common.DataAdapter> Aktualisieren der Datenbank durch Hinzufügen neuer Zeilen statt vorhandene Zeilen zu ändern.  

### <a name="modify-data-without-deserializing-the-current-value"></a>Ändern von Daten ohne Deserialisieren des aktuellen Werts  
 In einigen Fällen möchten Sie den Wert des zwischengespeicherten Objekts zu ändern, ohne die erste Deserialisieren des aktuellen Werts. Beispielsweise kann dies, wenn Sie den Wert eines Objekts ändern, das einen einfachen Typ, z. B. eine Zeichenfolge oder eine Ganzzahl, oder beim Initialisieren von zwischengespeicherten <xref:System.Data.DataSet> in einem Dokument auf einem Server. In diesen Fällen können Sie die <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.SerializeDataInstance%2A> -Methode ohne Deserialisieren von den aktuellen Wert des zwischengespeicherten Objekts.  

 Im folgenden Codebeispiel wird veranschaulicht, wie der Wert eine zwischengespeicherte Zeichenfolge in der `Sheet1` -Klasse ein Excel-Arbeitsmappenprojekt. Dieses Beispiel ist Teil eines umfangreicheren Beispiels für die <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.Save%2A> Methode.  

 [!code-csharp[Trin_ServerDocument#11](../vsto/codesnippet/CSharp/Trin_ServerDocument/Form1.cs#11)]
 [!code-vb[Trin_ServerDocument#11](../vsto/codesnippet/VisualBasic/Trin_ServerDocument/Form1.vb#11)]  

### <a name="modify-null-values-in-the-data-cache"></a>Ändern von null-Werten im Datencache  
 Der Datencache werden keine Objekte mit dem Wert gespeichert **null** Wenn das Dokument gespeichert und geschlossen. Diese Einschränkung hat mehrere folgen, wenn Sie zwischengespeicherte Daten ändern:  

-   Setzen Sie ein Objekt im Datencache den Wert **null**, alle Objekte im Datencache automatisch soll **null** beim Öffnen des Dokuments und der gesamte Datencache wird gelöscht, wenn die Dokument gespeichert und geschlossen. Das heißt, entfernt alle zwischengespeicherten Objekte aus dem Datencache und <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> Auflistung leer sein.  

-   Wenn Sie eine Projektmappe mit **null** Objekte in den Datencache erstellen und diese Objekte mithilfe von initialisieren möchten die <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> Klasse, bevor das Dokument zum ersten Mal geöffnet wird, müssen Sie sicherstellen, dass alle Objekte initialisieren im Datencache. Wenn nur einige der Objekte initialisieren aller Objekte festzulegen **null** beim Öffnen des Dokuments und der gesamte Datencache wird geleert, wenn das Dokument gespeichert und geschlossen wird.  

## <a name="access-typed-datasets-in-the-cache"></a>Zugriff auf typisierte Datasets im cache  
 Möchten Sie die Daten in einem typisierten Dataset sowohl aus einer Office-Projektmappe eine Anwendung außerhalb von Office, wie Windows Forms-Anwendung zugreifen oder ein [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] Projekt, Sie definieren das typisierte Dataset in einer separaten Assembly sowohl verwiesen wird Projekte. Wenn Sie das Dataset mit Hinzufügen der **Datenquellenkonfiguration** Assistenten oder **Dataset-Designer**, behandelt.NET Framework die typisierten Datasets in beiden Projekten als unterschiedliche Typen . Weitere Informationen zum Erstellen von typisierten Datasets finden Sie unter [erstellen und Konfigurieren von Datasets in Visual Studio](/visualstudio/data-tools/create-and-configure-datasets-in-visual-studio).  

## <a name="see-also"></a>Siehe auch  
 [Zugreifen auf Daten in Dokumenten auf dem server](../vsto/accessing-data-in-documents-on-the-server.md)   
 [Zwischengespeicherte Daten in Anpassungen auf Dokumentebene](../vsto/cached-data-in-document-level-customizations.md)  

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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ecfebda02096d1a36a5de84919aad65482a25ec0
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
ms.locfileid: "34268376"
---
# <a name="access-data-in-documents-on-the-server"></a>Zugreifen auf Daten in Dokumenten auf dem server
  Sie können die Daten in einer Anpassung auf Dokumentebene programmieren, ohne das Objektmodell der Microsoft Office Word oder Microsoft Office Excel verwenden. Dies bedeutet, dass Sie erreichen die Daten, die in einem Dokument auf einem Server befindet, die über keinen Word oder Excel installiert. Code beispielsweise auf einem Server (z. B. in einer [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] Seite ") können die Daten in einem Dokument anpassen und angepasste Dokument an Endbenutzer gesendet. Wenn der Endbenutzer das Dokument geöffnet wird, bindet Datenbindungscode in die Projektmappenassembly angepassten Daten in das Dokument. Dies ist möglich, da die Daten im Dokument über die Benutzeroberfläche getrennt ist. Weitere Informationen finden Sie unter [zwischengespeicherten Daten in Anpassungen auf Dokumentebene](../vsto/cached-data-in-document-level-customizations.md).  

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  

## <a name="cache-data-for-use-on-a-server"></a>Zwischenspeichern von Daten für die Verwendung auf einem server  
 Um ein Datenobjekt in einem Dokument zwischenspeichern möchten, markieren Sie es mit der <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> -Attributs zur Entwurfszeit aus, oder verwenden Sie die `StartCaching` Methode eines Hostelements zur Laufzeit. Wenn Sie ein Datenobjekt in einem Dokument Zwischenspeichern der [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] serialisiert das Objekt in eine XML-Zeichenfolge, die im Dokument gespeichert wird. Objekte müssen bestimmte Anforderungen für das caching geeignet sein. Weitere Informationen finden Sie unter [Zwischenspeichern von Daten](../vsto/caching-data.md).  

 Serverseitiger Code kann alle Datenobjekte im Datencache bearbeiten. Steuerelemente, die auf Instanzen der zwischengespeicherten Daten gebunden sind werden mit der Benutzeroberfläche synchronisiert, sodass sich alle serverseitigen Änderungen, die an den Daten vorgenommen werden automatisch angezeigt werden, wenn auf dem Client das Dokument geöffnet wird.  

## <a name="access-data-in-the-cache"></a>Zugreifen auf Daten im cache  
 Sie können Daten im Cache von Programmen außerhalb von Office, z. B. von einer Konsolenanwendung, ein Windows Forms-Anwendung oder eine Webseite zugreifen. Die Anwendung, die die zwischengespeicherten Daten zugreift, muss volle Vertrauenswürdigkeit verfügen. eine Webanwendung, die teilweise Vertrauenswürdigkeit verfügt kann nicht einfügen, Abrufen oder Ändern von Daten, die in einem Office-Dokument zwischengespeichert werden.  

 Der Datencache Zugriff erfolgt über eine Hierarchie von Auflistungen, die von verfügbar gemacht werden die <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> Eigenschaft von der <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> Klasse:  

-   Die <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> -Eigenschaft gibt ein <xref:Microsoft.VisualStudio.Tools.Applications.CachedData>, der alle zwischengespeicherten Daten in einer Anpassung auf Dokumentebene enthält.  

-   Jede <xref:Microsoft.VisualStudio.Tools.Applications.CachedData> enthält ein oder mehrere <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem> Objekte. Ein <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem> enthält alle zwischengespeicherten Datenobjekte, die innerhalb einer einzelnen Klasse definiert sind.  

-   Jede <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem> enthält ein oder mehrere <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> Objekte. Ein <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> stellt ein Objekt für die einzelnen zwischengespeicherten Daten dar.  

 Im folgenden Codebeispiel wird veranschaulicht, wie eine zwischengespeicherte Zeichenfolge in den Zugriff auf die `Sheet1` -Klasse eines Excel-Arbeitsmappenprojekts. In diesem Beispiel ist Teil eines umfangreicheren Beispiels, die aus Gründen der <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.Save%2A> Methode.  

 [!code-csharp[Trin_ServerDocument#12](../vsto/codesnippet/CSharp/Trin_ServerDocument/Form1.cs#12)]
 [!code-vb[Trin_ServerDocument#12](../vsto/codesnippet/VisualBasic/Trin_ServerDocument/Form1.vb#12)]  

## <a name="modify-data-in-the-cache"></a>Ändern von Daten im cache  
 Um ein Objekt zwischengespeicherten Daten zu ändern, führen Sie in der Regel die folgenden Schritte aus:  

1.  Deserialisieren Sie die XML-Darstellung des zwischengespeicherten Objekts in eine neue Instanz des Objekts. Sie erreichen den XML-Code mithilfe der <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.Xml%2A> Eigenschaft von der <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> , die das zwischengespeicherte Objekt darstellt.  

2.  Nehmen Sie die Änderungen an dieser Kopie.  

3.  Serialisieren Sie das geänderte Objekt wieder in den Datencache mithilfe einer der folgenden Optionen:  

    -   Wenn Sie die Änderungen automatisch serialisieren möchten, verwenden die <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.SerializeDataInstance%2A> Methode. Diese Methode verwendet die **DiffGram** Format für die Serialisierung <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, und das typisierte Dataset-Objekte im Datencache. Die **DiffGram** Format wird sichergestellt, dass die Änderungen für den Datencache in einem offline-Dokument ordnungsgemäß an den Server gesendet werden.  

    -   Wenn Sie eine eigene Serialisierung für Änderungen an den zwischengespeicherten Daten ausführen möchten, können Sie direkt zu schreiben die <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.Xml%2A> Eigenschaft. Angeben der **DiffGram** format bei Verwendung einer <xref:System.Data.Common.DataAdapter> zum Aktualisieren einer Datenbank mit Änderungen an Daten in eine <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, oder des typisierten Datasets. Andernfalls die <xref:System.Data.Common.DataAdapter> wird die Datenbank durch Hinzufügen neuer Zeilen anstelle der vorhandene Zeilen ändern, aktualisiert.  

### <a name="modify-data-without-deserializing-the-current-value"></a>Ändern von Daten ohne Deserialisierung des aktuellen Werts  
 In einigen Fällen empfiehlt es sich um den Wert des zwischengespeicherten Objekts zu ändern, ohne Deserialisieren von den aktuellen Wert. Angenommen, Sie erreichen dies, wenn Sie den Wert eines Objekts ändern, die einen einfachen Typ, z. B. eine Zeichenfolge oder eine ganze Zahl ist, oder wenn Sie eine zwischengespeicherte initialisieren <xref:System.Data.DataSet> in einem Dokument auf einem Server. In diesen Fällen können Sie die <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.SerializeDataInstance%2A> Methode ohne Deserialisieren von den aktuellen Wert des zwischengespeicherten Objekts.  

 Im folgenden Codebeispiel wird veranschaulicht, wie zum Ändern des Werts einer zwischengespeicherten Zeichenfolge in die `Sheet1` -Klasse eines Excel-Arbeitsmappenprojekts. In diesem Beispiel ist Teil eines umfangreicheren Beispiels, die aus Gründen der <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.Save%2A> Methode.  

 [!code-csharp[Trin_ServerDocument#11](../vsto/codesnippet/CSharp/Trin_ServerDocument/Form1.cs#11)]
 [!code-vb[Trin_ServerDocument#11](../vsto/codesnippet/VisualBasic/Trin_ServerDocument/Form1.vb#11)]  

### <a name="modify-null-values-in-the-data-cache"></a>Ändern der null-Werte im Datencache  
 Der Datencache speichert keine Objekte mit dem Wert **null** Wenn das Dokument gespeichert und geschlossen wird. Diese Einschränkung hat mehrere folgen, wenn Sie die zwischengespeicherte Daten ändern:  

-   Wenn Sie ein Objekt im Datencache auf den Wert festlegen **null**, alle Objekte im Datencache automatisch festgelegt, um **null** beim Öffnen des Dokuments und der gesamte Datencache werden gelöscht, wenn die Dokument gespeichert und geschlossen. D. h. entfernt alle zwischengespeicherten Objekte aus dem Datencache und <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> Auflistung leer sein wird.  

-   Wenn Sie eine Projektmappe mit **null** Objekte im Datencache, und Sie diese Objekte mit initialisiert werden soll die <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> Klasse, bevor das Dokument zum ersten Mal geöffnet wird, müssen Sie sicherstellen, dass Sie alle Objekte initialisiert werden im Datencache. Wenn Sie nur einige der Objekte zu initialisieren, alle Objekte auf festgelegt **null** beim Öffnen des Dokuments und der gesamte Datencache wird gelöscht, wenn das Dokument gespeichert und geschlossen wird.  

## <a name="access-typed-datasets-in-the-cache"></a>Zugriff von typisierten Datasets im cache  
 Wenn Sie die Daten in ein typisiertes Dataset aus einer Office-Projektmappe und aus einer Anwendung außerhalb von Office, z. B. eine Windows Forms-Anwendung zugreifen möchten oder eine [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] -Projekt müssen Sie das typisierte Dataset definieren, in einer separaten Assembly, die in beiden verwiesen wird Projekte. Wenn Sie jedes Projekt mit das typisierte Dataset Hinzufügen der **Datenquellenkonfiguration** Assistenten oder die **Dataset-Designer**, behandelt die .NET Framework die typisierten Datasets in beiden Projekten als unterschiedliche Typen . Weitere Informationen zum Erstellen von typisierten Datasets finden Sie unter [erstellen und Konfigurieren von Datasets in Visual Studio](/visualstudio/data-tools/create-and-configure-datasets-in-visual-studio).  

## <a name="see-also"></a>Siehe auch  
 [Zugreifen auf Daten in Dokumenten auf dem server](../vsto/accessing-data-in-documents-on-the-server.md)   
 [Zwischengespeicherte Daten in Anpassungen auf Dokumentebene](../vsto/cached-data-in-document-level-customizations.md)  

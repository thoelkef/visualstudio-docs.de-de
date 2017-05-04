---
title: "Gewusst wie: Zwischenspeichern von Daten zur Offlineverwendung oder zur Verwendung auf einem Server | Microsoft Docs"
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
  - "Zwischenspeichern von Daten [Office-Entwicklung in Visual Studio], Offlineverwendung"
  - "Zwischenspeichern von Daten [Office-Entwicklung in Visual Studio], Serververwendung"
  - "Datasets [Office-Entwicklung in Visual Studio], Zwischenspeichern"
  - "Office-Anwendungen [Office-Entwicklung in Visual Studio], Daten"
  - "Offlinedaten [Office-Entwicklung in Visual Studio]"
ms.assetid: 6246b187-9413-4336-821d-2259b1adec5a
caps.latest.revision: 49
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 48
---
# Gewusst wie: Zwischenspeichern von Daten zur Offlineverwendung oder zur Verwendung auf einem Server
  Sie können in einem Dokument ein Datenelement für die Zwischenspeicherung kennzeichnen, um es offline verfügbar zu machen.  Dabei können die in dem Dokument enthaltenen Daten durch anderen Code geändert werden, falls das Dokument auf einem Server gespeichert wird.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Sie können ein Datenelement entweder bei der Deklaration für die Zwischenspeicherung kennzeichnen oder – wenn Sie <xref:System.Data.DataSet> verwenden – im  Eigenschaftenfenster die Eigenschaft entsprechend festlegen.  Wenn Sie ein Datenelement zwischenspeichern, dass weder ein <xref:System.Data.DataSet> noch eine <xref:System.Data.DataTable> ist, müssen Sie sicherstellen, dass das Datenelement die Bedingungen für eine Zwischenspeicherung im Dokument erfüllt.  Weitere Informationen finden Sie unter [Zwischenspeichern von Daten](../vsto/caching-data.md).  
  
> [!NOTE]  
>  Datasets, die unter Verwendung von Visual Basic erstellt wurden und als **Cached** und **WithEvents** gekennzeichnet sind \(einschließlich Datasets, die aus dem **Datenquellenfenster** oder aus der **Toolbox** gezogen wurden und deren **CacheInDocument**\-Eigenschaft auf **True** festgelegt wurde\), werden mit einem dem Namen vorangestellten Unterstrich im Cache gespeichert.  Wenn Sie beispielsweise ein DataSet mit dem Namen "Kunden" erstellen, lautet der <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem>\-Name im Cache "\_Kunden".  Wenn Sie <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> für den Zugriff auf dieses zwischengespeicherte Element verwenden, müssen Sie "\_Kunden" anstelle von "Kunden" angeben.  
  
### So können Sie Daten im Dokument unter Verwendung von Code zwischenspeichern  
  
1.  Deklarieren Sie ein öffentliches Feld oder eine öffentliche Eigenschaft für das Datenelement als Member einer Hostelementklasse im Projekt, z. B. als `ThisDocumen`t\-Klasse in einem Word\-Projekt oder als `ThisWorkbook`\-Klasse in einem Excel\-Projekt.  
  
2.  Wenden Sie das <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute>\-Attribut auf den Member an, um das Datenelement für das Speichern im Datencache des Dokuments zu markieren.  Im folgenden Beispiel wird dieses Attribut auf eine Felddeklaration für ein <xref:System.Data.DataSet> angewendet.  
  
     [!code-csharp[Trin_VstcoreDataExcel#11](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#11)]
     [!code-vb[Trin_VstcoreDataExcel#11](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#11)]  
  
3.  Fügen Sie Code hinzu, um eine Instanz des Datenelements zu erstellen und es gegebenenfalls aus der Datenbank zu laden.  
  
     Das Datenelement wird nur bei der Erstellung geladen. Der Cache und damit auch das Dokument bleiben erhalten, und Sie müssen weiteren Code schreiben, um den Cache zu aktualisieren.  
  
### So können Sie ein DataSet im Dokument unter Verwendung des Eigenschaftenfensters zwischenspeichern  
  
1.  Fügen Sie in Visual Studio Designer dem Projekt mittels der entsprechenden Tools das DataSet hinzu. Eine Möglichkeit besteht darin, dem Projekt unter Verwendung des Datenquellenfensters eine Datenquelle hinzuzufügen.  
  
2.  Falls noch keine Instanz des Datasets existiert, erstellen Sie eine Instanz, und wählen Sie im Designer die Instanz aus.  
  
3.  Legen Sie im  Eigenschaftenfenster die Eigenschaft **CacheInDocument** auf **True** fest.  
  
     Weitere Informationen finden Sie unter [Eigenschaften in Office-Projekten](../vsto/properties-in-office-projects.md).  
  
4.  Legen Sie im **Eigenschaftenfenster** die **Modifiers**\-Eigenschaft auf **Public** fest \(der Standardwert ist **Internal**\).  
  
## Siehe auch  
 [Zwischenspeichern von Daten](../vsto/caching-data.md)   
 [Gewusst wie: Programmgesteuertes Zwischenspeichern von Datenquellen in einem Office-Dokument](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)   
 [Gewusst wie: Zwischenspeichern von Daten in einem kennwortgeschützten Dokument](../vsto/how-to-cache-data-in-a-password-protected-document.md)   
 [Zugreifen auf Daten in Dokumenten auf dem Server](../vsto/accessing-data-in-documents-on-the-server.md)   
 [Speichern von Daten](../data-tools/saving-data.md)  
  
  
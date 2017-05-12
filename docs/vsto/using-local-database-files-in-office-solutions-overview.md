---
title: "&#220;bersicht &#252;ber die Verwendung lokaler Datenbankdateien in Office-L&#246;sungen"
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
  - "Daten [Office-Entwicklung in Visual Studio], Lokal"
  - "Lokale Daten [Office-Entwicklung in Visual Studio]"
  - "Office-Anwendungen [Office-Entwicklung in Visual Studio], Daten"
ms.assetid: 7a920e6b-f0c3-4a62-b5dd-02668a6177b6
caps.latest.revision: 30
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 29
---
# &#220;bersicht &#252;ber die Verwendung lokaler Datenbankdateien in Office-L&#246;sungen
  Sie können eine Datenbankdatei, wie eine Datei des SQL Server Express \(.mdf\) oder eine Microsoft Office Access\-Datei \(.mdb\), in der Office\-Projektmappe einschließen.  Dadurch können Endbenutzer in Situationen, in denen die Verwendung einer zentralen Datenbank nicht erforderlich ist, eine lokale Datenbank verwenden. Diese Lösung bietet sich zum Beispiel bei einer lokalen Inventarprojektmappe an, die nur auf einem Computer verwendet wird.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## Importieren der Datenbankdatei in ein Projekt  
 Verwenden Sie zum Importieren der Datenbankdatei in das Projekt den **Assistenten zum Konfigurieren von Datenquellen**, um auf Grundlage der Datenbankdatei eine Datenquelle zu erstellen.  Der Assistent fügt dem Projekt die Datenbankdatei und ein typisiertes Dataset hinzu.  
  
## Bereitstellen der Datenbankdatei  
 Der **Assistent zum Konfigurieren von Datenquellen** verwendet einen relativen Pfad, um Verbindungen zur lokalen Datenbankdatei zu erstellen.  Dadurch können Sie die Projektmappen von einem Computer auf einen anderen kopieren, wenn Sie die relativen Positionen der Dateien beibehalten.  
  
 Wenn Sie die Projektmappe auf einem Server bereitstellen und anschließend das Dokument an alle Endbenutzer verteilen, müssen Sie zusätzlich die Datenbankdatei manuell verteilen und an derselben relativen Position zum Dokument installieren.  Dies bedeutet, dass der Endbenutzer das Dokument nicht an einen neuen Speicherort auf dem Computer verschieben darf, wenn er nicht auch die Datenbankdatei verschiebt.  
  
## Lokale Datenbankdateien und das Zwischenspeichern des Datasets  
 In Projektmappen auf Dokumentebene für Microsoft Office Excel oder Microsoft Office Word können Sie Datasets zwischenspeichern, indem Sie die Dataset\-Instanz mit dem Attribut <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> kennzeichnen.  Wenn Sie dem Projekt die Datenbankdatei unter Verwendung des **Assistenten zum Konfigurieren von Datenquellen** hinzufügen, wird dem Projekt automatisch ein typisiertes Dataset hinzugefügt.  Es ist nur selten erforderlich, auf dieses Dataset das Attribut <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> anzuwenden, da die Daten bereits lokal auf dem Computer des Benutzers vorhanden sind.  Weitere Informationen finden Sie unter [Zwischenspeichern von Daten](../vsto/caching-data.md).  
  
## Siehe auch  
 [Binden von Daten an Steuerelemente in Office-Projektmappen](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Gewusst wie: Auffüllen von Dokumenten mit Daten aus einer Datenbank](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [Gewusst wie: Aktualisieren einer Datenquelle mit Daten eines Hoststeuerelements](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)   
 [Bereitstellen einer Office-Projektmappe](../vsto/deploying-an-office-solution.md)   
 [Zwischenspeichern von Daten](../vsto/caching-data.md)  
  
  
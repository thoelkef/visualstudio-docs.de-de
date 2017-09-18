---
title: "Gewusst wie: Speichern von Daten aus einem Objekt in einer Datenbank | Microsoft Docs"
ms.custom: ""
ms.date: "09/22/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "Daten [Visual Studio], Speichern"
  - "Datenzugriff [Visual Studio], Objekte"
  - "Speichern von Daten"
ms.assetid: efd6135a-40cf-4b0d-8f8b-41a5aaea7057
caps.latest.revision: 9
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Gewusst wie: Speichern von Daten aus einem Objekt in einer Datenbank
Sie können Daten aus Objekten in einer Datenbank speichern, indem Sie die Werte aus dem Objekt an eine der DBDirect\-Methoden des TableAdapter übergeben \(z. B. `TableAdapter.Insert`\).  Weitere Informationen finden Sie unter [Übersicht über TableAdapters](../data-tools/tableadapter-overview.md).  
  
 Um Daten aus einer Auflistung von Objekten zu speichern, durchlaufen Sie die Auflistung \(z. B. in einer for\-next\-Schleife\), und senden Sie die Werte der einzelnen Objekte mithilfe einer der DBDirect\-Methoden des TableAdapter an die Datenbank.  
  
 Standardmäßig werden DBDirect\-Methoden auf einem TableAdapter erstellt, der direkt gegen die Datenbank ausgeführt werden kann.  Diese Methoden können direkt aufgerufen werden und benötigen keine <xref:System.Data.DataSet>\-Objekte oder <xref:System.Data.DataTable>\-Objekte für das Abgleichen von Änderungen beim Senden von Aktualisierungen an die Datenbank.  
  
> [!NOTE]
>  Wenn Sie einen TableAdapter konfigurieren, muss die Hauptabfrage ausreichend Informationen für die Erstellung der DBDirect\-Methoden enthalten.  Wenn ein TableAdapter z. B. für die Abfrage von Daten aus einer Tabelle konfiguriert wird, für die keine Primärschlüsselspalte definiert wurde, werden keine DBDirect\-Methoden generiert.  
  
|TableAdapter\-DBDirect\-Methode|Beschreibung|  
|-------------------------------------|------------------|  
|`TableAdapter.Insert`|Fügt einer Datenbank neue Datensätze hinzu. Dadurch können Sie einzelne Spaltenwerte als Methodenparameter übergeben.|  
|`TableAdapter.Update`|Aktualisiert vorhandene Datensätze in einer Datenbank.  Die `Update`\-Methode übernimmt die Werte der ursprünglichen und der neuen Spalte als Methodenparameter.  Anhand der ursprünglichen Werte wird der ursprüngliche Datensatz gefunden. Mit den neuen Werten wird dieser Datensatz anschließend aktualisiert.<br /><br /> Mit der `TableAdapter.Update`\-Methode werden auch Änderungen in einem Dataset abgeglichen, das an die Datenbank zurückgesendet wird. Dazu wird <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, <xref:System.Data.DataRow> oder ein Array aus <xref:System.Data.DataRow>s als Methodenparameter verwendet.|  
|`TableAdapter.Delete`|Löscht vorhandene Datensätze aus der Datenbank basierend auf den ursprünglichen Spaltenwerten, die als Methodenparameter übergeben werden.|  
  
### So speichern Sie neue Datensätze von einem Objekt in eine Datenbank  
  
-   Erstellen Sie die Datensätze, indem Sie die Werte an die `TableAdapter.Insert`\-Methode übergeben.  
  
     Im folgenden Beispiel wird in der Tabelle `Customers` ein neuer Kundendatensatz erstellt. Dazu werden die Werte im `currentCustomer`\-Objekt an die `TableAdapter.Insert`\-Methode übergeben.  
  
     [!code-cs[VbRaddataSaving#23](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_1.cs)]
     [!code-vb[VbRaddataSaving#23](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_1.vb)]  
  
### So aktualisieren Sie vorhandene Datensätze von einem Objekt in eine Datenbank  
  
-   Ändern Sie die Datensätze, indem Sie die `TableAdapter.Update`\-Methode aufrufen und die neuen Werte zur Aktualisierung des Datensatzes sowie die ursprünglichen Werte zum Finden des Datensatzes übergeben.  
  
    > [!NOTE]
    >  Das Objekt muss die ursprünglichen Werte beibehalten, um sie an die `Update`\-Methode übergeben zu können.  In diesem Beispiel werden Eigenschaften mit einem `orig`\-Präfix verwendet, um die ursprünglichen Werte zu speichern.  
  
     Im folgenden Beispiel wird in der Tabelle `Customers` ein vorhandener Datensatz aktualisiert. Dazu werden die ursprünglichen und die neuen Werte im `Customer`\-Objekt an die `TableAdapter.Update`\-Methode übergeben.  
  
     [!code-cs[VbRaddataSaving#24](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_2.cs)]
     [!code-vb[VbRaddataSaving#24](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_2.vb)]  
  
### So löschen Sie vorhandene Datensätze aus einer Datenbank  
  
-   Löschen Sie die Datensätze, indem Sie die `TableAdapter.Delete`\-Methode aufrufen und die ursprünglichen Werte zum Finden des Datensatzes übergeben.  
  
    > [!NOTE]
    >  Das Objekt muss die ursprünglichen Werte beibehalten, um sie an die `Delete`\-Methode übergeben zu können.  In diesem Beispiel werden Eigenschaften mit einem `orig`\-Präfix verwendet, um die ursprünglichen Werte zu speichern.  
  
     Im folgenden Beispiel wird in der Tabelle `Customers` ein Datensatz gelöscht. Dazu werden die ursprünglichen Werte im `Customer`\-Objekt an die `TableAdapter.Delete`\-Methode übergeben.  
  
     [!code-cs[VbRaddataSaving#25](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_3.cs)]
     [!code-vb[VbRaddataSaving#25](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_3.vb)]  
  
## .NET Framework-Sicherheit  
 Sie benötigen die Berechtigung, den ausgewählten INSERT\-, UPDATE\- oder DELETE\-Vorgang in der Tabelle in der Datenbank auszuführen.  
  
## Siehe auch  
 [Objektbindung in Visual Studio](../data-tools/bind-objects-in-visual-studio.md)   
 [Gewusst wie: Herstellen einer Verbindung mit Daten in Objekten](../Topic/How%20to:%20Connect%20to%20Data%20in%20Objects.md)   
 [Exemplarische Vorgehensweise: Herstellen einer Verbindung mit Daten in Objekten \(Windows Forms\)](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20Objects%20\(Windows%20Forms\).md)   
 [Gewusst wie: Direktes Zugreifen auf die Datenbank mit einem TableAdapter](../data-tools/directly-access-the-database-with-a-tableadapter.md)   
 [Binden von Windows Forms\-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Herstellen von Datenverbindungen in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Vorbereiten der Anwendung auf den Empfang von Daten](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Abrufen von Daten für die Anwendung](../data-tools/fetching-data-into-your-application.md)   
 [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Bearbeiten von Daten in der Anwendung](../data-tools/editing-data-in-your-application.md)   
 [Überprüfen von Daten](../Topic/Validating%20Data.md)   
 [Speichern von Daten](../data-tools/saving-data.md)
---
title: "Testbereich 6: L&#246;schen | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Löschen von Elementen der Datenquellen-Steuerelement [Visual Studio SDK]"
  - "Source Control-Plug-ins, Elemente löschen"
ms.assetid: 6f2e872c-5ba2-4303-9f50-a90cef9a6225
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Testbereich 6: L&#246;schen
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Dieses Quellcodeverwaltungs\-Plug\-In\-Testgebiet Löschaktionen enthält.  
  
 In **Projektmappen\-Explorer**Löschaktionen reagiert auf Quellcodeverwaltung.  
  
 Im Folgenden finden Sie eine Liste von Elementen, die gelöscht werden können:  
  
-   Dateien  
  
-   Ordner  
  
-   Project  
  
 Abhängig vom Projekttyp haben Sie möglicherweise die Option **Entfernen** das Projekt \(bewirkt, dass die Dateien auf dem Datenträger\) oder entfernt \( **Löschen** das Projekt die Dateien auf Datenträgern\).  Jede Aktion entfernt das Projekt oder Element von **Projektmappen\-Explorer**.  
  
## Erwartetes Verhalten  
 Das erwartete Verhalten für die Testfälle in testgebiet löschen:  
  
-   Gelöschtes Element ist nicht mehr in **Projektmappen\-Explorer**sichtbar.  
  
-   Das übergeordnete Element des gelöschten Projekts oder Elements wird nach Bedarf aktiviert \(möglicherweise mit einer Eingabeaufforderung aus.\)  
  
-   Nachdem Sie ausgecheckt oder hinzugefügtes Element löschen, wird NOT im **Anstehende Eincheckvorgänge** Fenster.  
  
-   Das Element ist immer noch im Quellcodeverwaltungsspeicher, nachdem der Löschvorgang und muss manuell gelöscht werden.  
  
|Aktion|Testschritte|Erwartete Ergebnisse zu überprüfen|  
|------------|------------------|----------------------------------------|  
|Löschen Sie ein Clientprojekt|1.  Erstellen Sie ein Clientprojekt.<br />2.  Fügen Sie die Projektmappe zur Quellcodeverwaltung hinzufügen.<br />3.  Entfernen Sie das gesamte Projekt aus der Projektmappe|Allgemeines erwartetes Verhalten.|  
|Löschen Sie eine leere Datei|1.  Erstellen Sie ein Clientprojekt.<br />2.  Fügen Sie eine Null\-Byte\-Datei dem Projekt hinzu.<br />3.  Fügen Sie die Projektmappe zur Quellcodeverwaltung hinzufügen.<br />4.  Wählen Sie die Datei aus, löschen Sie sie.|Allgemeines erwartetes Verhalten.|  
|Löschen Sie einen Ordner mit einer Datei|1.  Erstellen Sie einzelne Projektmappe Projekt.<br />2.  Fügen Sie einen Ordner hinzu.<br />3.  Fügen Sie eine Datei im Ordner hinzufügen.<br />4.  Fügen Sie die Projektmappe zur Quellcodeverwaltung hinzufügen.<br />5.  Checken Sie aufgefordert, das Projekt zu vermeiden.<br />6.  Löschen Sie den Ordner.|Allgemeines erwartetes Verhalten.|  
|Löschen eines Dateisystem\-Webprojekt|1.  Erstellen Sie ein Dateisystem\-Webprojekt \(verwenden Sie die Schaltfläche Durchsuchen, um einen UNC\-Pfad angegeben wird.\)<br />2.  Fügen Sie die Projektmappe zur Quellcodeverwaltung hinzufügen.<br />3.  Entfernen Sie das gesamte Projekt aus der Projektmappe.<br />4.  Wiederholen Sie die Schritte 1 bis 3 für ein lokales Webprojekt \(unterschiedliche Pfade der Übungen durch den Code hat jedoch die gleiche externen Schnittstelle und Verhalten.\)|Allgemeines erwartetes Verhalten.|  
|Löschen einer Datei aus einem Dateisystem\-Webprojekt|1.  Erstellen Sie ein Dateisystem\-Webprojekt.<br />2.  Fügen Sie die Projektmappe zur Quellcodeverwaltung hinzufügen.<br />3.  Löschen einer Datei aus dem Projekt.<br />4.  Wiederholen Sie die Schritte 1 bis 3 für ein lokales Webprojekt \(unterschiedliche Pfade der Übungen durch den Code hat jedoch die gleiche externen Schnittstelle und Verhalten.\)|Allgemeines erwartetes Verhalten.|  
  
## Siehe auch  
 [Test\-Handbuch für Source Control\-Plug\-ins](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
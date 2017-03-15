---
title: "Testbereich 7: Freigabe | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Gemeinsames Verwenden von Elementen der Datenquellen-Steuerelement [Visual Studio SDK]"
  - "Source Control-Plug-ins Freigabe Elemente"
ms.assetid: 6ec4780a-bda4-4327-bb3e-c6c9e7eabf35
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# Testbereich 7: Freigabe
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Dies schließt Testgebiet Elemente zwischen Speicherorten zum Freigeben **Freigeben** Befehl.  
  
 Ein hhare Vorgang ist die offensichtliche Duplikat von Dateien und Ordnern Elemente zwischen zwei oder mehreren Stellen innerhalb einer Hierarchie der Datei Quellcodeverwaltung.  Duplikat nicht wirklich tritt auf dem Server auf, aber der Benutzer sieht die gleiche Datei in zwei oder angegebenere Speicherorte.  Jedes Mal, wenn Änderungen an einem freigegebenen Elemente vorgenommen werden, finden diese Änderungen in allen anderen freigegebenen Speicherorten aus.  
  
 freigabe in Ordnern arbeiten, wenn Sie einen Ordner mit mindestens einer Datei unter Quellcodeverwaltung darin auswählen.  Der Befehl Freigabe erfolgt unter den folgenden Bedingungen deaktiviert:  
  
-   Wenn der ausgewählte Ordner ein leerer Ordner befindet.  
  
-   Wenn es sich um einen echten Ordner, gibt aber keine darin enthaltenen Dateien Quellcodeverwaltung.  
  
-   Wenn es sich um einen virtuellen Ordner, ob Dateien in der Quellcodeverwaltung oder darin enthalten sind.  
  
-   Wenn ein Remotewebsiten\-Webprojekt vorhanden ist.  
  
## Befehls\-Menü\-Zugriff  
 Die folgenden integrierten Entwicklungsumgebung [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] für Menüs werden in Testfällen verwendet.  
  
 Nutzung: **Datei**\- \>**Quellcodeverwaltung**\- \>**Freigeben**.  
  
## Erwartetes Verhalten  
  
-   Freigegebene Datei wird im freigegebenen Speicherort.  
  
-   Durch Anzeigen der Testergebnisse versions\-Speicher Quellcodeverwaltung, dass Dateien freigegeben werden.  
  
-   Eine freigegebene Datei bearbeiten, behandelt beide Speicherorte der Datei.  
  
## Testfälle  
 Im Folgenden sind bestimmte Testfälle für das Freigeben testgebiet.  
  
|Aktion|Testschritte|Erwartete Ergebnisse zu überprüfen|  
|------------|------------------|----------------------------------------|  
|Geben Sie eine Datei aus einem geladenen Projekt in einem Quellcodeverwaltungssystem zu einem anderen geladenen Projekt öffnen|1.  Erstellen Sie ein neues Projekt.<br />2.  Fügen Sie ein zweites Projekt der Projektmappe hinzu.<br />3.  Erstellen Sie eine Datei im zweiten Projekt mit einem Namen, der nicht im ersten Projekt befindet.<br />4.  Fügen Sie die Projektmappe zur Quellcodeverwaltung hinzufügen.<br />5.  Wählen Sie das erste Projekt aus.<br />6.  Öffnen Sie **Freigeben** \(Dialogfeld**Datei** \- \> **Quellcodeverwaltung** \- \> **Freigeben**\).<br />7.  Geben Sie die Datei aus dem zweiten Projekt im ersten Projekt.<br />8.  Übernehmen Sie **Auschecken** , wenn Sie dazu aufgefordert werden.|Allgemeines erwartetes Verhalten.|  
|Geben Sie eine Datei aus einem Projekt in ein anderes frei|1.  Erstellen Sie ein neues Projekt.<br />2.  Fügen Sie es zur Quellcodeverwaltung hinzufügen.<br />3.  Schließen Sie die Projektmappe.<br />4.  Erstellen Sie ein zweites Projekt \(neuen Projektmappe ein.\)<br />5.  Fügen Sie die Projektmappe zur Quellcodeverwaltung hinzufügen.<br />6.  Wählen Sie das Projekt aus.<br />7.  Öffnen Sie das Dialogfeld **Freigeben** \(**Datei** \- \> **Quellcodeverwaltung** \- \> **Freigeben**\).<br />8.  Geben Sie eine Datei aus dem zuvor hinzugefügten Projekt im geöffneten Projekt.<br />9. Übernehmen Sie **Auschecken** , wenn Sie dazu aufgefordert werden.|Allgemeines erwartetes Verhalten.|  
|Geben Sie einen Teil der Datei des Projekts nicht aus der Quellcodeverwaltung in das momentan geladene Projekt öffnen|1.  Erstellen Sie ein neues Projekt.<br />2.  Fügen Sie die Projektmappe zur Quellcodeverwaltung hinzufügen.<br />3.  Fügen Sie eine Datei zur Quellcodeverwaltung hinzufügen, die nicht Teil des Projekts oder der Projektmappe ist.<br />4.  Wählen Sie das Projekt aus, und öffnen Sie das Dialogfeld **Freigeben** \(**Datei** \- \> **Quellcodeverwaltung** \- \> **Freigeben**\).<br />5.  Wählen Sie eine Datei im **Freigeben** Dialogfelds aus, das sich nicht innerhalb des aktuellen Projekts oder der Projektmappe vorhanden ist und freigibt.<br />6.  Übernehmen Sie **Auschecken** , wenn Sie dazu aufgefordert werden.|Der get\-Accessor hat einen Datenspeicher Quellcodeverwaltung ausgeführt. Daher ist die Datei jetzt am lokalen Speicherort des Projekts.|  
|Freigeben von Dateien innerhalb desselben Projekts in einen anderen Ordner|1.  Wählen Sie in **Automatisch auscheckenExtras** \- \> **Optionen** \- \> **Quellcodeverwaltung**.<br />2.  Erstellen Sie ein neues Projekt und fügen Sie sie zur Quellcodeverwaltung hinzufügen.<br />3.  Fügen Sie dem Projekt einen Ordner hinzu.<br />4.  Fügen Sie dem Ordner eine Datei hinzu und überprüfen Sie in den Ordner.<br />5.  Wählen Sie den Ordner aus.<br />6.  Öffnen Sie **Freigeben** \(Dialogfeld**Datei** \- \> **Quellcodeverwaltung** \- \> **Freigeben**\).<br />7.  Freigeben Datei zum ausgewählten Ordner.|Allgemeines erwartetes Verhalten.<br /><br /> Ordner muss mit einer Datei in ihr eingecheckt werden, bevor sie für die Nutzung verwendet werden kann.|  
|Geben Sie einen Ordner in das geladene rekursive Projekt öffnen:|1.  Erstellen Sie ein neues Projekt.<br />2.  Fügen Sie die Projektmappe zur Quellcodeverwaltung hinzufügen.<br />3.  Wählen Sie das Projekt aus.<br />4.  Öffnen Sie das Dialogfeld **Freigeben** \(**Datei** \- \> **Quellcodeverwaltung** \- \> **Freigeben**\).<br />5.  Wählen Sie einen Ordner aus.<br />6.  Geben Sie den Ordner rekursiv in das Projekt.|Allgemeines erwartetes Verhalten.|  
|Geben Sie mehrere Dateien in einem Projekt gemeinsam mit anderen|1.  Erstellen Sie ein neues Projekt mit mehreren Dateien enthält.<br />2.  Fügen Sie die Projektmappe zur Quellcodeverwaltung hinzufügen.<br />3.  Schließen Sie die Projektmappe.<br />4.  Erstellen Sie ein neues Projekt in einer neuen Projektmappe.<br />5.  Fügen Sie die Projektmappe zur Quellcodeverwaltung hinzufügen.<br />6.  Wählen Sie das Projekt aus.<br />7.  Öffnen Sie das Dialogfeld **Freigeben** \(**Datei** \- \> **Quellcodeverwaltung** \- \> **Freigeben**\).<br />8.  Geben Sie mehrere Dateien aus dem zuvor erstellten Projekts dem aktuell geöffneten Projekt.|Allgemeines erwartetes Verhalten.|  
  
## Siehe auch  
 [Test\-Handbuch für Source Control\-Plug\-ins](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
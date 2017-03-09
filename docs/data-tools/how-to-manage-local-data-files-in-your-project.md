---
title: "Gewusst wie: Verwalten von lokalen Datendateien im Projekt | Microsoft Docs"
ms.custom: ""
ms.date: "09/21/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.data.LocalConnectionConverter"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - ".MDB-Dateien"
  - ".mdf-Dateien"
  - "Daten [Visual Studio], Lokal"
  - "Lokale Daten"
  - "MDB-Dateien"
  - "MDF-Dateien"
ms.assetid: 3ffa1aa9-17e4-422c-a02f-09224828cdfc
caps.latest.revision: 29
caps.handback.revision: 27
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Gewusst wie: Verwalten von lokalen Datendateien im Projekt
Eine lokale Datenbankdatei kann als Datei in ein Projekt eingebunden werden.  Wenn Sie zum ersten Mal eine Verbindung zwischen Ihrer Anwendung und einer lokalen Datenbankdatei herstellen, können Sie auswählen, ob Sie in Ihrem Projekt eine Kopie der Datenbank erstellen oder eine Verbindung zur Datenbankdatei an deren aktuellen Speicherort herstellen möchten.  Wenn Sie eine Verbindung zu der vorhandenen Datei herstellen, wird die Verbindung genauso wie zu jeder Remotedatenbank hergestellt, und die Datenbankdatei verbleibt am ursprünglichen Speicherort.  Wenn Sie die Datenbank in Ihr Projekt kopieren möchten, erstellt Visual Studio eine Kopie der Datenbankdatei, fügt sie dem Projekt hinzu und ändert die Verbindung, sodass sie auf die Datenbank im Projekt zeigt und nicht auf den ursprünglichen Speicherort der Datenbankdatei.  
  
> [!NOTE]
>  Bestehende Datenverbindungen im **Server\-Explorer\/Datenbank\-Explorer** werden geändert, sodass sie ebenfalls auf die Datenbankdatei im Projekt \(die Datenbankdatei im Stammordner des Projekts\) zeigen.  
  
 Wenn Sie ein Projekt erstellen, wird die Datenbankdatei eventuell aus dem Stammordner des Projekts in den Ausgabeordner \(**bin**\) kopiert. \(Wählen Sie im **Projektmappen\-Explorer** die Option **Alle Dateien anzeigen**, um den Ordner **bin** einzublenden.\) Dieses Verhalten basiert auf der Einstellung der Eigenschaft **In Ausgabeverzeichnis kopieren** der Datei.  Die Standardeinstellung der Eigenschaft ist abhängig vom Datenbankdateityp, den Sie verwenden.  
  
> [!NOTE]
>  Das Verhalten der Eigenschaft **In Ausgabeverzeichnis kopieren** gilt nicht für Webprojekte oder C\+\+\-Projekte.  
  
 Während der Anwendungsentwicklung werden alle Änderungen, die \(zur Laufzeit innerhalb der Anwendung\) vorgenommen werden, an der Datenbank im Ordner **bin** vorgenommen.  Wenn Sie beispielsweise F5 drücken, um die Anwendung zu debuggen, stellen Sie eine Verbindung mit der Datenbank im Ordner **bin** her.  Die Datenbankdatei im Stammordner des Projekts wird nur geändert, wenn Sie mit dem **Server\-Explorer**, **Datenbank\-Explorer** oder anderen [Visual Database Tools](http://msdn.microsoft.com/de-de/6b145922-2f00-47db-befc-bf351b4809a1) das Datenbankschema oder die Daten bearbeiten.  
  
 Die folgende Tabelle beschreibt die Einstellungen für die Eigenschaft **In Ausgabeverzeichnis kopieren**.  
  
|Einstellung|Verhalten|  
|-----------------|---------------|  
|**Kopieren, wenn neuer** \(Standardeinstellung für SDF\-Dateien\)|Die Datenbankdatei wird beim ersten Erstellen des Projekts aus dem Projektverzeichnis in das Verzeichnis **bin** kopiert.  Jedes Mal, wenn Sie das Projekt erneut erstellen, wird ein Vergleich mit der Eigenschaft **Geändert am** der Dateien durchgeführt.  Wenn die Datei im Projektordner neuer ist, wird sie in den Ordner **bin** kopiert und ersetzt die dort befindliche Datei.  Wenn die Datei im Ordner **bin** neuer ist, werden keine Dateien kopiert.  Mit dieser Einstellung werden alle zur Laufzeit vorgenommenen Änderungen an den Daten beibehalten, d. h., jedes Mal, wenn Sie die Anwendung ausführen und Änderungen an den Daten speichern, sind diese Änderungen beim nächsten Ausführen der Anwendung sichtbar. **Caution:**  Diese Option wird nicht für MDB\- oder MDF\-Dateien empfohlen.  Die Datenbankdatei kann sogar geändert werden, wenn gar keine Änderungen an den Daten vorgenommen werden.  Eine Datendatei wird auch dann als neuer gekennzeichnet, wenn eine Verbindung mit einer Datendatei für sie geöffnet wird \(z. B. durch Erweitern des Knotens **Tabellen** im **Server\-Explorer**\).|  
|**Immer kopieren** \(Standardeinstellung für MDF\- und MDB\-Dateien\)|Bei jedem Erstellen der Anwendung wird die Datenbankdatei aus dem Projektverzeichnis in das Verzeichnis "\/bin" kopiert.  Deshalb werden, wenn Sie die Anwendung erstellen und Änderungen an der Datei speichern, diese Änderungen überschrieben, wenn die ursprüngliche Datei das nächste Mal in das \/bin\-Verzeichnis kopiert wird.|  
|**Nicht kopieren**|Die Datei wird vom Projektsystem niemals kopiert oder überschrieben.  Sie müssen die Datei manuell aus dem Projektverzeichnis in das Ausgabeverzeichnis kopieren, wenn Sie diese Einstellung verwenden.|  
  
## Vorgehensweise  
  
#### So reagieren Sie auf das Dialogfeld "Lokale Datenbankdatei"  
  
-   Wenn Visual Studio die Datenbankdatei in Ihr Projekt kopieren soll und die Verbindung so ändern soll, dass sie auf die Kopie im Projekt zeigt, klicken Sie auf **Ja**.  Weitere Informationen zur Arbeit mit Datenbankdateien im Projekt finden Sie unter [Übersicht über lokale Daten](../data-tools/local-data-overview.md).  
  
-   Wenn Visual Studio die Datenbankdatei nicht in das Projekt kopieren soll, klicken Sie auf **Nein**.  Stattdessen zeigt die Verbindung auf die Datei am ursprünglichen Speicherort, und die Datenbankdatei wird dem Projekt nicht als Datei hinzugefügt.  
  
## Siehe auch  
 [Exemplarische Vorgehensweise: Herstellen einer Verbindung mit Daten in einer lokalen Datenbankdatei \(Windows Forms\)](../data-tools/walkthrough-connecting-to-data-in-a-local-database-file-windows-forms.md)   
 [Exemplarische Vorgehensweise: Herstellen einer Verbindung mit Daten in einer Access\-Datenbank \(Windows Forms\)](../data-tools/connect-to-data-in-an-access-database-windows-forms.md)
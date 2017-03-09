---
title: "Hierarchische Aktualisierung | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "Daten [Visual Basic], Hierarchische Aktualisierung"
  - "Datasets [Visual Basic], Hierarchische Aktualisierung"
  - "Hierarchische Aktualisierung"
  - "Speichern von geänderten Daten"
  - "Verknüpfte Tabellen, Speichern"
  - "Speichern von Daten, Geänderte Daten"
  - "Speichern von Daten, Hierarchische Aktualisierung"
  - "Speichern aktualisierter Daten"
  - "Speichern aktualisierter Daten"
ms.assetid: 68bae3f6-ec9b-45ee-a33a-69395029f54c
caps.latest.revision: 26
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Hierarchische Aktualisierung
*Hierarchische Aktualisierung* bezeichnet einen Vorgang, bei dem aktualisierte Daten \(aus einem DataSet mit mindestens zwei verknüpften Tabellen\) unter Einhaltung der Regeln zur referenziellen Integrität zurück in eine Datenbank gespeichert werden.  *Referenzielle Integrität* bezeichnet die Konsistenzregeln, die in einer Datenbank durch die Einschränkungen bereitgestellt werden, die das Verhalten beim Einfügen, Aktualisieren und Löschen von verknüpften Datensätzen steuern.  Beispielsweise wird durch die referenzielle Identität die Erstellung eines Kundendatensatzes erzwungen, bevor für diesen Kunden Aufträge erstellt werden können.  
  
 Das Speichern von geänderten Daten aus verknüpften Tabellen ist etwas komplexer als das Speichern von Daten einer einzelnen Tabelle.  Das liegt daran, dass die Befehle zum Aktualisieren, Einfügen und Löschen für jede verknüpfte Tabelle in einer bestimmten Reihenfolge ausgeführt werden müssen, um eine Verletzung der in der Datenbank definierten Fremdschlüsseleinschränkungen zu verhindern.  Stellen Sie sich z. B eine Auftragseingabeanwendung vor, mit der neue und bestehende Kunden und Aufträge verwaltet werden können.  Wenn Sie einen vorhandenen Kunden löschen möchten, müssen Sie erst sämtliche Aufträge dieses Kunden löschen, bevor Sie den Datensatz des Kunden löschen können.  Wenn Sie einen neuen Kunden \(mit Auftrag\) hinzufügen möchten, muss aufgrund der in den Tabellen bestehenden Fremdschlüsseleinschränkungen vor dem Einfügen des Kundenauftrags der Datensatz für den neuen Kunden eingefügt werden.  Wie Sie in diesen Beispiele sehen, müssen Sie bestimmte Untergruppen von Daten extrahieren und die Updates \(Einfügen, Aktualisieren und Löschen\) in der richtigen Reihenfolge senden, um die referenzielle Integrität einzuhalten.  
  
 Das hierarchische Updatefeature verwendet einen `TableAdapterManager`, um die `TableAdapter` in einem typisierten DataSet zu verwalten.  Bei der `TableAdapterManager`\-Komponente handelt es sich um eine von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] generierte Komponente. Sie ist daher nicht Teil von [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  Ausführliche Informationen über die `TableAdapterManager`\-Klasse finden Sie im Abschnitt TableAdapterManager\-Verweis in der [Übersicht über TableAdapterManager](../Topic/TableAdapterManager%20Overview.md).  
  
 Wenn die Anwendung typisierte DataSets verwendet und Benutzern ermöglicht, die Daten in verknüpften Datentabellen \(Datentabellen in einer 1:n\-Beziehung wie Customers oder Orders\) zu ändern, empfiehlt sich die Verwendung hierarchischer Aktualisierungen.  
  
## In diesem Abschnitt  
 [Übersicht über die hierarchische Aktualisierung](../Topic/Hierarchical%20Update%20Overview.md)  
 Bietet einen Überblick über hierarchische Aktualisierungen und enthält ausführliche Informationen zu deren Implementierung.  
  
 [Übersicht über TableAdapterManager](../Topic/TableAdapterManager%20Overview.md)  
 Bietet einen Überblick über den `TableAdapterManager` und enthält Beschreibungen des `TableAdapterManager`\-Codes, der vom DataSet\-Designer generiert wird.  
  
 [Gewusst wie: Aktivieren und Deaktivieren der hierarchischen Aktualisierung](../Topic/How%20to:%20Enable%20and%20Disable%20Hierarchical%20Update.md)  
 Beschreibt die erforderliche Einstellung der `Hierarchical Update`\-Eigenschaft in einem typisierten DataSet zum Generieren von Code und Speichern verknüpfter Tabellen.  
  
 [Gewusst wie: Konfigurieren von Fremdschlüsseleinschränkungen in einem DataSet](../Topic/How%20to:%20Configure%20Foreign-Key%20Constraints%20in%20a%20Dataset.md)  
 Beschreibt, wie die Einschränkungen in einem DataSet konfiguriert werden.  
  
 [Gewusst wie: Ausführen eines Commits für aktuelle Bearbeitungen von datengebundenen Steuerelementen vor dem Speichern von Daten](../data-tools/commit-in-process-edits-on-data-bound-controls-before-saving-data.md)  
 Beschreibt, wie in datengebundenen Steuerelementen in einem Formular alle aktuell ausgeführten Bearbeitungen beendet werden, um die zu speichernde Datenquelle vorzubereiten.  
  
 [Gewusst wie: Festlegen der Reihenfolge beim Durchführen einer hierarchischen Aktualisierung](../Topic/How%20to:%20Set%20the%20Order%20When%20Performing%20a%20Hierarchical%20Update.md)  
 Beschreibt, wie die `UpdateOrder`\-Eigenschaft in einem `TableAdapterManager` festgelegt wird, um die Reihenfolge der Einfüge\-, Aktualisierungs\- und Löschvorgänge zu steuern.  
  
 [Gewusst wie: Implementieren der hierarchischen Aktualisierung in vorhandenen Visual Studio\-Projekten](../Topic/How%20to:%20Implement%20Hierarchical%20Update%20in%20Existing%20Visual%20Studio%20Projects.md)  
 Beschreibt, wie eine Anwendung aktualisiert wird, in der verknüpfte Datentabellen enthalten sind, um Daten mit dem `TableAdapterManager` zu speichern.  
  
 [Exemplarische Vorgehensweise: Speichern von Daten aus verknüpften Datentabellen \(Hierarchische Aktualisierung\)](../Topic/Walkthrough:%20Saving%20Data%20from%20Related%20Data%20Tables%20\(Hierarchical%20Update\).md)  
 Bietet schrittweise Anweisungen zum Erstellen einer Anwendung mit verknüpften Datentabellen und zum Speichern von Daten mit dem `TableAdapterManager`.  
  
## Referenz  
 <xref:System.Data.DataSet>  
  
 <xref:System.Data.DataTable>  
  
## Verwandte Abschnitte  
 [Arbeiten mit Datasets in N\-Tier\-Anwendungen](../data-tools/work-with-datasets-in-n-tier-applications.md)  
  
 [Speichern von Daten](../data-tools/saving-data.md)  
  
 [Erstellen und Bearbeiten von typisierten Datasets](../data-tools/creating-and-editing-typed-datasets.md)  
  
 [TableAdapters](../Topic/TableAdapters.md)  
  
 [DataSets, DataTables und DataViews](../Topic/DataSets,%20DataTables,%20and%20DataViews.md)  
  
 [DataTables](../Topic/DataTables.md)  
  
 [Zugreifen auf Daten in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
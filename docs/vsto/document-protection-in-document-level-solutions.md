---
title: "Dokumentschutz in Projektmappen auf Dokumentebene"
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
  - "Dokumente [Office-Entwicklung in Visual Studio], Eingeschränkte Berechtigungen"
  - "Office-Dokumente [Office-Entwicklung in Visual Studio], Eingeschränkte Berechtigungen"
  - "Berechtigungen [Office-Entwicklung in Visual Studio]"
  - "Eingeschränkte Berechtigungen [Office-Entwicklung in Visual Studio]"
  - "Arbeitsmappen [Office-Entwicklung in Visual Studio], Eingeschränkte Berechtigungen"
ms.assetid: a25472ad-03f0-4804-9d19-e5ff71340d49
caps.latest.revision: 36
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 35
---
# Dokumentschutz in Projektmappen auf Dokumentebene
  In Projekten auf Dokumentebene können Sie die Schutzfunktionen von Microsoft Office Word und Microsoft Office Excel verwenden.  Diese verhindern, dass unbefugte Benutzer Änderungen an geschützten Teilen eines Dokuments vornehmen.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Mit Excel können Sie den Schutz aktivieren und deaktivieren, während die Arbeitsmappe im Designer geöffnet ist.  Mit Word können Sie den Schutz nur außerhalb des Designers aktivieren.  Zur Laufzeit können Sie den Schutz für Word und Excel programmgesteuert aktivieren oder deaktivieren.  
  
 Wenn der Dokumentschutz bei einem im Designer geöffneten Dokument aktiviert wird, werden alle Steuerelemente aus der **Toolbox** entfernt oder deaktiviert, sodass Sie nichts aus dem **Datenquellenfenster** auf das Dokument ziehen können.  
  
## ServerDocument und geschützte Dokumente  
 Wenn ein Dokument geschützt ist, kann auf den Datencache nicht von außerhalb des Dokuments zugegriffen werden.  Sie können weder mit der <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>\-Klasse in einem geschützten Dokument zwischengespeicherte Daten abrufen oder bearbeiten noch andere Methoden der <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ServerDocument>\-Klasse verwenden.  
  
## Word\-Dokumentschutz im Designer  
 Wenn Sie die Schutzfunktion für ein Word\-Dokument oder eine Word\-Vorlage aktivieren, während es bzw. sie in Visual Studio geöffnet ist, können Sie den Schutz nicht im Designer erzwingen.  Während es in Visual Studio geöffnet ist, befindet sich das Dokument im Entwurfsmodus. Den Schutz können Sie erst erzwingen, wenn es sich im Ausführmodus befindet.  
  
 Wenn Sie allerdings ein Projekt erstellen, das ein vorhandenes Word\-Dokument mit aktiviertem Schutz verwendet, ist das Dokument geschützt, während es im Designer geöffnet ist.  Seine geschützten Teile können Sie nicht bearbeiten, Sie können aber nach wie vor Code im Code\-Editor schreiben, um das Dokument zu automatisieren.  Wenn der Schutz aktiviert ist, während das Dokument in Visual Studio geöffnet ist, können Sie auch das Projekt nicht erstellen.  
  
 Sie können den Schutz deaktivieren, während das Dokument im Designer geöffnet ist, sodass Sie es bearbeiten und das Projekt erstellen können.  Beim Debuggen können Sie den Schutz für die Kopie im Designer nicht deaktivieren. Das Dokument, das beim Debuggen geöffnet wird, ist eine andere Kopie als die im Designer geöffnete \(die Ausgabekopie wird bei Visual Basic im Verzeichnis \\bin gespeichert, bei C\# im Verzeichnis \\bin\\debug\).  
  
 Für die Kopie des Dokuments, die im Designer geöffnet wird, können Sie den Schutz aktivieren, indem Sie das Projekt in Visual Studio schließen, die Dokumentkopie aus dem Projektverzeichnis öffnen und den Schutz aktivieren.  
  
## Erzwingen des Word\-Dokumentschutzes beim Build  
 Visual Studio erzwingt den Schutz für Word\-Dokumente und \-Vorlagen beim Buildvorgang, sodass der Schutz aktiviert ist, wenn das Dokument für das Debuggen geöffnet wird.  Das Dokument wird mit einem leeren Kennwort geschützt.  
  
 Der Schutz wird beim Build aktiviert, damit im Falle, dass es im <xref:Microsoft.Office.Tools.Word.Document.Startup>\-Ereignis des Dokuments Code gibt, der möglicherweise Ausnahmen verursacht oder das Anwendungsverhalten ändert, dieser richtig gedebuggt werden kann.  Wenn Sie den Schutz nach dem Öffnen des Dokuments aktivieren, kann der Initialisierungscode nicht gedebuggt oder getestet werden.  
  
## Festlegen des Kennworts  
 Visual Studio aktiviert automatisch Schutz, stellt aber standardmäßig kein Kennwort bereit.  Wenn der Dokumentschutz mit Kennwort erfolgen soll, müssen Sie das Kennwort vor der Bereitstellung der Projektmappe hinzufügen.  Durch Hinzufügen eines Kennworts können Sie Benutzern die Aufhebung des Dokumentschutzes ermöglichen; ohne Kennwort kann der Schutz nicht so leicht aufgehoben werden.  Ausführliche Informationen zum Festlegen eines Kennworts finden Sie in der Hilfe der jeweiligen Office\-Anwendung.  
  
## Siehe auch  
 [Gewusst wie: Programmgesteuertes Schützen von Dokumenten und Dokumentteilen](../vsto/how-to-programmatically-protect-documents-and-parts-of-documents.md)   
 [Beispiele und exemplarische Vorgehensweisen für die Programmierung mit Office](../vsto/office-development-samples-and-walkthroughs.md)   
 [Übersicht über Information Rights Management und Erweiterungen durch verwalteten Code](../vsto/information-rights-management-and-managed-code-extensions-overview.md)   
 [Kennwortschutz für Office-Dokumente](../vsto/password-protection-on-office-documents.md)   
 [Gewusst wie: Zulassen der Ausführung von Code im Hintergrund von Dokumenten mit eingeschränkten Berechtigungen](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)   
 [Entwerfen und Erstellen von Office-Lösungen](../vsto/designing-and-creating-office-solutions.md)  
  
  
---
title: "Gemeinsame Entwicklung von Office-L&#246;sungen | Microsoft Docs"
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
  - "Gemeinsame Entwicklung [Office-Entwicklung in Visual Studio]"
  - "Office-Anwendungen [Office-Entwicklung in Visual Studio], Gemeinsame Entwicklung"
  - "Office-Entwicklung in Visual Studio, Zusammenarbeit"
  - "Quellcodeverwaltung [Office-Entwicklung in Visual Studio]"
ms.assetid: c493354b-17d3-4e50-85f0-968b104bc978
caps.latest.revision: 29
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 28
---
# Gemeinsame Entwicklung von Office-L&#246;sungen
  Bei einem Office\-Projekt können mehrere Entwickler genauso zusammenarbeiten wie bei anderen Visual Studio\-Projekten.  Visual Studio findet Microsoft Office auf jedem Computer, selbst wenn Office an verschiedenen Speicherorten installiert ist.  Dabei sind aber einige wichtige Punkte zu beachten.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## Debugeigenschaften werden nicht freigegeben  
 In der Quellcodeverwaltung werden Debugeigenschaften nicht für mehrere Benutzer gemeinsam verwendet.  In Visual Basic\-Projekten und Visual C\#\-Projekten werden die Debugeigenschaften in einer benutzerspezifischen Datei \(*ProjectName*vbproj.user oder *ProjectName*.csproj.user\) gespeichert, und diese Datei wird nicht in die Quellcodeverwaltung einbezogen.  Wenn mehrere Personen debuggen, muss jede Person die Debugeigenschaften manuell eingeben.  
  
 Wenn sich das Projekt in einer Netzwerkfreigabe befindet statt in der Quellcodeverwaltung, müssen einige zusätzliche Schritte unternommen werden, damit zusammenarbeitende Entwickler die Projektmappe öffnen und die Assembly testen können.  
  
## Die Quellcodeverwaltung verlangt das Auschecken aller Dateien  
 Wenn Sie für Ihre Projekte die Quellcodeverwaltung verwenden, sollten Sie immer alle Dateien unterhalb einer Codedatei im **Projektmappen\-Explorer** \(beispielsweise die Codedateien ThisDocument, ThisWorkbook oder ThisAddIn\) auschecken, bevor Sie die Codedatei ändern. Dies gilt auch für Dateien, die standardmäßig ausgeblendet sind.  Wenn Sie nur die Codedatei der obersten Ebene auschecken, gehen die Änderungen möglicherweise verloren.  
  
 Nachdem Sie die Änderungen vorgenommen haben, checken Sie alle Dateien wieder ein.  Weitere Informationen zu ausgeblendeten Codedateien in Projekten finden Sie unter [Office-Projekte in der Visual Studio-Umgebung](../vsto/office-projects-in-the-visual-studio-environment.md).  
  
## Sicherheit für die zwanglose Zusammenarbeit in einem Netzwerk  
 Für alle Projektmappen auf Dokumentebene an einem Netzwerkspeicherort \(beispielsweise \\\\*Servername*\\*Sharename*\) muss der vollqualifizierte Speicherort zur Liste vertrauenswürdiger Verzeichnisse in der Microsoft Office\-Anwendung hinzugefügt werden, mit der Sie arbeiten.  Wählen Sie die Option, die Unterverzeichnisse unter dem Hauptverzeichnis einzuschließen, oder fügen Sie jeweils Debug\- und Buildverzeichnisse zur Liste vertrauenswürdiger Verzeichnisse hinzu.  Weitere Informationen hierzu finden Sie unter [Gewähren von Vertrauenswürdigkeit für Dokumente](../vsto/granting-trust-to-documents.md).  
  
 Die temporären Zertifikate, die automatisch zur Buildzeit generiert werden, werden nicht mit Kennwörtern gesichert.  Die Zertifikate enthalten den Benutzernamen des Entwicklers und andere persönliche Informationen.  Wenn Sie Anpassungen bereitstellen, die von temporären Zertifikaten signiert sind, könnten Andere auf diese Informationen zugreifen.  
  
## Siehe auch  
 [Sichern von Office-Projektmappen](../vsto/securing-office-solutions.md)   
 [Entwerfen und Erstellen von Office-Lösungen](../vsto/designing-and-creating-office-solutions.md)   
 [Aktualisieren von Office-Projektmappen](../vsto/building-office-solutions.md)  
  
  
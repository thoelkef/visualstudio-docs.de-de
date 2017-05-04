---
title: "Gewusst wie: Zulassen der Ausf&#252;hrung von Code im Hintergrund von Dokumenten mit eingeschr&#228;nkten Berechtigungen | Microsoft Docs"
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
  - "Code [Office-Entwicklung in Visual Studio], Ausführen vor beschränkten Dokumenten"
  - "Dokumente [Office-Entwicklung in Visual Studio], Eingeschränkte Berechtigungen"
  - "Information Rights Management [Office-Entwicklung in Visual Studio]"
  - "IRM [Office-Entwicklung in Visual Studio]"
  - "Office-Dokumente [Office-Entwicklung in Visual Studio], Eingeschränkte Berechtigungen"
  - "Berechtigungen [Office-Entwicklung in Visual Studio]"
ms.assetid: d037eae5-cf83-4be0-85ba-05e9f7d570e1
caps.latest.revision: 27
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 26
---
# Gewusst wie: Zulassen der Ausf&#252;hrung von Code im Hintergrund von Dokumenten mit eingeschr&#228;nkten Berechtigungen
  Sie können die Funktion für die Verwaltung von Informationsrechten in Microsoft Office verwenden, um Berechtigungen für ein Dokument oder eine Arbeitsmappe einzuschränken.  Der Code im Hintergrund eines Microsoft Office Word\-Dokuments oder einer Microsoft Office Excel\-Arbeitsmappe mit eingeschränkten Berechtigungen darf standardmäßig nicht ausgeführt werden.  Sie können die Standardeinstellung ändern, sodass Ihre Erweiterungen durch verwalteten Code auf das Objektmodell zugreifen können und die Lösung funktioniert.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Um die Berechtigungseinstellungen ändern zu können, müssen Sie der Autor des Dokuments oder der Arbeitsmappe sein oder über Vollzugriff verfügen.  
  
### So lassen Sie die Ausführung von Code im Hintergrund von Dokumenten mit eingeschränkten Berechtigungen zu  
  
1.  Öffnen Sie das Dokument oder die Arbeitsmappe in Word bzw. in Excel.  
  
2.  Klicken Sie auf die Registerkarte **Datei**, zeigen Sie auf **Vorbereiten**, zeigen Sie auf **Berechtigung einschränken**, und klicken Sie dann auf **Eingeschränkter Zugriff**.  
  
    > [!NOTE]  
    >  Bei der ersten Verwendung werden Sie aufgefordert, den Windows\-Rechteverwaltungsclient zu installieren.  Nachdem Sie den Client installiert haben, müssen Sie möglicherweise die Schritte wiederholen.  
  
3.  Wählen Sie im Dialogfeld **Berechtigung** die Option **Berechtigung für dieses Dokument einschränken** aus, und klicken Sie dann auf **Weitere Optionen**.  
  
4.  Wählen Sie unter **Zusätzliche Berechtigungen für Benutzer** die Option **Auf Inhalt programmatisch zugreifen** aus.  
  
 Word bzw. Excel ermöglicht dann den Programmzugriff auf das Objektmodell.  
  
## Siehe auch  
 [Übersicht über Information Rights Management und Erweiterungen durch verwalteten Code](../vsto/information-rights-management-and-managed-code-extensions-overview.md)   
 [Dokumentschutz in Projektmappen auf Dokumentebene](../vsto/document-protection-in-document-level-solutions.md)   
 [Kennwortschutz für Office-Dokumente](../vsto/password-protection-on-office-documents.md)   
 [Entwerfen und Erstellen von Office-Lösungen](../vsto/designing-and-creating-office-solutions.md)   
 [Sichern von Office-Projektmappen](../vsto/securing-office-solutions.md)   
 [Bereitstellen einer Office-Projektmappe](../vsto/deploying-an-office-solution.md)  
  
  
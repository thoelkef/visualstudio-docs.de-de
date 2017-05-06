---
title: "&#220;bersicht &#252;ber Information Rights Management und Erweiterungen durch verwalteten Code"
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
  - "Information Rights Management [Office-Entwicklung in Visual Studio]"
  - "IRM [Office-Entwicklung in Visual Studio]"
  - "Office-Dokumente [Office-Entwicklung in Visual Studio], Eingeschränkte Berechtigungen"
  - "Rechteverwaltung [Office-Entwicklung in Visual Studio]"
  - "Arbeitsmappen [Office-Entwicklung in Visual Studio], Eingeschränkte Berechtigungen"
ms.assetid: 9728f5fe-9122-48e7-b0a3-9f5e0a16164f
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# &#220;bersicht &#252;ber Information Rights Management und Erweiterungen durch verwalteten Code
  Microsoft Office Word und Microsoft Office Excel bieten ein neues Feature: Information Rights Management \(IRM\). Damit können Sie verhindern, dass Unbefugte vertrauliche Informationen anzeigen oder ändern.  Informationen zur Funktionsweise von Information Rights Management finden Sie in der Hilfe der jeweiligen Anwendung.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## Ausführen von Code im Hintergrund von Dokumenten mit eingeschränkten Berechtigungen  
 Wenn Ihre Projektmappe ein Dokument oder eine Arbeitsmappe enthält, das bzw. die IRM verwendet, ermöglichen Word und Excel keine Ausführung von Code.  Wenn Sie der Autor des Dokuments sind oder über Vollzugriff verfügen, können Sie die Standardeinstellung so ändern, dass die Projektmappe funktioniert.  Weitere Informationen finden Sie unter [Gewusst wie: Zulassen der Ausführung von Code im Hintergrund von Dokumenten mit eingeschränkten Berechtigungen](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md).  
  
 IRM verhindert, dass im Dokument zwischengespeicherte Daten mithilfe von <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ServerDocument> abgerufen oder bearbeitet werden.  
  
## Einschränken von Berechtigungen für Dokumente mit Erweiterungen durch verwalteten Code durch Endbenutzer  
 Jeder Benutzer mit Vollzugriff auf das Dokument oder die Arbeitsmappe in der Projektmappe kann mithilfe von IRM Berechtigungen einschränken.  Wenn beispielsweise ein Endbenutzer aus der Buchhaltung eine Lösung verwendet, mit der ein Arbeitsblatt automatisch mit Daten aus einer Datenbank gefüllt wird, wird dieser Benutzer u. U. den Schreibzugriff auf Mitarbeiter seiner Abteilung beschränken und den anderen nur Lesezugriff gewähren möchten.  Wenn der Benutzer die eingeschränkten Berechtigungen hinzufügt, kann in der Standardeinstellung der Code im Hintergrund des Arbeitsblattes nicht ausgeführt werden, weshalb es nicht mit Daten gefüllt werden kann.  
  
 Zur Behebung des Problems muss eine Person mit Vollzugriff auf das Dokument oder die Arbeitsmappe die standardmäßigen Berechtigungseinstellungen so ändern, dass der Programmzugriff auf das Objektmodell zulässig ist.  Weitere Informationen finden Sie unter [Gewusst wie: Zulassen der Ausführung von Code im Hintergrund von Dokumenten mit eingeschränkten Berechtigungen](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md).  
  
## Siehe auch  
 [Dokumentschutz in Projektmappen auf Dokumentebene](../vsto/document-protection-in-document-level-solutions.md)   
 [Kennwortschutz für Office-Dokumente](../vsto/password-protection-on-office-documents.md)   
 [Sichern von Office-Projektmappen](../vsto/securing-office-solutions.md)   
 [Bereitstellen einer Office-Projektmappe](../vsto/deploying-an-office-solution.md)   
 [Entwerfen und Erstellen von Office-Lösungen](../vsto/designing-and-creating-office-solutions.md)  
  
  
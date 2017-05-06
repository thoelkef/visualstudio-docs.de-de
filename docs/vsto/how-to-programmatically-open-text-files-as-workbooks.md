---
title: "Gewusst wie: Programmgesteuertes &#214;ffnen von Textdateien als Arbeitsmappen"
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
  - "Text [Office-Entwicklung in Visual Studio], Textdateien"
  - "Textdateien, Öffnen als Arbeitsmappen"
  - "Arbeitsmappen, Öffnen von Textdateien als"
ms.assetid: 056ae3d0-7fe7-4c28-a2a5-5a948baee0e6
caps.latest.revision: 47
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 46
---
# Gewusst wie: Programmgesteuertes &#214;ffnen von Textdateien als Arbeitsmappen
  Sie können eine Textdatei als Arbeitsmappe öffnen.  Sie müssen den Namen der zu öffnenden Textdatei übergeben.  Sie können dabei mehrere optionale Parameter angeben, z. B. die Zeilennummer, an der die Bearbeitung begonnen werden soll, oder das Spaltenformat der Daten in der Datei.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## Beispiel  
 [!code-csharp[Trin_VstcoreExcelAutomation#80](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#80)]
 [!code-vb[Trin_VstcoreExcelAutomation#80](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#80)]  
  
## Kompilieren des Codes  
 In diesem Beispiel sind die folgenden Komponenten erforderlich:  
  
-   Eine durch Komma getrennte Textdatei mit dem Namen `Test.txt`, die mindestens drei Textzeilen enthält.  
  
-   Die Textdatei `Test.txt`, die auf dem Laufwerk C: gespeichert werden soll.  
  
## Siehe auch  
 [Arbeiten mit Arbeitsmappen](../vsto/working-with-workbooks.md)   
 [Gewusst wie: Programmgesteuertes Öffnen von Arbeitsmappen](../vsto/how-to-programmatically-open-workbooks.md)   
 [Gewusst wie: Programmgesteuertes Erstellen neuer Arbeitsmappen](../vsto/how-to-programmatically-create-new-workbooks.md)   
 [Gewusst wie: Programmgesteuertes Speichern von Arbeitsmappen](../vsto/how-to-programmatically-save-workbooks.md)   
 [Gewusst wie: Programmgesteuertes Schließen von Arbeitsmappen](../vsto/how-to-programmatically-close-workbooks.md)   
 [Optionale Parameter in Office-Lösungen](../vsto/optional-parameters-in-office-solutions.md)  
  
  
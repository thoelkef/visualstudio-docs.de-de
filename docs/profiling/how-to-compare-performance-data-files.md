---
title: "Gewusst wie: Vergleichen der Profilerdatendateien | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vsperf.choosediffbinaries"
helpviewer_keywords: 
  - "Profilerergebnisdateien, Gewusst wie: Vergleichen"
  - "Profilerstellungstools, Gewusst wie: Vergleichen der Profilerergebnisdateien"
ms.assetid: 1905b45d-c6b3-43c8-87b1-1aee734f37f9
caps.latest.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 20
---
# Gewusst wie: Vergleichen der Profilerdatendateien
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können die Ergebnisse aus zwei unterschiedlichen Profilerdatendateien \(.vsp oder .vsps\) vergleichen, indem Sie einen Vergleichsbericht \("Diff"\) oder eine Vergleichsansicht erstellen.  Der Vergleich zeigt die Unterschiede, Leistungsregressionen und Verbesserungen an, die zwischen beiden Profilerstellungssitzungen aufgetreten sind.  
  
 Der Unterschiedsbericht enthält eine Tabellenansicht der Daten.  In der Tabelle wird das Delta bzw. die Abweichung von der Baseline dargestellt.  Zur Berechnung wird der Unterschied zwischen dem alten Wert, dem Baselinewert, und dem Ergebniswert aus der neuen Analyse ermittelt.  
  
 Vergleiche der Profilerdaten können auf den Funktionen im Code, den Modulen in der Anwendung, Zeilen, Anweisungszeigern \(IPs\) und Typen basieren.  
  
 Ein Schwellenwert kann festgelegt werden, um Störungen zu reduzieren und alle Daten in der Tabellenansicht der Zeilen herauszufiltern, bei denen keine Änderung um einen bestimmten Wert feststellbar ist.  
  
### So erstellen Sie für ein Projekt eine Vergleichsdateiansicht im Leistungs\-Explorer  
  
1.  Wählen Sie im **Leistungs\-Explorer** unter **Berichte** die VSP\- oder VSPS\-Berichtsdatei aus, die die Baselinewerte für den Vergleich liefern soll.  
  
2.  Wählen Sie die VSP\- oder VSPS\-Berichtsdateien aus, die Sie vergleichen möchten.  
  
3.  Klicken Sie mit der rechten Maustaste auf eine der ausgewählten Dateien, und klicken Sie dann auf **Berichte vergleichen**.  
  
### So vergleichen Sie Werte  
  
1.  Wählen Sie die Registerkarte **Vergleichsbericht** im Berichtsansichtsfenster.  
  
2.  Wählen Sie in der Dropdownliste **Tabelle** entweder die Funktion oder die Module für den Vergleich aus.  
  
3.  Wählen Sie in der Dropdownliste **Spalte** den Wert aus, den Sie vergleichen möchten.  
  
4.  \(optional\) Geben Sie einen Wert für **Schwellenwert** ein.  
  
5.  Klicken Sie auf **Übernehmen**.  
  
### So vergleichen Sie Berichtsdateien  
  
1.  Wählen Sie im Menü **Analyse Leistungsberichte vergleichen** aus.  
  
2.  Wählen Sie im Fenster **Analysedateien für Vergleich auswählen** die Analysedatei **Baselinedatei** \(.vsp oder .vsps\) und die **Vergleichsdatei** \(.vsp oder .vsps\) aus.  
  
3.  Klicken Sie auf **OK**.
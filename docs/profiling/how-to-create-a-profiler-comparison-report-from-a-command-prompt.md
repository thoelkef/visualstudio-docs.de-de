---
title: "Gewusst wie: Erstellen eines Profiler-Vergleichsberichts &#252;ber eine Eingabeaufforderung | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 00548d16-eb5b-46f7-8a65-862f98a43831
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Gewusst wie: Erstellen eines Profiler-Vergleichsberichts &#252;ber eine Eingabeaufforderung
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können einen Bericht der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Profilerstellungstools generieren, in dem die Leistungsdaten von zwei Profilerstellungs\-Datendateien \(VSP\- oder VSPS\-Dateien\) miteinander verglichen werden.  In dem Bericht werden die Unterschiede, Leistungsregressionen und Verbesserungen angezeigt, die zwischen beiden Profilerstellungssitzungen aufgetreten sind.  Die Werte im Bericht stellen das Delta bzw. die Abweichung von der Baseline der ersten Datei dar, die Sie angeben.  Zur Berechnung des Deltas wird der Unterschied zwischen dem alten Wert \(Baselinewert\) und dem Ergebniswert aus der neuen Analyse ermittelt.  Vergleiche der Profilerdaten können auf den Funktionen im Code, den Modulen in der Anwendung, Zeilen, Anweisungszeigern \(IPs\) und Typen basieren.  
  
 Geben Sie die folgende Befehlszeile ein, um die Bezeichner der Vergleichskategorien und der Felder aufzuführen:  
  
 **VSPerfReport \/querydifftables**  *VspFileName1* *VspFileName2*  
  
 Verwenden Sie die folgende Syntax, um den Vergleichsbericht zu erstellen:  
  
 **VSPerfReport \/diff**  `VspFileName1` *VspFileName2* \[**\/**`Options`\]  
  
 Sie können der **VSPerfReport \/diff** \-Befehlszeile Optionen aus der folgenden Tabelle hinzufügen.  
  
|Option|**Beschreibung**|  
|------------|----------------------|  
|**DiffThreshold:**\[*Value*\]|Ignoriert die Differenz, wenn sie unter diesem in Prozent angegebenen Schwellenwert liegt.  Neue Daten mit Werten, die unter diesem Schwellenwert liegen, werden ebenfalls nicht angezeigt.|  
|**DiffTable:** *TableName*|Verwendet diese Tabelle, um Dateien miteinander zu vergleichen.  Standardmäßig wird die Funktionstabelle verwendet.  Geben Sie den Bezeichner an, der in **VSPerfReport \/querydifftables** aufgeführt ist.|  
|**DiffColumn:** *ColumnName*|Verwendet diese Spalte, um Werte miteinander zu vergleichen.  Standardmäßig wird die Spalte mit dem prozentualen Wert der exklusiven Samplings verwendet.  Geben Sie den Bezeichner an, der in **VSPerfReport \/querydifftables** aufgeführt ist.|
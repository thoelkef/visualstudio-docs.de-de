---
title: 'Vorgehensweise: Erstellen eines Profilervergleichsberichts über eine Eingabeaufforderung | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 00548d16-eb5b-46f7-8a65-862f98a43831
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3cb31a79af25fbe66112efd6be0aacd9b3c3820d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47512888"
---
# <a name="how-to-create-a-profiler-comparison-report-from-a-command-prompt"></a>Gewusst wie: Erstellen eines Profiler-Vergleichsberichts über eine Eingabeaufforderung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Vorgehensweise: Erstellen eines Profiler-Vergleichsberichts über eine Eingabeaufforderung](https://docs.microsoft.com/visualstudio/profiling/how-to-create-a-profiler-comparison-report-from-a-command-prompt).  
  
Sie können einen Bericht zu Profilerstellungstools von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] erzeugen, der die Leistungsdaten von zwei Profilerstellungsdatendateien (VSP oder VSPS) miteinander vergleicht. Der Bericht zeigt die Unterschiede, leistungsregressionen und Verbesserungen, die von einer Profilerstellungssitzung in die andere aufgetreten sind. Die Werte im Bericht stehen für das Delta, oder die Abweichungen, von den Grundwerten der ersten Datei, die Sie angegeben haben. Zur Berechnung des Deltas wird der Unterschied zwischen dem alten Wert, welcher der Grundwert ist, und dem Ergebniswert aus der neuen Analyse ermittelt. Vergleiche der Profilerdaten können auf den Funktionen im Code, den Modulen in der Anwendung, Zeilen, Anweisungszeigern (IPs) und Typen basieren.  
  
 Um die Bezeichner der Vergleichskategorien und -felder aufzulisten, geben Sie die folgende Befehlszeile ein:  
  
 **VSPerfReport /querydifftables** *VspDateiName1* *VspDateiName2*  
  
 Verwenden Sie folgende Syntax zum Erstellen des Vergleichsberichts:  
  
 **VSPerfReport /diff** `VspFileName1` *VspDateiName2* [**/**`Options`]  
  
 Sie können Optionen aus der folgenden Tabelle in der Befehlszeile **VSPerfReport /diff** einfügen.  
  
|Option|Beschreibung|  
|------------|-----------------|  
|**DiffThreshold:**[*Wert*]|Ignorieren der Differenz, wenn Sie sich unterhalb dieses prozentualen Schwellenwerts befindet. Neue Daten mit Werten unterhalb dieses Schwellenwerts werden nicht angezeigt.|  
|**DiffTable:** *Tabellenname*|Vergleichen Sie die Dateien anhand dieser Tabelle. Standardmäßig wird die Funktionstabelle verwendet. Geben Sie den Bezeichner an, der in **VSPerfReport /querydifftables** aufgelistet ist.|  
|**DiffColumn:** *Spaltenname*|Verwenden Sie diese Spalte, um Werte zu vergleichen. Standardmäßig wird die exklusive Beispielprozentsatzspalte verwendet. Geben Sie den Bezeichner an, der in **VSPerfReport /querydifftables** aufgelistet ist.|




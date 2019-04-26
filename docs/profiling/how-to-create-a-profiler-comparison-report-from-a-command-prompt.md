---
title: 'Vorgehensweise: Erstellen eines Profilervergleichsberichts über eine Eingabeaufforderung | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 00548d16-eb5b-46f7-8a65-862f98a43831
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 11a3850073068cf280901a6948565329e83f4629
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62973941"
---
# <a name="how-to-create-a-profiler-comparison-report-from-a-command-prompt"></a>Vorgehensweise: Erstellen eines Profiler-Vergleichsberichts über eine Eingabeaufforderung
Sie können einen Bericht zu Profilerstellungstools von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] generieren, der die Leistungsdaten von zwei Profilerstellungsdatendateien (.*vsp* oder .*vsps*) miteinander vergleicht. Der Bericht zeigt die Unterschiede, Leistungsabnahmen und -verbesserungen, die beim Vergleich von zwei Profilerstellungssitzungen aufgefallen sind. Die Werte im Bericht stehen für das Delta, oder die Abweichungen, von den Grundwerten der ersten Datei, die Sie angegeben haben. Zur Berechnung des Deltas wird der Unterschied zwischen dem alten Wert, welcher der Grundwert ist, und dem Ergebniswert aus der neuen Analyse ermittelt. Vergleiche der Profilerdaten können auf den Funktionen im Code, den Modulen in der Anwendung, Zeilen, Anweisungszeigern (IPs) und Typen basieren.

 Um die Bezeichner der Vergleichskategorien und -felder aufzulisten, geben Sie die folgende Befehlszeile ein:

 **VSPerfReport /querydifftables** *VspDateiName1* *VspDateiName2*

 Verwenden Sie folgende Syntax zum Erstellen des Vergleichsberichts:

 **VSPerfReport /diff** `VspFileName1` *VspDateiName2* [**/**`Options`]

 Sie können Optionen aus der folgenden Tabelle in der Befehlszeile **VSPerfReport /diff** einfügen.

|Option|Beschreibung|
|------------|-----------------|
|**DiffThreshold:**[*Wert*]|Ignorieren der Differenz, wenn Sie sich unterhalb dieses prozentualen Schwellenwerts befindet. Neue Daten mit Werten unterhalb dieses Schwellenwerts werden nicht angezeigt.|
|**DiffTable:** *TableName*|Vergleichen Sie die Dateien anhand dieser Tabelle. Standardmäßig wird die Funktionstabelle verwendet. Geben Sie den Bezeichner an, der in **VSPerfReport /querydifftables** aufgelistet ist.|
|**DiffColumn:** *ColumnName*|Verwenden Sie diese Spalte, um Werte zu vergleichen. Standardmäßig wird die exklusive Beispielprozentsatzspalte verwendet. Geben Sie den Bezeichner an, der in **VSPerfReport /querydifftables** aufgelistet ist.|
---
title: 'Vorgehensweise: Sammeln von Samplingdaten auf Zeilenebene | Microsoft-Dokumentation'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- performance tools, line-level sampling
ms.assetid: 44803aad-dd39-4c2e-9209-d35185d44983
caps.latest.revision: 22
author: mikejo5000
ms.author: mikejo
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: 779171013514e67e5d7516521d136fa17adff06b
ms.contentlocale: de-de
ms.lasthandoff: 05/13/2017

---
# <a name="how-to-collect-line-level-sampling-data"></a>Gewusst wie: Sammeln von Samplingdaten auf Zeilenebene
Sampling auf Zeilenebene ermöglicht es dem Profiler zu bestimmen, wo eine prozessorintensive Funktion im Code ist, z.B. eine Funktion mit äußerst exklusiven Stichproben, die vom Prozessor die meiste Zeit beanspruchen.  
  
## <a name="overview"></a>Übersicht  
 Für das Sampling auf Zeilenebene, durchläuft der Profiler die Aufrufliste des Programms in festgelegten Intervallen und aggregiert diese Ergebnisse. Diese Ergebnisse zeigen, welche Anweisungen vom Prozessor ausgeführt wurde, als die Stichproben entnommen wurden. Die gesammelten Daten über exklusive Stichproben werden anschließend analysiert, um die Codezeile und den Anweisungszeiger (IP) zu identifizieren.  
  
 Sampling auf Zeilenebene funktioniert sowohl für verwalteten als auch nativen Code. Leistungsberichte, die diese Daten anzeigen, enthalten die Zeilen- und Modulansicht.  
  
 Begin/End-Zeicheninformationen sind nicht für nativen Code verfügbar. Für mehrzeilige Anweisungen sind Zeilenanfangsinformationen für nativen Code nicht verfügbar. Nur Zeilenendeinformationen sind verfügbar.  
  
### <a name="available-data"></a>Verfügbare Daten  
 Verfügbare Samplingdaten auf Zeilenebene umfassen die folgenden Informationen:  
  
-   Funktionsname  
  
-   Funktionsadresse  
  
-   Zeilenanfang: Zeilennummer des Samplingcodes.  
  
-   Zeilenende: Endquellzeilennummer. Dies ist normalerweise identisch mit den Daten „Line begin“, außer ein einzelner Programmauszug umfasst mehrere Quellcodezeilen.  
  
-   Zeichenanfang: Anfangsspalte der aggregierten Stichprobe. Dies ist normalerweise 0, außer eine einzelne Zeile enthält mehrere Programmauszüge.  
  
-   Zeilenende: Endspalte der aggregierten Stichprobe.  
  
-   IP: Adresse, von der die aggregierte Stichprobe (nur IP-Ansicht) erfasst wurde.  
  
 Wenn eine Funktion über Statistiken auf Zeilenebene in der Ansicht **Module** verfügt, schachteln sich die Statistiken unter jeder Funktion ein. Darüber hinaus werden Statistiken auf IP-Ebene angezeigt, die unter jeder Zeile geschachtelt werden.  
  
### <a name="turn-off-line-level-sampling-for-managed-code"></a>Deaktivieren Sie das Sampling auf Zeilenebene für verwalteten Code  
 Sampling auf Zeilenebene ist standardmäßig aktiviert. Sie können die Datensammlung auf Zeilenebene für verwalteten Code deaktivieren, indem Sie einen der folgenden Schritte durchführen:  
  
-   Bevor Sie ein Profil erstellen, geben Sie **VSPerfCLREnv /samplelineoff** ein. Dies wirkt sich auf Anwendungen und Dienste aus.  
  
     – oder –  
  
-   Wenn eine Anwendung starten, geben Sie **VSPerfCmd/lineoff \<other arguments >** ein.  
  
## <a name="see-also"></a>Siehe auch  
 [Konfigurieren von Leistungssitzungen](../profiling/configuring-performance-sessions.md)   
 [Analysieren der durch Leistungstools erstellten Daten](../profiling/analyzing-performance-tools-data.md)

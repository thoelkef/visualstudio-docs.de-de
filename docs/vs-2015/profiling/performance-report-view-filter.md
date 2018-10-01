---
title: Filter für die Leistungsberichtansicht | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- profiling tools, Profiler Report view filter
- Profiler Report View filter, profiling tools
ms.assetid: 35f89d86-4683-4db1-aa0c-ae0ce65fa524
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1568ec12a635014239a1533bf00df09a1e63ac14
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47513419"
---
# <a name="performance-report-view-filter"></a>Filter für die Leistungsberichtansicht
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Leistungsberichtansicht](https://docs.microsoft.com/visualstudio/profiling/performance-report-view-filter).  
  
Das Fenster für den Filter für die Profilerstellungsberichtansicht befindet sich am oberen Rand des Leistungsberichtsfensters. Wenn es nicht angezeigt wird, klicken Sie auf die Schaltfläche **Filter anzeigen**.  
  
 Sie können jede Filterklausel ändern, um Ihre Suchergebnisse zu verfeinern. Die folgenden Spalten sind im Filtergenerator verfügbar.  
  
|Element filtern|Beschreibung|  
|-----------------|-----------------|  
|Und/Oder|Wählen Sie **Und** aus, wenn diese Klausel und die nächste Klausel beide wahr sein müssen, um zu einer Übereinstimmung zu führen. Wählen Sie **Oder** aus, wenn diese Klausel oder die nächste Klausel wahr sein kann, um zu einer Übereinstimmung zu führen.|  
|Feld|Wählen Sie das zu verwendende Feld in der Filterklausel aus der Liste der Datenfelder aus, die in der aktuellen Berichtsdatei verfügbar sind.|  
|Operator|Wählen Sie den Operator aus, der die Beziehung angibt, die Sie zwischen dem Feld und dem Wert herstellen möchten.<br /><br /> = Gleich<br /><br /> <> Ungleich<br /><br /> < Kleiner als<br /><br /> > Größer als<br /><br /> <= Kleiner als oder gleich<br /><br /> >= Größer als oder gleich|  
|Wert|Wählen Sie den Wert aus, nach dem gesucht werden soll, oder geben Sie den Wert ein. In einigen Feldern werden die verfügbaren Werte für das Feld aufgeführt.|  
  
 Sie können Filterklauseln hinzufügen, bis Sie glauben, dass Sie durch den Filter die besten Ergebnisse erhalten. Klicken Sie auf **Filter ausführen**, um den Filter auf die Datendatei anzuwenden.  
  
 Aus der Berichtsansicht **Markierungen** können Sie Filterklauseln generieren, um die Daten in den Berichtsansichten auf die Daten zu begrenzen, die zwischen zwei Markierungen gesammelt werden. Wählen Sie die Eingaben, die Sie zum Beginn und Ende der Berichtsdaten verwenden möchten, klicken Sie dann mit der rechten Maustaste und wählen Sie entweder **Filter für Markierungen hinzufügen** oder **Filter für Timestamps hinzufügen**. Beide Filter beschränken die Daten in der aktuellen Datendatei auf denselben Zeitraum. **Filter für Markierungen hinzufügen** kann auf andere VSP-Dateien angewendet werden.  
  
 Um den Filter zu speichern, klicken Sie auf **Filter exportieren** in der Leistungsberichtssymbolleiste, und geben Sie dann einen Speicherort und Namen für die VSPF-Datei an. Um einen zuvor gespeicherten Filter zu laden, klicken Sie auf **Filter importieren**, und suchen Sie die gespeicherte Filterdatei. Filterdateien können auch verwendet werden, um Datendateien auf Computern zu filtern, auf denen eigenständigen Profilerstellungstools installiert sind. Weitere Informationen finden Sie unter [VSPerfReport](../profiling/vsperfreport.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Analysieren der durch Leistungstools erstellten Daten](../profiling/analyzing-performance-tools-data.md)   
 [VSPerfReport](../profiling/vsperfreport.md)




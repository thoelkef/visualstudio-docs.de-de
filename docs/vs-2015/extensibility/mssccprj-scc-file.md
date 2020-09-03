---
title: Mssccprj. SCC-Datei | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, MSSCCPRJ.SCC file
- MSSCCPRJ.SCC file
ms.assetid: 6f2e39d6-b79d-407e-976f-b62a3cedd378
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 705e0fa821000716dc9cd729901fbb7db5fd759c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194218"
---
# <a name="mssccprjscc-file"></a>Datei „MSSCCPRJ.SCC“
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn eine Visual Studio-Projekt Mappe oder ein Projekt in der Quell Code Verwaltung mithilfe der IDE platziert wird, empfängt die IDE zwei wichtige Informationen aus dem Quellcodeverwaltungs-Plug-in in Form von Zeichen folgen. Diese Zeichen folgen "" und "" "" "" "" "" "" "" "" "" "" "" " Die IDE erhält diese Zeichen folgen in der Regel beim ersten Mal durch Aufrufen von [sccgetprojpath](../extensibility/sccgetprojpath-function.md). Sie speichert Sie dann in der Projekt Mappe oder Projektdatei, um Sie in zukünftigen Aufrufen von [sccopenproject](../extensibility/sccopenproject-function.md)aufrufen zu können. Wenn Sie in die Projekt Mappe und die Projektdateien eingebettet sind, werden die Zeichen folgen "AUXPATH" und "ProjName" nicht automatisch aktualisiert, wenn ein Benutzer Projektmappen und Projektdateien, die sich in der Versionskontrolle befinden, verzweigt, verzweigt oder kopiert. Um sicherzustellen, dass die Projektmappen-und Projektdateien auf Ihren richtigen Speicherort in der Versionskontrolle zeigen, müssen die Benutzer die Zeichen folgen manuell aktualisieren. Da die Zeichen folgen als nicht transparent gemeint sind, ist es möglicherweise nicht immer klar, wie Sie aktualisiert werden sollten.  
  
 Das Quellcodeverwaltungs-Plug-in kann dieses Problem vermeiden, indem die Zeichen folgen "AUXPATH" und "ProjName" in einer speziellen Datei namens "Mssccprj" gespeichert werden. SCC-Datei. Dabei handelt es sich um eine lokale, Client seitige Datei, die im Besitz des Plug-ins ist. Diese Datei wird nie unter Quell Code Verwaltung abgelegt, aber vom Plug-in für jedes Verzeichnis generiert, das Quell Code gesteuerte Dateien enthält. Um zu ermitteln, welche Dateien Visual Studio-Projektmappen-und Projektdateien sind, kann ein Quellcodeverwaltungs-Plug-in die Dateierweiterungen mit einer standardmäßigen oder benutzerdefinierten Liste vergleichen. Sobald die IDE erkennt, dass ein Plug-in Mssccprj unterstützt. SCC-Datei, wird die Zeichenfolge "AUXPATH" und "ProjName" nicht mehr in Projektmappen-und Projektdateien eingebettet und liest diese Zeichen folgen aus Mssccprj. Stattdessen SCC-Datei.  
  
 Ein Quellcodeverwaltungs-Plug-in, das Mssccprj unterstützt. Die SCC-Datei muss den folgenden Richtlinien entsprechen:  
  
- Es darf nur ein Mssccprj vorhanden sein. SCC-Datei pro Verzeichnis.  
  
- Ein Mssccprj. Die SCC-Datei kann "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "  
  
- Die ""-Zeichenfolge "" für "" Es darf z. b. in Anführungszeichen eingeschlossen werden (z. b., um eine leere Zeichenfolge anzugeben). Die IDE entfernt alle Anführungszeichen aus der Zeichenfolge "AUXPATH", wenn Sie aus der Mssccprj-Datei gelesen wird. SCC-Datei.  
  
- Die Zeichenfolge "ProjName" in Mssccprj. Die SCC-Datei muss genau mit der von der Funktion zurückgegebenen Zeichenfolge übereinstimmen `SccGetProjPath` . Wenn die von der Funktion zurückgegebene Zeichenfolge in Anführungszeichen eingeschlossen ist, ist dies die Zeichenfolge in Mssccprj. Die SCC-Datei muss in Anführungszeichen eingeschlossen werden und umgekehrt.  
  
- Ein Mssccprj. Die SCC-Datei wird immer dann erstellt oder aktualisiert, wenn eine Datei unter Quell Code Verwaltung platziert wird.  
  
- Wenn ein Mssccprj. SCC-Datei wird gelöscht. ein Anbieter sollte ihn beim nächsten Ausführen eines Quell Code Verwaltungs Vorgangs für dieses Verzeichnis erneut generieren.  
  
- Ein Mssccprj. Die SCC-Datei muss streng dem definierten Format entsprechen.  
  
## <a name="an-illustration-of-the-mssccprjscc-file-format"></a>Eine Abbildung von Mssccprj. SCC-Datei Format  
 Im folgenden finden Sie ein Beispiel für Mssccprj. SCC-Dateiformat (die Zeilennummern werden nur als Leitfaden bereitgestellt und sollten nicht in den Datei Text eingefügt werden):  
  
 [Zeile 1] `SCC = This is a Source Code Control file`  
  
 [Zeile 2]  
  
 [Zeile 3] `[TestApp.sln]`  
  
 [Zeile 4] `SCC_Aux_Path = "\\server\vss\"`  
  
 [Zeile 5] `SCC_Project_Name = "$/TestApp"`  
  
 [Zeile 6]  
  
 [Zeile 7] `[TestApp.csproj]`  
  
 [Zeile 8] `SCC_Aux_Path = "\\server\vss\"`  
  
 [Zeile 9] `SCC_Project_Name = "$/TestApp"`  
  
 Die erste Zeile gibt den Zweck der Datei an und fungiert als Signatur für alle Dateien dieses Typs. Diese Zeile sollte in allen Mssccprj genau wie folgt aussehen. SCC-Dateien:  
  
 `SCC = This is a Source Code Control file`  
  
 Dabei handelt es sich um einen Abschnitt von Einstellungen für jede Datei, der durch den Dateinamen in eckigen Klammern gekennzeichnet ist. Dieser Abschnitt wird für jede Datei wiederholt, die nachverfolgt wird. Diese Zeile ist ein Beispiel für einen Dateinamen, nämlich `[TestApp.csproj]` . Die IDE erwartet die folgenden beiden Zeilen. Dabei wird jedoch nicht der Stil der definierten Werte definiert. Die Variablen sind `SCC_Aux_Path` und `SCC_Project_Name` .  
  
 `SCC_Aux_Path = "\\server\vss\"`  
  
 `SCC_Project_Name = "$/TestApp"`  
  
 Es gibt kein endtrennzeichen zu diesem Abschnitt. Der Name der Datei sowie alle Literale, die in der Datei angezeigt werden, werden in der SCC. h-Header Datei definiert. Weitere Informationen finden Sie unter Zeichen folgen, die [als Schlüssel zum Suchen eines Quellcodeverwaltungs-Plug-ins verwendet werden](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Quellcodeverwaltungs-Plug-ins](../extensibility/source-control-plug-ins.md)   
 [Als Schlüssel zum Suchen eines Quellcodeverwaltungs-Plug-Ins verwendete Zeichenfolgen](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)

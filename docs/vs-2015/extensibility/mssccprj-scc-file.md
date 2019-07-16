---
title: MSSCCPRJ. SCC-Datei | Microsoft-Dokumentation
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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68194218"
---
# <a name="mssccprjscc-file"></a>Datei „MSSCCPRJ.SCC“
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn Visual Studio-Projektmappe oder das Projekt unter quellcodeverwaltung, die mit der IDE platziert wird, erhält die IDE zwei wichtige Informationen über das Quellcodeverwaltungs-Plug-in Form von Zeichenfolgen. Diese Zeichenfolgen, die "AuxPath" und "Projektname", sind für die IDE nicht transparent, aber sie werden vom plug-in verwendet, um die Projektmappe oder das Projekt in der Versionskontrolle zu suchen. Die IDE in der Regel ruft diese Zeichenfolgen erstmals durch Aufrufen der [SccGetProjPath](../extensibility/sccgetprojpath-function.md), und klicken Sie dann speichert sie in der Projektmappe oder ein Projekt-Datei für zukünftige Aufrufe von der [SccOpenProject](../extensibility/sccopenproject-function.md). Bei der Einbettung in die Projektmappen- und Projektdateien-Dateien werden die Zeichenfolgen "AuxPath" und "Projektname" nicht automatisch aktualisiert, wenn ein Benutzer, Forks, branches oder Projektmappen- und Projektdateien-Dateien, die in der Versionskontrolle werden kopiert. Um sicherzustellen, dass die Dateien Projektmappen- und Projektdateien auf am richtigen Speicherort in der Versionskontrolle verweisen, müssen die Zeichenfolgen von Benutzer manuell aktualisieren. Da die Zeichenfolgen nicht transparent sein sollen, möglicherweise nicht immer klar, wie sie aktualisiert werden soll.  
  
 Das Quellcodeverwaltungs-Plug-in kann dieses Problem vermeiden, indem Sie die Zeichenfolgen "AuxPath" und "Projektname" in eine spezielle Datei namens der MSSCCPRJ speichern. SCC-Datei. Es handelt es sich um eine lokale, Client-Side-Datei, die im Besitz ist und vom plug-in beibehalten. Diese Datei befindet sich nicht unter quellcodeverwaltung, aber es wird generiert, indem Sie das plug-in für jedes Verzeichnis an, die der quellcodeverwaltung unterliegende Dateien enthält. Um zu bestimmen, welche Dateien über Visual Studio-Projektmappen und Projektdateien-Dateien sind, kann ein Quellcodeverwaltungs-Plug-in die Erweiterungen mit einer Standard- oder benutzerdefinierte Liste vergleichen. Sobald die IDE erkennt, dass ein plug-in die MSSCCPRJ unterstützt. SCC-Datei, sie ist nicht mehr zum Einbetten der "AuxPath" und "Projektname" von Zeichenfolgen in Projektmappen und Projektdateien und liest diese Zeichenfolgen aus der MSSCCPRJ. Stattdessen SCC-Datei.  
  
 Eines Quellcodeverwaltungs-Plug-in, das die MSSCCPRJ unterstützt. SCC-Datei muss die folgenden Richtlinien eingehalten werden:  
  
- Es kann nur eine MSSCCPRJ vorhanden sein. SCC-Datei pro Verzeichnis.  
  
- Ein MSSCCPRJ. SCC-Datei kann die "AuxPath" und "Projektname" für mehrere Dateien enthalten, die in der quellcodeverwaltung in einem angegebenen Verzeichnis befinden.  
  
- Die Zeichenfolge "AuxPath" darf keine Anführungszeichen in die Datei haben. Es ist zulässig, die Anführungszeichen als Trennzeichen verwendet haben (z. B. ein Paar von Anführungszeichen kann an eine leere Zeichenfolge verwendet werden). Beim Lesen aus der MSSCCPRJ, wird die IDE alle Angebote aus der Zeichenfolge "AuxPath" entfernen. SCC-Datei.  
  
- Die Zeichenfolge "Projektname" in der MSSCCPRJ. SCC-Datei muss genau mit die Zeichenfolge zurückgegeben, die aus entsprechen den `SccGetProjPath` Funktion. Wenn die Zeichenfolge, die von der Funktion zurückgegebene Anführungszeichen, die Zeichenfolge in die MSSCCPRJ hat. SCC-Datei müssen die Anführungszeichen um es herum (und umgekehrt).  
  
- Ein MSSCCPRJ. SCC-Datei erstellt oder aktualisiert, wenn eine Datei unter quellcodeverwaltung gestellt wird.  
  
- Wenn ein MSSCCPRJ. SCC-Datei gelöscht wird, wird ein Anbieter sollte es das nächste Mal wird einen Quellcodeverwaltungsvorgang zu diesem Verzeichnis generieren.  
  
- Ein MSSCCPRJ. SCC-Datei muss genau mit dem definierte Format folgen.  
  
## <a name="an-illustration-of-the-mssccprjscc-file-format"></a>Eine Abbildung der MSSCCPRJ. SCC-Dateiformat  
 Es folgt ein Beispiel für die MSSCCPRJ. SCC-Dateiformat (die Zeilennummern werden nur als Leitfaden bereitgestellt und sollte nicht in der Datei Text enthalten sein):  
  
 [Zeile 1] `SCC = This is a Source Code Control file`  
  
 [Zeile 2]  
  
 [Zeile 3] `[TestApp.sln]`  
  
 [Zeile 4] `SCC_Aux_Path = "\\server\vss\"`  
  
 [Line 5] `SCC_Project_Name = "$/TestApp"`  
  
 [Zeile 6]  
  
 [Zeile 7] `[TestApp.csproj]`  
  
 [Line 8] `SCC_Aux_Path = "\\server\vss\"`  
  
 [Zeile 9] `SCC_Project_Name = "$/TestApp"`  
  
 Die erste Zeile gibt den Zweck der Datei, und dient als die Signatur für alle Dateien dieses Typs. Diese Zeile sollte genau wie dies in allen MSSCCPRJ angezeigt werden. SCC-Dateien:  
  
 `SCC = This is a Source Code Control file`  
  
 Im folgenden ist ein Abschnitt der Einstellungen für jede Datei, die durch den Dateinamen in eckige Klammern gekennzeichnet. In diesem Abschnitt wird für jede Datei, die nachverfolgt wird wiederholt. Diese Zeile ist ein Beispiel für einen Dateinamen ein, nämlich `[TestApp.csproj]`. Die IDE erwartet, dass die folgenden zwei Zeilen. Es definiert jedoch nicht, den Stil der definierten Werte. Die Variablen sind `SCC_Aux_Path` und `SCC_Project_Name`.  
  
 `SCC_Aux_Path = "\\server\vss\"`  
  
 `SCC_Project_Name = "$/TestApp"`  
  
 Es gibt keine Endtrennzeichen, das in diesem Abschnitt. Der Name der Datei als auch Literale, die in der Datei angezeigt werden, werden in der Headerdatei scc.h definiert. Weitere Informationen finden Sie unter [Zeichenfolgen, die als Schlüssel für die Suche nach einer Datenquellen-Steuerelement-Plug-Ins](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Quellcodeverwaltungs-Plug-ins](../extensibility/source-control-plug-ins.md)   
 [Als Schlüssel zum Suchen eines Quellcodeverwaltungs-Plug-Ins verwendete Zeichenfolgen](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)

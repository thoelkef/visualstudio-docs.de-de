---
title: MSSCCPRJ. SCC-Datei | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control plug-ins, MSSCCPRJ.SCC file
- MSSCCPRJ.SCC file
ms.assetid: 6f2e39d6-b79d-407e-976f-b62a3cedd378
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 90a21ba6aafa0c5d06565c66531e2a6779aa419f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="mssccprjscc-file"></a>MSSCCPRJ. SCC-Datei
Wenn Visual Studio-Projektmappen oder Projekten unter quellcodeverwaltung mithilfe der IDE platziert wird, empfängt die IDE zwei sind wichtige Informationen aus dem Quellsteuerelement-Plug-in Form von Zeichenfolgen. Diese Zeichenfolgen, die "AuxPath" und "Projektname", sind für die IDE nicht transparent, aber sie werden vom plug-in verwendet, um die Projektmappe oder das Projekt in der Versionskontrolle zu suchen. Die IDE in der Regel ruft diese Zeichenfolgen erstmalig durch Aufrufen der [SccGetProjPath](../extensibility/sccgetprojpath-function.md), und es dann speichert sie in der Projektmappe bzw. im Projekt-Datei für zukünftige Aufrufe der [SccOpenProject](../extensibility/sccopenproject-function.md). Wenn in den Dateien Projektmappen- und Projektdateien eingebettet wird, werden die Zeichenfolgen "AuxPath" und "Projektname" nicht automatisch aktualisiert, wenn ein Benutzer, Zweige verzweigt, oder Projektmappen- und Projektdateien Dateien kopiert, die in der Versionskontrolle sind. Um sicherzustellen, dass die Projektmappen- und Projektdateien Dateien am richtigen Speicherort in der Versionskontrolle verweisen, müssen Benutzer die Zeichenfolgen manuell aktualisieren. Da die Zeichenfolgen nicht transparent sein sollen, ist es nicht immer klar werden wie sie aktualisiert werden sollen.  
  
 Die Datenquellen-Steuerelement-Plug-in kann dieses Problem vermeiden, indem Sie die Zeichenfolgen "AuxPath" und "Projektname" in eine spezielle Datei namens der MSSCCPRJ speichern. SCC-Datei. Es handelt es sich um eine lokale, für die clientseitige Datei, die im Besitz und vom plug-in verwaltet wird. Diese Datei befindet sich nie in der quellcodeverwaltung jedoch durch das plug-in für jedes Verzeichnis mit quellcodeverwaltete Dateien generiert. Um zu bestimmen, welche Dateien Visual Studio-Projektmappe und Projekt Dateien sind, kann ein Quellcodeverwaltungs-Plug-in die Erweiterungen, die mit einer Standard- oder benutzerdefinierte Liste vergleichen. Sobald die IDE erkennt, dass ein plug-in die MSSCCPRJ unterstützt. SCC-Datei, es wird nicht mehr zum Einbetten von der "AuxPath" und "Projektname" Zeichenfolgen in der Projektmappe und Projektdateien und liest diese Zeichenfolgen aus dem MSSCCPRJ. Die Datei stattdessen SCC.  
  
 Ein Quellcodeverwaltungs-Plug-in, das die MSSCCPRJ unterstützt. SCC-Datei muss die folgenden Richtlinien befolgen:  
  
-   Es kann nur eine MSSCCPRJ vorhanden sein. SCC-Datei pro Verzeichnis.  
  
-   Ein MSSCCPRJ. SCC-Datei kann die "AuxPath" und "Projektname" für mehrere Dateien enthalten, die in der quellcodeverwaltung innerhalb eines bestimmten Verzeichnisses sind.  
  
-   Die Zeichenfolge "AuxPath" darf nicht mit Anführungszeichen darin sein. Es ist zulässig, haben Anführungszeichen als Trennzeichen (z. B. ein Paar von Anführungszeichen kann an, dass eine leere Zeichenfolge verwendet werden). Die IDE entfernt alle Anführungszeichen in der Zeichenfolge "AuxPath" beim Lesen aus der MSSCCPRJ. SCC-Datei.  
  
-   Die Zeichenfolge "Projektname" in der MSSCCPRJ. SCC-Datei übereinstimmen genau mit die Zeichenfolge zurückgegeben, die von der `SccGetProjPath` Funktion. Wenn die Zeichenfolge, die von der Funktion zurückgegebenen Anführungszeichen, die Zeichenfolge in der MSSCCPRJ verfügt. SCC-Datei müssen die Anführungszeichen umgeben (und umgekehrt).  
  
-   Ein MSSCCPRJ. SCC-Datei erstellt oder aktualisiert, sobald eine Datei unter quellcodeverwaltung gestellt wird.  
  
-   Wenn ein MSSCCPRJ. Ruft SCC-Datei gelöscht wird, ein Anbieter sollten neu generieren sie das nächste Mal eine Quelle-Steuerungsvorgang zu diesem Verzeichnis ausgeführt.  
  
-   Ein MSSCCPRJ. SCC-Datei muss streng definierte Format entsprechen.  
  
## <a name="an-illustration-of-the-mssccprjscc-file-format"></a>Eine Abbildung der MSSCCPRJ. SCC-Dateiformat  
 Es folgt ein Beispiel für die MSSCCPRJ. SCC-Dateiformat (die Zeilennummern werden nur dienen zur Orientierung und sollte nicht in der Datei Text enthalten sein):  
  
 [Zeile 1]`SCC = This is a Source Code Control file`  
  
 [Zeile 2]  
  
 [Zeile 3]`[TestApp.sln]`  
  
 [Zeile 4]`SCC_Aux_Path = "\\server\vss\"`  
  
 [Zeile 5]`SCC_Project_Name = "$/TestApp"`  
  
 [Zeile 6]  
  
 [Zeile 7]`[TestApp.csproj]`  
  
 [Zeile 8]`SCC_Aux_Path = "\\server\vss\"`  
  
 [Zeile 9]`SCC_Project_Name = "$/TestApp"`  
  
 Die erste Zeile gibt den Zweck der Datei und dient als die Signatur für alle Dateien dieses Typs. Diese Zeile sollte genau wie folgt in alle MSSCCPRJ angezeigt werden. SCC-Dateien:  
  
 `SCC = This is a Source Code Control file`  
  
 Im folgenden ist ein Abschnitt der Einstellungen für jede Datei im Dateinamen in eckige Klammern gekennzeichnet. In diesem Abschnitt wird für jede Datei, die nachverfolgt wird wiederholt. Diese Zeile ist ein Beispiel eines Dateinamens, nämlich `[TestApp.csproj]`. Die IDE erwartet die folgenden zwei Zeilen. Die Art des definierten Werte werden jedoch nicht definiert. Die Variablen sind `SCC_Aux_Path` und `SCC_Project_Name`.  
  
 `SCC_Aux_Path = "\\server\vss\"`  
  
 `SCC_Project_Name = "$/TestApp"`  
  
 Es gibt keine End-Trennzeichen, das in diesem Abschnitt. Der Name der Datei sowie alle Literale, die in der Datei angezeigt werden, werden in der Headerdatei scc.h definiert. Weitere Informationen finden Sie unter [Zeichenfolgen, die als Schlüssel für die Suche nach einer Quelle Steuerelement-Plug-in verwendeten](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Datenquellen-Steuerelement-Plug-ins](../extensibility/source-control-plug-ins.md)   
 [Als Schlüssel zum Suchen eines Quellcodeverwaltungs-Plug-Ins verwendete Zeichenfolgen](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)
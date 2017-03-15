---
title: "MSSCCPRJ. SCC-Datei | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Quellcode-Plug-ins MSSCCPRJ. SCC-Datei"
  - "MSSCCPRJ. SCC-Datei"
ms.assetid: 6f2e39d6-b79d-407e-976f-b62a3cedd378
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# MSSCCPRJ. SCC-Datei
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Wenn eine Visual Studio\-Projektmappe oder ein Projekt unter Versionskontrolle mithilfe der IDE eingefügt wird, empfängt die IDE zwei wesentliche Informationen aus dem Quellsteuerelement\-Plug\-in Form von Zeichenfolgen. Diese Zeichenfolgen "AuxPath" und "Projektname", sind für die IDE nicht transparent, aber sie werden durch das plug\-in verwendet, in der Versionskontrolle die Projektmappe oder das Projekt zu suchen. Die IDE in der Regel enthält diese Zeichenfolgen erstmals durch Aufrufen der [SccGetProjPath](../extensibility/sccgetprojpath-function.md), und er speichert sie anschließend in der Projektmappe oder das Projekt Datei bei nachfolgenden Aufrufen der [SccOpenProject](../extensibility/sccopenproject-function.md). Wenn in der Projektmappe und Projekt eingebettet ist, werden die Zeichenfolgen "AuxPath" und "Projektname" nicht automatisch aktualisiert, wenn ein Benutzer, Zweige verzweigt, oder Projektmappen\- und Projektdateien Dateien kopiert, die in der Versionskontrolle sind. Um sicherzustellen, dass es am richtigen Speicherort in der Versionskontrolle die Projektmappe und Dateien auf, müssen Benutzer die Zeichenfolgen manuell aktualisieren. Da die Zeichenfolgen nicht transparent sein sollen, immer löschen möglicherweise nicht wie diese aktualisiert werden sollen.  
  
 Das Quellcodeverwaltungs\-Plug\-in kann dieses Problem vermeiden, indem Sie die Zeichenfolgen "AuxPath" und "Projektname" in eine spezielle Datei namens der MSSCCPRJ speichern. SCC\-Datei. Es handelt es sich um eine lokale, clientseitige\-Datei, die im Besitz und vom plug\-in gewartet wird. Diese Datei befindet sich nie in einem Quellcodeverwaltungsprojekt jedoch wird generiert, indem das plug\-in für jedes Verzeichnis, quellcodeverwaltete Dateien enthält. Um zu bestimmen, welche Dateien über Visual Studio\-Projektmappe und Dateien sind, kann ein Quellcodeverwaltungs\-Plug\-in die Erweiterungen für eine standardmäßige oder benutzerdefinierte Liste vergleichen. Sobald die IDE erkennt, dass ein plug\-in die MSSCCPRJ unterstützt. SCC\-Datei, sie ist nicht mehr zum Einbetten der "AuxPath" und "Projektname" Zeichenfolgen in Projektmappen und Projektdateien und es liest diese Zeichenfolgen aus dem MSSCCPRJ. Stattdessen SCC\-Datei.  
  
 Ein Quellcodeverwaltungs\-Plug\-in, das die MSSCCPRJ unterstützt. SCC\-Datei müssen Sie die folgenden Richtlinien halten:  
  
-   Es kann nur eine MSSCCPRJ vorhanden sein. SCC\-Datei pro Verzeichnis.  
  
-   Ein MSSCCPRJ. SCC\-Datei kann die "AuxPath" und "Projektname" für mehrere Dateien enthalten, in der Datenquellen\-Steuerelement in einem angegebenen Verzeichnis befinden.  
  
-   Die Zeichenfolge "AuxPath" darf keine Anführungszeichen darin haben. Es ist zulässig, haben Anführungszeichen als Trennzeichen \(z. B. ein Paar von Anführungszeichen kann an, dass eine leere Zeichenfolge verwendet werden\). Die IDE entfernt alle Angebote aus der Zeichenfolge "AuxPath" beim Lesen aus der MSSCCPRJ. SCC\-Datei.  
  
-   Die Zeichenfolge "Projektname" in der MSSCCPRJ. SCC\-Datei muss genau mit die von zurückgegebene Zeichenfolge entsprechen den `SccGetProjPath` Funktion. Wenn die von der Funktion zurückgegebene Zeichenfolge Anführungszeichen, die Zeichenfolge in der MSSCCPRJ hat. SCC\-Datei müssen die Anführungszeichen umgeben, und umgekehrt.  
  
-   Ein MSSCCPRJ. SCC\-Datei erstellt oder aktualisiert, sobald eine Datei unter quellcodeverwaltung gespeichert wird.  
  
-   Wenn ein MSSCCPRJ. SCC\-Datei gelöscht wird, ein Anbieter sollten neu generieren sie das nächste Mal, das es eine Datenquellen\-Steuerelement für dieses Verzeichnis ausführt.  
  
-   Ein MSSCCPRJ. SCC\-Datei muss genau definierte Format entsprechen.  
  
## Eine Abbildung der MSSCCPRJ. SCC\-Dateiformat  
 Es folgt ein Beispiel für die MSSCCPRJ. SCC\-Dateiformat \(die Zeilennummern werden nur als Leitfaden bereitgestellt und sollte nicht in der Datei Text enthalten sein\):  
  
 \[Zeile 1\] `SCC = This is a Source Code Control file`  
  
 \[Zeile 2\]  
  
 \[Zeile 3\] `[TestApp.sln]`  
  
 \[Zeile 4\] `SCC_Aux_Path = "\\server\vss\"`  
  
 \[Zeile 5\] `SCC_Project_Name = "$/TestApp"`  
  
 \[Zeile 6\]  
  
 \[Zeile 7\] `[TestApp.csproj]`  
  
 \[Zeile 8\] `SCC_Aux_Path = "\\server\vss\"`  
  
 \[Zeile 9\] `SCC_Project_Name = "$/TestApp"`  
  
 Die erste Zeile den Zweck der Datei und dient als die Signatur für alle Dateien dieses Typs. Diese Zeile sollte genau so in alle MSSCCPRJ angezeigt werden. SCC\-Dateien:  
  
 `SCC = This is a Source Code Control file`  
  
 Im folgenden ist ein Abschnitt der Einstellungen für jede Datei, die vom Dateinamen in eckige Klammern gekennzeichnet. In diesem Abschnitt wird für jede Datei, die nachverfolgt wird wiederholt. Diese Zeile ist ein Beispiel für einen Dateinamen ein, d. h. `[TestApp.csproj]`. Die IDE erwartet, dass die folgenden beiden Zeilen. Das Format der definierten Werte werden jedoch nicht definiert. Die Variablen sind `SCC_Aux_Path` und `SCC_Project_Name`.  
  
 `SCC_Aux_Path = "\\server\vss\"`  
  
 `SCC_Project_Name = "$/TestApp"`  
  
 Es gibt keine End\-Trennzeichen, das in diesem Abschnitt. Der Name der Datei sowie alle Literale, die in der Datei angezeigt werden, werden in der Headerdatei scc.h definiert. Weitere Informationen finden Sie unter [Zeichenfolgen, die als Schlüssel für ein Quellcodeverwaltungs\-Plug\-in zu suchen](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md).  
  
## Siehe auch  
 [Source Control\-Plug\-ins](../extensibility/source-control-plug-ins.md)   
 [Zeichenfolgen, die als Schlüssel für ein Quellcodeverwaltungs\-Plug\-in zu suchen](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)
---
title: "MSBuild Tasks Specific to Visual C++ | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild, tasks specific to Visual C++"
ms.assetid: 05410f0c-7356-4692-bc00-20664421c9ff
caps.latest.revision: 7
caps.handback.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# MSBuild Tasks Specific to Visual C++
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Aufgaben stellen den Code bereit, der während des Buildprozesses ausgeführt wird.  Wenn Visual C\+\+ installiert ist, sind die folgenden Aufgaben, zusätzlich zu den verfügbar, die mit [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] installiert werden.  Weitere Informationen finden Sie unter [Übersicht über MSBuild \(Visual C\+\+\)](/visual-cpp/build/msbuild-visual-cpp-overview).  
  
 Zusätzlich zu den Parametern der einzelnen Aufgaben verfügt jede Aufgabe auch über die folgenden Parameter.  
  
|Parameter|Description|  
|---------------|-----------------|  
|`Condition`|Optionaler `String`\-Parameter.<br /><br /> Ein `Boolean`\-Ausdruck, mit dem vom [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]\-Modul ermittelt wird, ob diese Aufgabe ausgeführt wird.  Weitere Informationen zu den Bedingungen, die von [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] unterstützt werden, finden Sie unter [Conditions](../msbuild/msbuild-conditions.md).|  
|`ContinueOnError`|Optionaler \- Parameter.  Kann einen der folgenden Werte enthalten:<br /><br /> -   **WarnAndContinue** oder **true**.  Wenn eine Aufgabe fehlschlägt, werden folgende Aufgaben im [Ziel](../msbuild/target-element-msbuild.md)\-Element und im Build fort, um auszuführen, und alle Fehler von der Aufgabe werden als Warnungen behandelt<br />-   **ErrorAndContinue**.  Wenn eine Aufgabe fehlschlägt, werden folgende Aufgaben im `Target`\-Element und im Build fort, um auszuführen, und alle Fehler von der Aufgabe werden als Fehler behandelt.<br />-   **ErrorAndStop** oder **false** \(Standard\).  Wenn eine Aufgabe fehlschlägt, werden die übrigen Aufgaben im `Target`\-Element und im Build nicht ausgeführt, und das gesamte `Target`\-Element und der Build werden erwogen fehlgeschlagen sein.<br /><br /> .NET Framework\-Versionen vor 4,5 unterstützten nur die `true` und `false`\-Werte.<br /><br /> Weitere Informationen finden Sie unter [How to: Ignore Errors in Tasks](../msbuild/how-to-ignore-errors-in-tasks.md).|  
  
## Verwandte Themen  
  
|Titel|Description|  
|-----------|-----------------|  
|[BscMake Task](../msbuild/bscmake-task.md)|Umschließt das Microsoft\-Wartungshilfsprogramm zum Durchsuchen von Informationen \("bscmake.exe"\).|  
|[CL Task](../msbuild/cl-task.md)|Umschließt das Visual C\+\+\-Compilertool \("cl.exe"\).|  
|[CPPClean Task](../msbuild/cppclean-task.md)|Löscht die temporären Dateien, die MSBuild erstellt, wenn ein Visual C\+\+\-Projekt erstellt wird.|  
|[LIB Task](../msbuild/lib-task.md)|Umschließt das 32\-Bit\-Tool von Microsoft zur Bibliotheksverwaltung \("lib.exe"\).|  
|[Link Task](../msbuild/link-task.md)|Umschließt das Visual C\+\+\-Linkertool \("link.exe"\).|  
|[MIDL Task](../msbuild/midl-task.md)|Umschließt das MIDL \(Microsoft Interface Definition Language\)\-Compilertool \("midl.exe"\).|  
|[MT Task](../msbuild/mt-task.md)|Umschließt das Microsoft Manifest\-Tool \("mt.exe"\).|  
|[RC Task](../msbuild/rc-task.md)|Umschließt das Microsoft Windows\-Ressourcencompilertool \("rc.exe"\).|  
|[SetEnv Task](../msbuild/setenv-task.md)|Legt den Wert einer angegebenen Umgebungsvariablen fest oder löscht ihn.|  
|[VCMessage Task](../msbuild/vcmessage-task.md)|Protokolliert Warn\- und Fehlermeldungen während eines Builds.|  
|[XDCMake Task](../msbuild/xdcmake-task.md)|Umschließt das XML\-Dokumentationstool \("xdcmake.exe"\), das XML\-Dokument\-Kommentardateien \(.xdc\) mit einer XML\-Datei zusammenführt.|  
|[XSD Task](../msbuild/xsd-task.md)|Umschließt das XML\-Schemadefinitionstool \(xsd.exe\), das Schema\- oder Klassendateien von einer Quelle generiert.|  
|[MSBuild Reference](../msbuild/msbuild-reference.md)|Beschreibt die Elemente des MSBuild\-Systems.|  
|[Tasks](../msbuild/msbuild-tasks.md)|Beschreibt Aufgaben, die Einheiten von Code darstellen und zum Erstellen eins Build kombiniert werden können.|  
|[Task Writing](../msbuild/task-writing.md)|Beschreibt das Erstellen einer Aufgabe.|
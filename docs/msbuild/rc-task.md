---
title: "RC Task | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCResourceCompilerTool.UndefineProcessorDefinitions"
  - "vc.task.rc"
  - "VC.Project.VCResourceCompilerTool.SuppressStartupBanner"
  - "VC.Project.VCResourceCompilerTool.NullTerminateStrings"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
  - "C++"
helpviewer_keywords: 
  - "RC task (MSBuild (Visual C++))"
  - "MSBuild (Visual C++), RC task"
ms.assetid: 2fd26c75-a056-4dda-9f7e-2f90d3748d88
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 10
---
# RC Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Umschließt das Microsoft Windows\-Ressourcencompilertool \("rc.exe"\).  Die **RC**\-Aufgabe kompiliert Ressourcen, z. B. Cursor, Symbole, Bitmaps, Dialogfelder und Schriftarten in eine Ressourcendatei \(.res\).  Weitere Informationen finden Sie unter "Ressourcencompiler" auf der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737)\-Website.  
  
## Parameter  
 In der folgenden Tabelle werden die Parameter der RC\-Aufgabe beschrieben.  Die meisten Aufgabenparameter und einige Sätze von Parametern entsprechen einer Befehlszeilenoption.  
  
|Parameter|Beschreibung|  
|---------------|------------------|  
|**AdditionalIncludeDirectories**|Optionaler **String\[\]**\-Parameter.<br /><br /> Fügt ein Verzeichnis zur Verzeichnisliste hinzu, in der nach Includedateien gesucht wird.<br /><br /> Weitere Informationen finden Sie unter der Option **\/I** in [Using RC \(The RC Command Line\)](http://go.microsoft.com/fwlink/?LinkId=155730) auf der MSDN\-Website.|  
|**AdditionalOptions**|Optionaler **String**\-Parameter.<br /><br /> Eine Liste von Befehlszeilenoptionen oder \-beispielen, **"** *\/option1 \/option2 \/option\#*".  Verwenden Sie diesen Parameter, um Befehlszeilenoptionen anzugeben, die nicht von einem beliebigen anderen **RC**\-Aufgabenparameter dargestellt werden.<br /><br /> Weitere Informationen finden Sie unter den Optionen in [Using RC \(The RC Command Line\)](http://go.microsoft.com/fwlink/?LinkId=155730) auf der MSDN\-Website.|  
|**Culture**|Optionaler **String**\-Parameter.<br /><br /> Gibt eine Gebietsschema\-ID an, die die in der Ressource verwendete Kultur darstellt.<br /><br /> Weitere Informationen finden Sie unter der Option **\/l** in [Using RC \(The RC Command Line\)](http://go.microsoft.com/fwlink/?LinkId=155730) auf der MSDN\-Website.|  
|**IgnoreStandardIncludePath**|Optionaler **Boolean**\-Parameter.<br /><br /> Wenn `true`, wird verhindert, dass der Ressourcencompiler die INCLUDE\-Umgebungsvariable überprüft, wenn diese nach Headerdateien oder Ressourcendateien sucht.<br /><br /> Weitere Informationen finden Sie unter der Option **\/x** in [Using RC \(The RC Command Line\)](http://go.microsoft.com/fwlink/?LinkId=155730) auf der MSDN\-Website.|  
|**NullTerminateStrings**|Optionaler **Boolean**\-Parameter.<br /><br /> Wenn `true`, beendet NULL alle Zeichenfolgen in der Zeichenfolgentabelle.<br /><br /> Weitere Informationen finden Sie unter der Option **\/n** in [Using RC \(The RC Command Line\)](http://go.microsoft.com/fwlink/?LinkId=155730) auf der MSDN\-Website.|  
|**PreprocessorDefinitions**|Optionaler **String\[\]**\-Parameter.<br /><br /> Definieren Sie ein oder mehrere Präprozessorsymbole für den Ressourcencompiler.  Geben Sie eine Liste von Makrosymbolen an.<br /><br /> Weitere Informationen finden Sie unter der Option **\/d** in [Using RC \(The RC Command Line\)](http://go.microsoft.com/fwlink/?LinkId=155730) auf der MSDN\-Website.  Siehe auch **UndefinePreprocessorDefinitions** in dieser Tabelle.|  
|**ResourceOutputFileName**|Optionaler **String**\-Parameter.<br /><br /> Gibt den Namen der Ressourcendatei an.  Geben Sie einen Ressourcendateiname an.<br /><br /> Weitere Informationen finden Sie unter der Option **\/fo** in [Using RC \(The RC Command Line\)](http://go.microsoft.com/fwlink/?LinkId=155730) auf der MSDN\-Website.|  
|**ShowProgress**|Optionaler **Boolean**\-Parameter.<br /><br /> Wenn `true`, werden Meldungen angezeigt, die über den Status des Compilers berichten.<br /><br /> Weitere Informationen finden Sie unter der Option **\/v** in [Using RC \(The RC Command Line\)](http://go.microsoft.com/fwlink/?LinkId=155730) auf der MSDN\-Website.|  
|**Source**|Erforderlicher `ITaskItem[]`\-Parameter.<br /><br /> Definiert ein Array von MSBuild\-Quelldateielementen, die von Aufgaben aufgenommen und ausgegeben werden können.|  
|**SuppressStartupBanner**|Optionaler **Boolean**\-Parameter.<br /><br /> Bei `true` wird die Anzeige der Urheberrechts\- und Versionsnummernmeldung verhindert, wenn die Aufgabe startet.<br /><br /> Für weitere Informationen geben Sie **\/?** in der Befehlszeilenoption ein und sehen sich die **\/nologo**\-Option an.|  
|**TrackerLogDirectory**|Optionaler **String**\-Parameter.<br /><br /> Gibt das Verzeichnis des Protokolliererprotokolls an.|  
|**UndefinePreprocessorDefinitions**|Hebt die Definition für ein Präprozessorsymbol auf.<br /><br /> Weitere Informationen finden Sie unter der Option **\/u** in [Using RC \(The RC Command Line\)](http://go.microsoft.com/fwlink/?LinkId=155730) auf der MSDN\-Website.  Siehe auch **PreprocessorDefinitions** in dieser Tabelle.|  
  
## Hinweise  
  
## Siehe auch  
 [Task Reference](../msbuild/msbuild-task-reference.md)
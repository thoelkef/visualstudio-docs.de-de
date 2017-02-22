---
title: "XDCMake Task | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.task.xdcmake"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
  - "C++"
helpviewer_keywords: 
  - "XDCMake task (MSBuild (Visual C++))"
  - "MSBuild (Visual C++), XDCMake task"
ms.assetid: a7de9c64-903a-4a02-85f3-f37672270f25
caps.latest.revision: 7
caps.handback.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# XDCMake Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Umschließt das XML\-Dokumentationstool \("xdcmake.exe"\), das XML\-Dokument\-Kommentardateien \(.xdc\) mit einer XML\-Datei zusammenführt.  
  
 Eine XDC\-Datei wird erstellt, wenn Sie Dokumentationskommentare im Visual C\+\+\-Quellcode angeben und mit der [\/doc](/visual-cpp/build/reference/doc-process-documentation-comments-c-cpp)\-Compileroption kompilieren.  Weitere Informationen finden Sie unter [XDCMake\-Verweis](/visual-cpp/ide/xdcmake-reference), [Eigenschaftenseiten für das Tool XML\-Dokument\-Generator](/visual-cpp/ide/xml-document-generator-tool-property-pages) und der Befehlszeilenhilfeoption \(**\/?**\) für "xdcmake.exe".  
  
## Hinweise  
 Standardmäßig unterstützt das xdcmake.exe\-Tool einige Befehlszeilenoptionen.  Zusätzliche Optionen werden unterstützt, wenn Sie die **\/old**\-Befehlszeilenoption angeben.  
  
## Parameter  
 In der folgenden Tabelle werden die Parameter der **XDCMake**\-Aufgabe beschrieben.  
  
|Parameter|Beschreibung|  
|---------------|------------------|  
|**AdditionalDocumentFile**|Optionaler **String\[\]**\-Parameter.<br /><br /> Gibt eine oder mehrere weitere XDC\-Dateien zum Zusammenführen an.<br /><br /> Weitere Informationen finden Sie unter der Beschreibung **Zusätzliche Dokumentdateien** in [Eigenschaftenseiten für das Tool XML\-Dokument\-Generator](/visual-cpp/ide/xml-document-generator-tool-property-pages).  Sehen Sie auch in den **\/old**\- und **\/Fs** \-Befehlszeilenoptionen für "xdcmake.exe" nach.|  
|**AdditionalOptions**|Optionaler **String**\-Parameter.<br /><br /> Eine Liste von Optionen, wie in der Befehlszeile angegeben.  Beispiel: "*\/option1 \/option2 \/option\#*".  Verwenden Sie diesen Parameter, um Optionen anzugeben, die nicht von einem beliebigen anderen **XDCMake**\-Aufgabenparameter dargestellt werden.<br /><br /> Weitere Informationen finden Sie unter [XDCMake\-Verweis](/visual-cpp/ide/xdcmake-reference), [Eigenschaftenseiten für das Tool XML\-Dokument\-Generator](/visual-cpp/ide/xml-document-generator-tool-property-pages) und der Befehlszeilenhilfe \(**\/?**\) für "xdcmake.exe".|  
|**DocumentLibraryDependencies**|Optionaler **Boolean**\-Parameter.<br /><br /> Wenn `true` zutrifft und das aktuelle Projekt von einem Projekt einer statischen Bibliothek \(LIB\-Format\) in der Lösung abhängig ist, sind die XDC\-Dateien für dieses LIB\-Projekt in der XML\-Ausgabe für das aktuelle Projekt enthalten.<br /><br /> Weitere Informationen finden Sie unter der Beschreibung **Dokumentbibliothekabhängigkeiten** in [Eigenschaftenseiten für das Tool XML\-Dokument\-Generator](/visual-cpp/ide/xml-document-generator-tool-property-pages).|  
|**OutputFile**|Optionaler **String**\-Parameter.<br /><br /> Überschreibt den Standarddateinamen für die Ausgabe.  Der Standardname ist vom Namen der ersten XDC\-Datei abgeleitet, die verarbeitet wird.<br /><br /> Weitere Informationen finden Sie unter der Option **\/out:**`filename` in [XDCMake\-Verweis](/visual-cpp/ide/xdcmake-reference).  Sehen Sie auch in den **\/old**\- und **\/Fo** \-Befehlszeilenoptionen für "xdcmake.exe" nach.|  
|**ProjectName**|Optionaler **String**\-Parameter.<br /><br /> Der Name des aktuellen Projekts.|  
|**SlashOld**|Optionaler **Boolean**\-Parameter.<br /><br /> Wenn `true`, werden zusätzliche xdcmake.exe\-Optionen aktiviert.<br /><br /> Weitere Informationen finden Sie in der **\/old**\-Befehlszeilenoption für "xdcmake.exe".|  
|**Sources**|Erforderlicher `ITaskItem[]`\-Parameter.<br /><br /> Definiert ein Array von MSBuild\-Quelldateielementen, die von Aufgaben aufgenommen und ausgegeben werden können.|  
|**SuppressStartupBanner**|Optionaler **Boolean**\-Parameter.<br /><br /> Bei `true` wird die Anzeige der Urheberrechts\- und Versionsnummernmeldung verhindert, wenn die Aufgabe startet.<br /><br /> Weitere Informationen finden Sie unter der Option **\/nologo** in [XDCMake\-Verweis](/visual-cpp/ide/xdcmake-reference).|  
|**TrackerLogDirectory**|Optionaler **String**\-Parameter.<br /><br /> Gibt das Verzeichnis für das Protokolliererprotokoll an.|  
  
## Siehe auch  
 [Task Reference](../msbuild/msbuild-task-reference.md)
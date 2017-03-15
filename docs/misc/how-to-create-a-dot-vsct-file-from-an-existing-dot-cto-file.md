---
title: "Gewusst wie: Erstellen einer VSCT-Datei anhand einer vorhandenen CTO-Datei | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSCT-Dateien, anhand einer CTO-Datei erstellen"
ms.assetid: 847717c9-477d-4ac9-8b2c-2da878912478
caps.latest.revision: 11
caps.handback.revision: 11
manager: "douge"
---
# Gewusst wie: Erstellen einer VSCT-Datei anhand einer vorhandenen CTO-Datei
Sie können eine XML\-basierte VSCT\-Datei anhand einer vorhandenen binären CTO\-Datei erstellen. Diese Vorgehensweise ermöglicht es Ihnen, das neue Befehlstabellen\-Compilerformat zu nutzen. Dies funktioniert sogar, wenn die CTO\-Datei aus einer CTC\-Datei kompiliert wurde. Sie können die VSCT\-Datei bearbeiten und in eine andere CTO\-Datei kompilieren.  
  
### So erstellen Sie eine VSCT\-Datei anhand einer CTO\-Datei  
  
1.  Erstellen Sie Kopien der CTO\-Datei und der zugehörigen .CRSYM\-Datei.  
  
2.  Platzieren Sie die Dateien in dem Verzeichnis, in dem sich der Compiler „vsct.exe“ befindet.  
  
3.  Navigieren Sie an der Visual Studio\-Eingabeaufforderung zu dem Verzeichnis, das die CTO\- und die CTSYM\-Datei enthält.  
  
4.  Geben Sie **vsct.exe** *ctofilename***.cto** *vsctfilename***.vsct \-S***symfilename***.ctsym** ein.  
  
     `ctofilename` ist der Name der CTO\-Datei, `vsctfilename` ist der Name der VSCT\-Datei, die Sie erstellen möchten, und `symfilename` ist der Name der CTSYMDatei.  
  
     Bei diesem Vorgang wird eine neue VSCT\-XML\-Befehlstabellen\-Compilerdatei erstellt. Sie können die Datei mit „vsct.exe“, dem vsct\-Compiler, wie jede andere VSCT\-Datei bearbeiten und kompilieren.  
  
## Siehe auch  
 [Gewusst wie: Erstellen einer. VSCT\-Datei](../extensibility/internals/how-to-create-a-dot-vsct-file.md)   
 [Visual Studio\-Befehl\-Tabelle \(. VSCT\) Dateien](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
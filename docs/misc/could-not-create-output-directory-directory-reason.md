---
title: "Could not create output directory &#39;directory&#39;. &lt;reason&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.cannot_create_output_dir"
ms.assetid: b4d1d19f-f582-49d0-a9a9-d3f4ce0a447b
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Could not create output directory &#39;directory&#39;. &lt;reason&gt;
Das Projektsystem konnte kein Projektverzeichnis erstellen.  
  
 Das Projektsystem versucht, alle Ausgabeverzeichnisse zu erstellen, sobald das Projekt geöffnet wird.  Hier sehen Sie eine Liste der Ausgabeverzeichnisse, die vom Projektsystem erstellt wurden:  
  
 *Projektordner*\\obj\\`configname`  
 Ein temporäres, konfigurationsspezifisches Ausgabeverzeichnis.  
  
 *Projektordner*\\obj\\`configname`\\temp  
 Arbeitsbereich des Compilers.  
  
 *Projektordner*\\obj\\`configname`\\temppe  
 Hier werden temporäre Assemblys, die von Entwicklern zur Entwurfszeit verwendet werden, erstellt.  
  
 outputdir  
 Das von der **OutputPath**\-Eigenschaft angegebene Verzeichnis.  Weitere Informationen finden Sie unter [Seite "Erstellen", Projekt\-Designer \(C\#\)](../ide/reference/build-page-project-designer-csharp.md).  
  
 Die häufigste Ursache dafür, dass das Erstellen eines Verzeichnisses unter dem Ordner **obj** fehlschlägt, ist die Überschreitung der MAX\_PATH\-Begrenzung für Verzeichnisnamen.  
  
 Weniger häufige Ursachen sind die Zugriffsverweigerung oder unzureichender Speicherplatz.  
  
 **So beheben Sie diesen Fehler**  
  
-   Wenn der Pfad zu lang ist, ändern Sie das Projektverzeichnis oder kürzen den Namen der Projektkonfiguration.  
  
     Der Buildprozess schlägt fehl, wenn dieser Fehler auftritt.  
  
## Siehe auch  
 [NIB How to: Modify Project Properties and Configuration Settings](http://msdn.microsoft.com/de-de/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)
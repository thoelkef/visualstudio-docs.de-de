---
title: "Cannot copy multifile assembly &#39;assembly&#39; to directory &#39;directory&#39;. &lt;reason&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.cannotcopyscatterassembly"
ms.assetid: 939519c7-741d-4e05-8b63-71e39fb426ad
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Cannot copy multifile assembly &#39;assembly&#39; to directory &#39;directory&#39;. &lt;reason&gt;
Mehrfachdateiassemblys werden in ein Unterverzeichnis des Projektverzeichnisses kopiert, aus dem sie ausgeführt werden.  Wenn der Ausgabepfad z. B. c:\\project1\\bin lautet und eine Assembly \(deren `CopyLocal`\-Eigenschaft `true` lautet\) mit der Bezeichnung Test vorhanden ist, die die Dateien a.dll und b.dll enthält, erhalten Sie nach dem Kopieren folgende Dateistruktur:  
  
```  
c:\project1\bin\Test  
   c:\project1\bin\Test\Test.dll   (main assembly)  
   c:\project1\bin\Test\a.dll       (file a.dll)  
   c:\project1\bin\Test\b.dll       (file b.dll)  
```  
  
 Dieser Fehler wird vom Projektsystem angezeigt, wenn das Verzeichnis **c:\\project1\\bin\\Test** nicht auf der Festplatte erstellt werden konnte.  
  
 Dieser Fehler gibt an, dass der Speicherplatz nicht ausreicht oder die MAX\_PATH\-Begrenzung für die Pfadlänge überschritten wird.  
  
 **So beheben Sie diesen Fehler**  
  
-   Prüfen Sie den Speicherplatz.  
  
-   Verschieben Sie das Projekt in einen Ordner, dessen Pfad kürzer ist als der Pfad, in dem sich das Projekt gegenwärtig befindet.  
  
-   Wählen Sie für das Ausgabeverzeichnis einen Ordner mit einem kürzeren absoluten Pfad \(gilt nur für Clientprojekte\).  
  
## Siehe auch  
 [Problembehandlung bei fehlerhaften Verweisen](../ide/troubleshooting-broken-references.md)   
 [Gewusst wie: Hinzufügen oder Entfernen von Verweisen mithilfe des Dialogfelds "Verweise hinzufügen"](http://msdn.microsoft.com/de-de/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [Assemblies in the Common Language Runtime](http://msdn.microsoft.com/de-de/33a0bc6a-6bb3-44c7-ada7-4a046e8c0945)
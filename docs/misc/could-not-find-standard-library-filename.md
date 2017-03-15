---
title: "Die Standardbibliothek &quot;&lt;Dateiname&gt;&quot; wurde nicht gefunden. | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc40049"
  - "bc40049"
helpviewer_keywords: 
  - "BC40049"
ms.assetid: a292f97e-4852-4021-b300-7ab47beb95d9
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Die Standardbibliothek &quot;&lt;Dateiname&gt;&quot; wurde nicht gefunden.
[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] kann eine für die Kompilierung und Verknüpfung erforderliche DLL\-Standardbibliothek nicht finden oder öffnen.  
  
 Bei der nicht verwendbaren Bibliothek handelt es sich höchstwahrscheinlich um mscorlib.dll oder microsoft.visualbasic.dll.  
  
 Standardmäßig ist diese Meldung eine Warnung. Informationen zum Ausblenden von Warnungen oder zum Behandeln von Warnungen als Fehler finden Sie unter [Konfigurieren von Warnungen in Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Fehler\-ID:** BC40049  
  
### So beheben Sie diesen Fehler  
  
1.  Überprüfen Sie, ob die in der Fehlermeldung genannte Datei auf der Festplatte vorhanden ist, von der [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ausgeführt wird. In der Regel befinden sich die Standardbibliotheken in einem Unterverzeichnis unter \\WINNT\\Microsoft.NET\\Framework oder \\WINDOWS\\Microsoft.NET\\Framework.  
  
2.  Stellen Sie sicher, dass weder die Datei noch das Verzeichnis eine Einstellung oder ein Attribut aufweist, das den Lesezugriff durch [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] verhindert.  
  
3.  Stellen Sie sicher, dass Dateiname und Erweiterung richtig geschrieben sind. Groß\-\/Kleinschreibung ist nicht relevant.  
  
4.  Wenn sich die Datei im richtigen Verzeichnis befindet und für den Zugriff verfügbar zu sein scheint, ist sie möglicherweise auf dem Datenträger beschädigt. Installieren Sie [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] neu, falls dies möglich ist.  
  
5.  Notieren Sie sich den genauen Dateinamen und die Erweiterung, und wenden Sie sich an den Produktsupport von Microsoft.  
  
## Siehe auch  
 [Erstellen von der Befehlszeile aus](/dotnet/visual-basic/reference/command-line-compiler/building-from-the-command-line)   
 [How to: Invoke the Command\-Line Compiler](../Topic/How%20to:%20Invoke%20the%20Command-Line%20Compiler%20\(Visual%20Basic\).md)   
 [Sprechen Sie mit uns](../ide/talk-to-us.md)
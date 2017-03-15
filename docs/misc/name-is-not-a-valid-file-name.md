---
title: "&lt;name&gt; is not a valid file name. | Microsoft Docs"
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
  - "VS_E_INVALIDFILENAME"
  - "VS.Message.0x00006A72"
ms.assetid: c5969671-3b64-4854-acb6-328e8a30863f
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# &lt;name&gt; is not a valid file name.
Dieser Fehler tritt beim Versuch auf, eine neue Datei über das Befehlsfenster zu erstellen, wenn der Dateiname nicht unterstützte Zeichen enthält.  
  
 Die folgenden Zeichen dürfen in Dateinamen nicht enthalten sein:  
  
-   Nummernzeichen \(\#\)  
  
-   Prozent \(%\)  
  
-   Kaufmännisches Und\-Zeichen \(&\)  
  
-   Sternchen \(\*\)  
  
-   Senkrechter Strich \(&#124;\)  
  
-   Umgekehrter Schrägstrich \(\\\)  
  
-   Doppelpunkt \(:\)  
  
-   Doppeltes Anführungszeichen \("\)  
  
-   Kleiner als \(\<\)  
  
-   Größer als \(\>\)  
  
-   Punkt \(.\)  
  
-   Fragezeichen \(?\)  
  
-   Schrägstrich \(\/\)  
  
-   Führende oder nachfolgende Leerzeichen \(' '\)  
  
-   Von Windows oder DOS reservierte Namen  \(nul, aux, con, com1, lpt1 usw.\)  
  
### So beheben Sie diesen Fehler  
  
-   Geben Sie den Befehl mit einem neuen Dateinamen ein, in dem die oben aufgeführten Zeichen nicht enthalten sind.  
  
## Siehe auch  
 [Befehl "Neue Datei"](../ide/reference/new-file-command.md)   
 [Visual Studio\-Befehle](../ide/reference/visual-studio-commands.md)
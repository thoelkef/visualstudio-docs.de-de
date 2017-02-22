---
title: "Wie k&#246;nnen Funktionen der Windows-API gedebuggt werden? | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.api"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "APIs, Debuggen"
  - "Debuggen [C++], Windows-API-Funktionen"
  - "NT-Symbole und Debuggen von Windows API-Funktionen"
  - "Windows-API-Funktionen, Debuggen"
  - "Windows-API, Debuggen von API-Funktionen"
ms.assetid: 7c126f57-62ab-4d94-9805-632d696ba1f0
caps.latest.revision: 20
caps.handback.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Wie k&#246;nnen Funktionen der Windows-API gedebuggt werden?
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Wenn Sie eine Windows API\-Funktion debuggen möchten, in der NT\-Symbole geladen sind, müssen Sie wie im Folgenden beschrieben vorgehen.  
  
### So legen Sie einen Haltepunkt für eine Windows API\-Funktion mit NT\-Symbolen fest  
  
-   Geben Sie den Namen der Funktion und den Namen der DLL ein, in der sich die Funktion befindet.  Verwenden Sie im 32\-Bit\-Code die ergänzte Form des Funktionsnamens.  Zum Festlegen eines Haltepunkts für **MessageBeep** müssen Sie z. B. Folgendes eingeben:  
  
    ```  
    {,,USER32.DLL}_MessageBeep@4  
    ```  
  
     Informationen zum Abrufen des ergänzten Namens finden Sie unter [Viewing Decorated Names](http://msdn.microsoft.com/de-de/f79e2717-a4db-4d12-a689-69830cce2be0).  
  
## Siehe auch  
 [FAQs zum Debuggen von systemeigenem Code](../debugger/debugging-native-code-faqs.md)   
 [Debuggen von systemeigenem Code](../debugger/debugging-native-code.md)
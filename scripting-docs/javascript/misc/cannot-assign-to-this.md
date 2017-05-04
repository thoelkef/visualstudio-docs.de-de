---
title: "Die Zuweisung zu &quot;this&quot; ist nicht m&#246;glich | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.WebClient.Help.SCRIPT5000"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: ba2b0a2b-f0f8-4698-b335-a4ab6c166671
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Die Zuweisung zu &quot;this&quot; ist nicht m&#246;glich
Sie haben versucht, **this** einen Wert zuzuweisen.  **this** ist ein [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]\-Schlüsselwort, das auf Folgendes verweisen kann:  
  
-   das Objekt, das derzeit eine Methode ausführt, oder  
  
-   das globale Objekt, wenn keine aktuelle Methode vorhanden ist \(oder die Methode zu keinem anderen Objekt gehört\).  
  
 Eine Methode ist eine [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]\-Funktion, die über ein Objekt aufgerufen wird.  Das **this**\-Schlüsselwort ist in einer Methode ein Verweis auf das Objekt, über das die Methode aufgerufen wurde. Dies ist das Objekt, das durch Aufrufen des Klassenkonstruktors mit dem **new**\-Operator erstellt wurde.  
  
 In einer Methode können Sie mit **this** auf das aktuelle Objekt verweisen. Sie können **this** jedoch keinen neuen Wert zuweisen.  
  
### So beheben Sie diesen Fehler  
  
-   Versuchen Sie nicht, **this** etwas zuzuweisen.  Verwenden Sie den Punktoperator \(z.B. circle**.**radius\), um auf eine Eigenschaft oder Methode eines instanziierten Objekts zuzugreifen.  
  
    > [!NOTE]
    >  Sie können eine vom Benutzer erstellte Variable nicht mit **this** benennen, da dies in [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] ein reserviertes Wort ist.  
  
## Siehe auch  
 [this\-Anweisung](../../javascript/reference/this-statement-javascript.md)   
 [Problembehandlung bei Skripts](../../javascript/advanced/troubleshooting-your-scripts-javascript.md)
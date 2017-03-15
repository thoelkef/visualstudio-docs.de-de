---
title: "Der &lt;typ&gt; &#39;&lt;typname&gt;&#39; f&#252;hrt Shadowing f&#252;r eine &#252;berschreibbare Methode in der Basisklasse aus | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc40005"
  - "bc40005"
helpviewer_keywords: 
  - "BC40005"
ms.assetid: 1dadda7f-1d26-4ae8-a668-9f69d55ceb50
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Der &lt;typ&gt; &#39;&lt;typname&gt;&#39; f&#252;hrt Shadowing f&#252;r eine &#252;berschreibbare Methode in der Basisklasse aus
Der \<typ\> '\<typname\>' führt Shadowing für eine überschreibbare Methode in der Basisklasse aus. Wenn Sie die Basismethode überschreiben möchten, muss die Methode als 'Overrides' deklariert sein.  
  
 Ein Programmierelement wird mit demselben Namen wie eine überschreibbare Prozedur oder Eigenschaft deklariert, die in der Basisklasse definiert ist. In diesem Fall muss das Element in dieser Klasse Shadowing für das Element der Basisklasse ausführen.  
  
 Standardmäßig ist diese Meldung eine Warnung. Weitere Informationen zum Ausblenden von Warnungen oder zum Behandeln von Warnungen als Fehler finden Sie unter [Konfigurieren von Warnungen in Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Fehler\-ID:** BC40005  
  
### So beheben Sie diesen Fehler  
  
-   Wenn Sie die Basisprozedur überschreiben möchten, fügen Sie das Schlüsselwort `Overrides` zur Deklaration hinzu.  
  
-   Wenn Sie Shadowing für die Basisprozedur ausführen möchten, fügen Sie der Deklaration des Schlüsselwort `Shadows` hinzu.  
  
-   Wenn Sie weder Überschreiben noch Shadowing ausführen möchten, ändern Sie den Namen des deklarierten Elements.  
  
## Siehe auch  
 [NICHT IM BUILD: Überschreiben von Eigenschaften und Methoden](http://msdn.microsoft.com/de-de/2167e8f5-1225-4b13-9ebd-02591ba90213)   
 [Shadowing in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/declared-elements/shadowing)   
 [Overrides](/dotnet/visual-basic/language-reference/modifiers/overrides)   
 [Shadows](/dotnet/visual-basic/language-reference/modifiers/shadows)
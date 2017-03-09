---
title: "Unzul&#228;ssige Verwendung des Schl&#252;sselworts &lt;Schl&#252;sselwort&gt; in einem Modul | Microsoft Docs"
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
  - "vbc42028"
  - "BC42028"
helpviewer_keywords: 
  - "BC42028"
ms.assetid: a9bc1e9d-ba2c-4a71-b147-0fb66f670316
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Unzul&#228;ssige Verwendung des Schl&#252;sselworts &lt;Schl&#252;sselwort&gt; in einem Modul
Module verfügen nicht über Instanzen, unterstützen keine Vererbung und implementieren keine Schnittstellen. Daher gelten die folgenden Schlüsselwörter nicht für eine Moduldeklaration:  
  
-   [MustInherit](/dotnet/visual-basic/language-reference/modifiers/mustinherit)  
  
-   [NotInheritable](/dotnet/visual-basic/language-reference/modifiers/notinheritable)  
  
-   [Overloads](/dotnet/visual-basic/language-reference/modifiers/overloads)  
  
-   [Private](/dotnet/visual-basic/language-reference/modifiers/private)  
  
-   [Protected](/dotnet/visual-basic/language-reference/modifiers/protected)  
  
-   [Shadows](/dotnet/visual-basic/language-reference/modifiers/shadows)  
  
-   [Shared](/dotnet/visual-basic/language-reference/modifiers/shared)  
  
-   [Static](/dotnet/visual-basic/language-reference/modifiers/static)  
  
 Die einzigen Schlüsselwörter, die in einer [Module Statement](/dotnet/visual-basic/language-reference/statements/module-statement) unterstützt werden, sind [Public](/dotnet/visual-basic/language-reference/modifiers/public) und [Friend](/dotnet/visual-basic/language-reference/modifiers/friend).  
  
 Darüber hinaus können Sie die [Implements](/dotnet/visual-basic/language-reference/statements/implements-clause)\-Anweisung oder die [Inherits Statement](/dotnet/visual-basic/language-reference/statements/inherits-statement) im Anweisungsblock des Moduls nicht verwenden.  
  
 Standardmäßig ist diese Meldung eine Warnung. Weitere Informationen zum Ausblenden von Warnungen und zum Behandeln von Warnungen als Fehler finden Sie unter [Konfigurieren von Warnungen in Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Fehler\-ID:** BC42028  
  
### So beheben Sie diesen Fehler  
  
-   Wenn dieses Programmierelement ein Modul sein soll, verwenden Sie nur das `Public`\- oder `Friend`\-Schlüsselwort in der Deklaration. Standardmäßig verwendet ein Modul `Friend`, wenn Sie keine Zugriffsebene angeben.  
  
-   Wenn Sie Instanzen dieses Programmierelements erstellen möchten, deklarieren Sie es als Klasse. Sie können dann die Schlüsselwörter verwenden, die für eine Klassendeklaration gelten.  
  
## Siehe auch  
 [Class Statement](/dotnet/visual-basic/language-reference/statements/class-statement)
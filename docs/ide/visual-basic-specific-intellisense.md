---
title: "Visual&#160;Basic-spezifisches IntelliSense | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IntelliSense [Visual Basic]"
  - "IntelliSense [Visual Studio], Visual Basic"
ms.assetid: 4dec8753-05e5-4f74-b304-5f8c4ed8723b
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 10
---
# Visual&#160;Basic-spezifisches IntelliSense
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Der Visual Basic\-Quellcode\-Editor unterstützt die folgenden IntelliSense\-Features:  
  
-   Syntaxtipps  
  
     Syntaxtipps enthalten die Syntax der Anweisung, die gerade eingegeben wird.  Dies ist nützlich für Anweisungen, z. B. [Declare](/dotnet/visual-basic/language-reference/statements/declare-statement).  
  
## Automatische Vervollständigung  
  
-   Anweisungsvervollständigung bei verschiedenen Schlüsselwörtern  
  
     Wenn Sie z. B. `goto` und ein Leerzeichen eingeben, zeigt IntelliSense in einem Dropdownmenü eine Liste der definierten Marken an.  Andere unterstützte Schlüsselwörter sind `Exit`, `Implements`, `Option` und `Declare`.  
  
-   Anweisungsvervollständigung bei `Enum` und `Boolean`  
  
     Wenn eine Anweisung auf einen Member innerhalb einer Enumeration verweist, zeigt IntelliSense eine Liste der Member von `Enum` an.  Wenn eine Anweisung auf ein `Boolean`\-Objekt verweist, zeigt IntelliSense ein True\-False\-Dropdownmenü an.  
  
 Die Vervollständigung kann standardmäßig deaktiviert sein. Dazu deaktivieren Sie im Ordner **Visual Basic** auf der Eigenschaftenseite **Allgemein** das Kontrollkästchen **Member automatisch auflisten**.  
  
 Durch Aufrufen von Member auflisten, Wort vervollständigen oder ALT \+ nach\-rechts\-Pfeil können Sie manuell Abschluss aufrufen.  Weitere Informationen finden Sie unter [Verwenden von IntelliSense](../ide/using-intellisense.md).  
  
## IntelliSense pro Zone  
 IntelliSense pro Zone unterstützt Visual Basic\-Entwickler, die Anwendungen über [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] bereitstellen müssen und auf teilweise vertrauenswürdige Einstellungen beschränkt sind.  Dieses Feature ermöglicht Ihnen:  
  
-   Auswählen der Berechtigungen, mit denen die Anwendung ausgeführt wird  
  
-   Anzeigen von APIs in der ausgewählten Zone unter Member auflisten als verfügbar sowie Anzeigen von APIs, die zusätzliche Berechtigungen erfordern, als nicht verfügbar  
  
 Weitere Informationen finden Sie unter [Codezugriffssicherheit für ClickOnce\-Anwendungen](../deployment/code-access-security-for-clickonce-applications.md).  
  
## Siehe auch  
 [Verwenden von IntelliSense](../ide/using-intellisense.md)
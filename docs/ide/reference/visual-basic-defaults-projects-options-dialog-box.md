---
title: "VB-Standard, Projekte, Dialogfeld &quot;Optionen&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ToolsOptionsPages.Projects.VBDefaults"
helpviewer_keywords: 
  - "Option Explicit-Anweisung, Festlegen in der IDE"
  - "Option Compare-Anweisung, Festlegen in der IDE"
  - "Option Strict-Anweisung, Festlegen in der IDE"
ms.assetid: 2465cd9d-18b6-4c4a-b1ea-86dbab23fc79
caps.latest.revision: 19
caps.handback.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# VB-Standard, Projekte, Dialogfeld &quot;Optionen&quot;
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Gibt die Standardeinstellungen für Visual Basic\-Projektoptionen an.  Bei der Erstellung eines neues Projekts werden die angegebenen `Option`\-Anweisungen im Code\-Editor zum Projektheader hinzugefügt.  Diese Optionen gelten für alle Visual Basic\-Projekte.  
  
 Klicken Sie zum Öffnen dieses Dialogfelds im Menü **Extras** auf **Optionen**, erweitern Sie den Ordner **Projekte und Projektmappen**, und klicken Sie auf **VB\-Standard**.  
  
 **Option Explicit**  
 Legt den Compilerstandard so fest, dass explizite Deklarationen von Variablen erforderlich sind.  Standardmäßig ist **Option Explicit** auf **On** festgelegt.  Weitere Informationen finden Sie unter [\/optionexplicit](/dotnet/visual-basic/reference/command-line-compiler/optionexplicit).  
  
 **"Option Strict"**  
 Legt den Compilerstandard so fest, dass explizite Eingrenzungskonvertierungen erforderlich sind und späte Bindung nicht zulässig ist.  Standardmäßig ist **Option Strict** auf **Off** festgelegt.  Weitere Informationen finden Sie unter [\/optionstrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict).  
  
 **Option Compare**  
 Legt den Compilerstandard für Zeichenfolgenvergleiche fest: binär \(Berücksichtigung von Groß\- und Kleinschreibung\) oder Text \(ohne Berücksichtigung von Groß\- und Kleinschreibung\). Standardmäßig ist **Option Compare** auf **Binary** festgelegt.  Weitere Informationen finden Sie unter [\/optioncompare](/dotnet/visual-basic/reference/command-line-compiler/optioncompare).  
  
 **Option Infer**  
 Legt den Compilerstandard für lokalen Typrückschluss fest.  Standardmäßig ist **Option Infer** für neu erstellte Projekte auf **On** und für migrierte, in früheren Versionen von Visual Basic erstellte Projekte auf **Off** eingestellt.  Weitere Informationen finden Sie unter [\/optioninfer](/dotnet/visual-basic/reference/command-line-compiler/optioninfer).  
  
## Siehe auch  
 [Projektmappen und Projekte](../../ide/solutions-and-projects-in-visual-studio.md)
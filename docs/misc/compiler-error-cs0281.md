---
title: "Compilerfehler CS0281 | Microsoft Docs"
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
  - "CS0281"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0281"
ms.assetid: 3b886510-6e4d-45bc-b885-3ab7f6b6b2c6
caps.latest.revision: 18
caps.handback.revision: 18
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0281
"AssemblyName1" wurde Friend\-Zugriff gewährt, die Ausgabeassembly hat aber den Namen "AssemblyName2". Fügen Sie einen Verweis auf "AssemblyName1" hinzu, oder ändern Sie den Namen der Ausgabeassembly entsprechend.  
  
 Friend\-Zugriff ist eine neue CLR\-Funktion \(Common Language Runtime\), die es einer Assembly ermöglicht, die nicht öffentlichen Typen einer anderen Assembly anzuzeigen. Dieser Fehler tritt auf, wenn die Assembly, die Friend\-Zugriff gewährt, den falschen Namen für die Empfängerassembly angibt. Weitere Informationen finden Sie unter [Friend\-Assemblys](../Topic/Friend%20Assemblies%20\(C%23%20and%20Visual%20Basic\).md).  
  
## Beispiel  
 In den folgenden Codebeispielen wird CS0281 generiert.  
  
 Die Dateien zum Erstellen der Assemblys mit starkem Namen werden wie folgt generiert:  
  
-   sn \-d CS0281.snk  
  
-   sn \-k CS0281.snk  
  
-   sn \-i CS0281.snk CS0281.snk  
  
-   sn \-pc CS0281.snk key.publickey  
  
-   sn \-tp key.publickey  
  
```  
// CS0281.cs // compile with: /target:library /keyfile:CS0281.snk public class A {}  
```  
  
## Beispiel  
  
```  
// CS0281_b.cs // compile with: /target:library /keyfile:CS0281.snk /reference:CS0281.dll [assembly:System.Runtime.CompilerServices.InternalsVisibleTo("CS0281 , PublicKey=00240000048000009400000006020000002400005253413100040000010001004b2d4d56af7c50be2fcbbf97cb880b9e73ad84467a587191fef63aadc118a96cecf9d508cd679c907b6e20f71684300bdc2c0a851019af0c96b29bf8f1339753276041aefd67db46139e6348b3a12f29537b4dc6c2c19829df2c9ed6803f3c63c3b84cfa2728849386aea575c543a5f70fa85793d2946f15f7fe1ccb0c5e8fe0")] class B : A {}  
```  
  
## Beispiel  
 Im folgenden Beispiel wird CS0281 generiert.  
  
 In diesem Beispiel wird eine Ausgabedatei erstellt, die den gleichen Namen wie die Ausgabedatei im ersten Beispiel aufweist. Um das Problem zu beheben, ändern Sie nicht die Assemblyattribute der Komponente, und fügen Sie Klasse C hinzu.  
  
```  
// CS0281_c.cs // compile with: /target:library /out:CS0281.dll /keyfile:CS0281.snk /reference:CS0281_b.dll // CS0281 expected [assembly:System.Reflection.AssemblyVersion("3")] [assembly:System.Reflection.AssemblyCulture("en-us")] class C : B {} public class A {}  
```
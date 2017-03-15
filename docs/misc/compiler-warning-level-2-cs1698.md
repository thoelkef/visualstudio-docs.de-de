---
title: "Compilerwarnung (Stufe 2) CS1698 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1698"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1698"
ms.assetid: 65cac5d0-e045-40f9-911c-1bf50e710b18
caps.latest.revision: 20
caps.handback.revision: 20
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerwarnung (Stufe 2) CS1698
Der Assemblyzirkelverweis "AssemblyName1" stimmt nicht mit dem Ausgabeassemblynamen "AssemblyName2" überein. Fügen Sie einen Verweis auf "AssemblyName1" hinzu, oder ändern Sie den Namen der Ausgabeassembly entsprechend.  
  
 CS1698 tritt bei einem falschen Assemblyverweis auf. Dies kann beim erneuten Kompilieren einer Assembly geschehen, auf die verwiesen wird. Um den Fehler zu beheben, sollten Sie eine Assembly, die selbst eine Abhängigkeit einer Assembly darstellt, auf die Sie verweisen, nicht ersetzen.  
  
## Beispiel  
  
```  
// CS1698_a.cs // compile with: /target:library /keyfile:mykey.snk [assembly:System.Reflection.AssemblyVersion("2")] public class CS1698_a {}  
```  
  
## Beispiel  
  
```  
// CS1698_b.cs // compile with: /target:library /reference:CS1698_a.dll /keyfile:mykey.snk public class CS1698_b : CS1698_a {}  
```  
  
## Beispiel  
 Im folgenden Beispiel wird CS1698 generiert.  
  
```  
// CS1698_c.cs // compile with: /target:library /out:cs1698_a.dll /reference:cs1698_b.dll /keyfile:mykey.snk // CS1698 expected [assembly:System.Reflection.AssemblyVersion("3")] public class CS1698_c : CS1698_b {} public class CS1698_a {}  
  
```
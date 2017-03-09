---
title: "Compilerwarnung (Stufe 1) CS1687 | Microsoft Docs"
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
  - "CS1687"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1687"
ms.assetid: f65d184f-fa1d-45d7-be7d-f439f67bace4
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerwarnung (Stufe 1) CS1687
Die Quelldatei hat das Limit von 16.707.565 Zeilen überschritten, die in der PDB dargestellt werden können. Die Debuginformationen sind falsch.  
  
 Die PDB und der Debugger weisen einige Einschränkungen hinsichtlich der Größe einer Datei auf. Wenn die Quelldatei zu groß ist, verhält sich der Debugger über diesen Grenzwert hinaus nicht ordnungsgemäß. Der Benutzer sollte entweder keine Debuginformationen zu dieser Datei ausgeben, indem z. B. `#line hidden` verwendet wird, oder der Benutzer muss eine Möglichkeit finden, um die Datei zu verkleinern, indem die Datei z. B. in mehrere Dateien aufgeteilt wird. Sie können das `partial`\-Schlüsselwort verwenden, um eine große Klasse aufzuteilen.
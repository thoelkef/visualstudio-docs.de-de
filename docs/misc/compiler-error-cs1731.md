---
title: "Compilerfehler CS1731 | Microsoft Docs"
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
  - "CS1731"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1731"
ms.assetid: 267b32aa-a692-4a54-8654-0540ee36c0a0
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1731
'Ausdruck' kann nicht in einen Delegaten konvertiert werden, da einige der Rückgabetypen im Block nicht implizit in den Rückgabetyp des Delegaten konvertiert werden können.  
  
 Dieser Fehler wird generiert, wenn ein Lambdaausdruck oder eine anonyme Methode einen Rückgabetyp aufweist, der nicht mit dem Rückgabetyp des Delegaten kompatibel ist.  
  
### So beheben Sie diesen Fehler  
  
1.  Ändern Sie den Rückgabetyp des Delegaten oder des Ausdrucks.  
  
## Beispiel  
 Der folgende Code generiert CS1731.  
  
```  
class CS1731 { delegate double D(); D d = () => { return "Who knows the real sword of Gryffindor?"; }; }  
```
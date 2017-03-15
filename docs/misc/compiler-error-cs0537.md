---
title: "Compilerfehler CS0537 | Microsoft Docs"
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
  - "CS0537"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0537"
ms.assetid: 6c832a5f-47dc-4f60-aed8-69ac328af44b
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0537
Die System.Object\-Klasse kann keine Basisklasse haben oder eine Schnittstelle implementieren.  
  
 CS0537 tritt auf, wenn die <xref:System>\-Klassenbibliotheken neu erstellt werden und wo <xref:System.Object> von einer anderen Klasse abgeleitet wird. Das Auftreten dieses Fehlers ist sehr unwahrscheinlich. Wenn er dennoch auftritt, leiten Sie <xref:System.Object> nicht von einer Klasse oder Schnittstelle ab. Es handelt sich um den Stamm der gesamten .NET Framework\-Klassenhierarchie, und sie wird als solche nicht von anderen Elementen abgeleitet.
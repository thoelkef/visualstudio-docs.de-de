---
title: "Bearbeiten und Fortfahren wird f&#252;r F# nicht unterst&#252;tzt | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Debuggen [F#], Bearbeiten und Fortfahren"
  - "Bearbeiten und Fortfahren [F#]"
ms.assetid: 40ec77bb-07e3-4b58-9254-ae015009441c
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Bearbeiten und Fortfahren wird f&#252;r F# nicht unterst&#252;tzt
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Beim Debuggen von F\#\-Code wird Bearbeiten und Fortfahren nicht unterstützt.  Das Bearbeiten von F\#\-Code während einer Debugsitzung ist möglich, sollte aber vermieden werden.  Codeänderungen werden während der Debugsitzung nicht übernommen.  Daher führen alle während des Debuggens an F\#\-Code vorgenommenen Bearbeitungen dazu, dass der Quellcode nicht mit dem gerade gedebuggten Code übereinstimmt.
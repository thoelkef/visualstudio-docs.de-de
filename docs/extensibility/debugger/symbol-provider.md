---
title: "Symbol-Anbieter | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Symbol-handler"
  - "Debuggen [Debugging-SDK] Handler symbol"
ms.assetid: 5fce651b-fead-4418-81b0-a011df7644ab
caps.latest.revision: 17
caps.handback.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
---
# Symbol-Anbieter
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Eine Ausdrucksauswertung Implementierung muss die symbolischen Debuginformationen zugreifen, die durch Sprachcompiler generiert werden, um Variablen und Ausdrücke auswerten.  Sie wird mithilfe der Schnittstellen Symbol eines Anbieters \(SP\) nutzen, auch als einen Klassenhandler Symbol.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Zubehör SP für verwalteten Code als auch systemeigener Code mit dem Symbol dateiformats der Programmdatenbank \(PDB\).  Sofern es eine starke Anforderung vorhanden sind, damit das Programm die Symbole verwendet, die in einem benutzerdefinierten Format gespeichert werden, wird empfohlen, das mit dem von SP [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]angegeben wird.  
  
## Implementierungs\-Hinweise  
 Die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Debugmodule zu erwarten, mit dem SP mithilfe der Schnittstellen der Common Language Runtime \(CLR\) zu verweisen.  Daher muss ein SP, das den Modulen Debuggen von Visual Studio arbeiten, wird der CLR unterstützen.  Eine vollständige Liste aller CLR\-Debugschnittstellen kann in debugref.doc gefunden werden, das Teil [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)]ist.  
  
 Wenn die SP nur mit dem benutzerdefinierten Funktion Modul Debuggen wird, können Sie das SP je nach Bedarf Implementierung erfordern vom Modul Debuggen.  
  
## Siehe auch  
 [Debuggerkomponenten](../../extensibility/debugger/debugger-components.md)
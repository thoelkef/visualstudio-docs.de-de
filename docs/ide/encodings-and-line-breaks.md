---
title: "Codierungen und Zeilenumbr&#252;che | Microsoft Docs"
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
  - "vs.Encoding"
helpviewer_keywords: 
  - "Editoren, Zeilenumbrüche"
  - "Codierung"
  - "Zeilenumbruchzeichen"
  - "Zeilenumbrüche"
  - "Visual Studio, Codierung"
  - "Visual Studio, Zeilenumbruchzeichen"
ms.assetid: 8f9b3ffc-7b8d-44f4-87cb-dc29105be12d
caps.latest.revision: 8
caps.handback.revision: 8
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Codierungen und Zeilenumbr&#252;che
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In Visual Studio können Sie unter **Datei\/Erweiterte Speicheroptionen** den Typ der gewünschten Zeilenumbruchzeichen bestimmen.  Sie können auch die Codierung einer Datei mit denselben Einstellungen ändern.  
  
> [!NOTE]
>  Bei bestimmten Entwicklungseinstellungen \(Visual Basic, F\# Web Development\) wird im Menü möglicherweise nicht die Option **Erweiterte Speicheroptionen** angezeigt.  Wenn Sie die Einstellungen ändern möchten \(beispielsweise in "Allgemein"\), öffnen Sie **Tools\/Einstellungen importieren und exportieren**.  Weitere Informationen finden Sie unter [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/de-de/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 In Visual Studio werden die folgenden Zeichen als Zeilenumbrüche interpretiert:  
  
-   CRLF: Wagenrücklauf und Zeilenvorschub, Unicode\-Zeichen 000D und 000A  
  
-   LF: Zeilenvorschub, Unicode\-Zeichen 000A  
  
-   NEL: Nächste Zeile, Unicode\-Zeichen 0085  
  
-   LS: Zeilentrennzeichen, Unicode\-Zeichen 2028  
  
-   PS: Absatztrennzeichen, Unicode\-Zeichen 2029  
  
 In Text, der aus anderen Anwendungen kopiert wurde, bleiben die Codierungen und Zeilenumbruchzeichen unverändert.  Wenn Sie beispielsweise Text aus Windows\-Editor kopieren und in eine Textdatei in Visual Studio einfügen, weist der Text dieselben Einstellungen auf wie in Windows\-Editor.  
  
 Wenn Sie eine Datei öffnen, die andere Zeilenumbruchzeichen aufweist, wird evtl. ein Dialogfeld angezeigt, in dem Sie gefragt werden, ob die inkonsistenten Zeilenumbruchzeichen normalisiert werden sollen und welche Art von Zeilenumbrüchen verwendet werden soll.
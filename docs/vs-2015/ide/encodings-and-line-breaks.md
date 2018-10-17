---
title: Codierungen und Zeilenumbrüche | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.Encoding
helpviewer_keywords:
- line breaks
- encoding
- Visual Studio, encoding
- editors, line breaks
- line break characters
- Visual Studio, line break characters
ms.assetid: 8f9b3ffc-7b8d-44f4-87cb-dc29105be12d
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d11bc0743faa9e512fcd144bfef09a84a316531d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49284985"
---
# <a name="encodings-and-line-breaks"></a>Codierungen und Zeilenumbrüche
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In Visual Studio können Sie unter **Datei/Erweiterte Speicheroptionen** den Typ der gewünschten Zeilenumbruchzeichen bestimmen. Sie können auch die Codierung einer Datei mit denselben Einstellungen ändern.  
  
> [!NOTE]
>  Bei bestimmten Entwicklungseinstellungen (Visual Basic, F# Web Development) wird im Menü möglicherweise nicht die Option **Erweiterte Speicheroptionen** angezeigt. Wenn Sie die Einstellungen ändern möchten (beispielsweise in "Allgemein"), öffnen Sie **Tools/Einstellungen importieren und exportieren**. Weitere Informationen finden Sie unter [Anpassen der Entwicklungseinstellungen in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 In Visual Studio werden die folgenden Zeichen als Zeilenumbrüche interpretiert:  
  
-   CRLF: Wagenrücklauf und Zeilenvorschub, Unicode-Zeichen 000D und 000A  
  
-   LF: Zeilenvorschub, Unicode-Zeichen 000A  
  
-   NEL: Nächste Zeile, Unicode-Zeichen 0085  
  
-   LS: Zeilentrennzeichen, Unicode-Zeichen 2028  
  
-   PS: Absatztrennzeichen, Unicode-Zeichen 2029  
  
 In Text, der aus anderen Anwendungen kopiert wurde, bleiben die Codierungen und Zeilenumbruchzeichen unverändert. Wenn Sie beispielsweise Text aus Windows-Editor kopieren und in eine Textdatei in Visual Studio einfügen, weist der Text dieselben Einstellungen auf wie in Windows-Editor.  
  
 Wenn Sie eine Datei öffnen, die andere Zeilenumbruchzeichen aufweist, wird evtl. ein Dialogfeld angezeigt, in dem Sie gefragt werden, ob die inkonsistenten Zeilenumbruchzeichen normalisiert werden sollen und welche Art von Zeilenumbrüchen verwendet werden soll.




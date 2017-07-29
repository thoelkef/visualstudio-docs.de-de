---
title: "Codierungen und Zeilenumbrüche | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
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
caps.latest.revision: 8
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 5ea9179ad37514ffad4876177b05150eecc22def
ms.openlocfilehash: 34c400c280096acb7e0ce272fa717cbc2f8f0d8a
ms.contentlocale: de-de
ms.lasthandoff: 05/24/2017

---
# <a name="encodings-and-line-breaks"></a>Codierungen und Zeilenumbrüche
In Visual Studio können Sie unter **Datei/Erweiterte Speicheroptionen** den Typ der gewünschten Zeilenumbruchzeichen bestimmen. Sie können auch die Codierung einer Datei mit denselben Einstellungen ändern.  
  
> [!NOTE]
>  Bei bestimmten Entwicklungseinstellungen (Visual Basic, F# Web Development) wird im Menü möglicherweise nicht die Option **Erweiterte Speicheroptionen** angezeigt. Wenn Sie die Einstellungen ändern möchten (beispielsweise in "Allgemein"), öffnen Sie **Tools/Einstellungen importieren und exportieren**. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md).  
  
 In Visual Studio werden die folgenden Zeichen als Zeilenumbrüche interpretiert:  
  
-   CRLF: Wagenrücklauf und Zeilenvorschub, Unicode-Zeichen 000D und 000A  
  
-   LF: Zeilenvorschub, Unicode-Zeichen 000A  
  
-   NEL: Nächste Zeile, Unicode-Zeichen 0085  
  
-   LS: Zeilentrennzeichen, Unicode-Zeichen 2028  
  
-   PS: Absatztrennzeichen, Unicode-Zeichen 2029  
  
 In Text, der aus anderen Anwendungen kopiert wurde, bleiben die Codierungen und Zeilenumbruchzeichen unverändert. Wenn Sie beispielsweise Text aus Windows-Editor kopieren und in eine Textdatei in Visual Studio einfügen, weist der Text dieselben Einstellungen auf wie in Windows-Editor.  
  
 Wenn Sie eine Datei öffnen, die andere Zeilenumbruchzeichen aufweist, wird evtl. ein Dialogfeld angezeigt, in dem Sie gefragt werden, ob die inkonsistenten Zeilenumbruchzeichen normalisiert werden sollen und welche Art von Zeilenumbrüchen verwendet werden soll.

---
title: Codierungen und Zeilenumbrüche | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: 6ceec5e44ade219f069e72f712129a137d70875f
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63437523"
---
# <a name="encodings-and-line-breaks"></a>Codierungen und Zeilenumbrüche
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In Visual Studio können Sie unter **Datei/Erweiterte Speicheroptionen** den Typ der gewünschten Zeilenumbruchzeichen bestimmen. Sie können auch die Codierung einer Datei mit denselben Einstellungen ändern.  
  
> [!NOTE]
> Bei bestimmten Entwicklungseinstellungen (Visual Basic, F# Web Development) wird im Menü möglicherweise nicht die Option **Erweiterte Speicheroptionen** angezeigt. Wenn Sie die Einstellungen ändern möchten (beispielsweise in "Allgemein"), öffnen Sie **Tools/Einstellungen importieren und exportieren**. Weitere Informationen finden Sie unter [Anpassen der Entwicklungseinstellungen in Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 In Visual Studio werden die folgenden Zeichen als Zeilenumbrüche interpretiert:  
  
- CRLF: Wagenrücklauf und Zeilenvorschub, Unicode-Zeichen 000D und 000A  
  
- LF: Zeilenvorschub, Unicode-Zeichen 000A  
  
- NEL: Nächste Zeile, Unicode-Zeichen 0085  
  
- LS: Zeilentrennzeichen, Unicode-Zeichen 2028  
  
- PS: Absatztrennzeichen, Unicode-Zeichen 2029  
  
  In Text, der aus anderen Anwendungen kopiert wurde, bleiben die Codierungen und Zeilenumbruchzeichen unverändert. Wenn Sie beispielsweise Text aus Windows-Editor kopieren und in eine Textdatei in Visual Studio einfügen, weist der Text dieselben Einstellungen auf wie in Windows-Editor.  
  
  Wenn Sie eine Datei öffnen, die andere Zeilenumbruchzeichen aufweist, wird evtl. ein Dialogfeld angezeigt, in dem Sie gefragt werden, ob die inkonsistenten Zeilenumbruchzeichen normalisiert werden sollen und welche Art von Zeilenumbrüchen verwendet werden soll.

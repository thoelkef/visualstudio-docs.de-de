---
title: Problembehandlung für Codemetrikfehler | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2fdb995-4888-4246-85dc-7bacadd45968
caps.latest.revision: 6
author: erickson-doug
ms.author: gewarren
manager: douge
ms.openlocfilehash: 2cadd72f23fee6b89804fdbe61b105ff36b89caf
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47522324"
---
# <a name="troubleshooting-code-metrics-issues"></a>Problembehandlung für Codemetrikfehler
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Problembehandlung für Codemetrikfehler](https://docs.microsoft.com/visualstudio/code-quality/troubleshooting-code-metrics-issues).  
  
Beim Sammeln von Codemetriken stoßen Sie möglicherweise auf folgende Probleme:  
  
-   [Änderung in der Berechnung von Codekomplexität in Visual Studio 2010](#Changes_in_Visual_Studio_2010_code_complexity_calculations)  
  
##  <a name="Changes_in_Visual_Studio_2010_code_complexity_calculations"></a> Änderung in der Berechnung von Codekomplexität in Visual Studio 2010  
 Die Codekomplexitätsmetrik, die in [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] berechnet wurde, kann sich in folgenden Szenarios für die gleiche Funktion von der Metrik unterscheiden, die von früheren Versionen von [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] berechnet wurde:  
  
-   Die Funktion enthält mindestens einen Catch-Block. In früheren Versionen von [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] waren Catch-Blöcke nicht in der Berechnung enthalten. Bei [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] wird die Komplexität jedes einzelnen Catch-Blocks zu der Komplexität der Funktion hinzugefügt.  
  
-   Die Funktion enthält eine switch-Anweisung (Select Case in Visual Basic). Unterschiede der Compiler zwischen [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] und früheren Versionen können bei manchen switch-Anweisungen, die Fall-Through-Fälle beinhalten, unterschiedlichen MSIL-Code generieren.  
  
## <a name="see-also"></a>Siehe auch  
 [Messen von Komplexität und Verwaltbarkeit verwalteten Codes](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)




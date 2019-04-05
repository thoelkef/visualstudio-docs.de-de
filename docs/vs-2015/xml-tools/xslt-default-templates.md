---
title: XSLT-Standardvorlagen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 773dd34e-67d3-4997-8df9-b71e7f880d88
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 10937ed9c3ade13bf553ba4d3a2a9c551597949e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58961123"
---
# <a name="xslt-default-templates"></a>XSLT-Standardvorlagen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Eine Standardvorlage wird bei der XSLT-Verarbeitung verwendet, wenn im Stylesheet keine passende explizite Vorlagenregel vorhanden ist. Die Standardvorlage (oder integrierte Vorlagenregel) wird in Abschnitt 5.8 der W3C XSLT 1.0 Recommendation definiert. Mithilfe der Standardvorlage kann der XSLT-Prozessor einen Knoten verarbeiten, auch wenn keine passende Vorlagenregel explizit angegeben wurde. Da die integrierte Vorlagenregel nicht explizit im Stylesheet definiert ist, kann dies jedoch zu unerwarteten oder widersprüchlichen Ergebnissen bei der XSL-Transformation führen.  
  
 Der XSLT-Debugger zeigt jetzt den Code von XSLT-Standardvorlagen an. Bei den einzelnen Schritten einer XSL-Transformation zeigt der Debugger, sofern eine Standardvorlage verwendet wird, diese in einem Fenster an. Dadurch können der Code der Standardvorlage schrittweise ausgeführt werden und Haltepunkte für dessen Anweisungen festgelegt werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von XSLT](../xml-tools/debugging-xslt.md)

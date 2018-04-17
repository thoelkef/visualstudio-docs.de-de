---
title: XSLT-Standardvorlagen | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
ms.assetid: 773dd34e-67d3-4997-8df9-b71e7f880d88
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5b1d2f0a7102821041bf76f1e8dcd73ff01baacc
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="xslt-default-templates"></a>XSLT-Standardvorlagen
Eine Standardvorlage wird bei der XSLT-Verarbeitung verwendet, wenn im Stylesheet keine passende explizite Vorlagenregel vorhanden ist. Die Standardvorlage (oder integrierte Vorlagenregel) wird in Abschnitt 5.8 der W3C XSLT 1.0 Recommendation definiert. Mithilfe der Standardvorlage kann der XSLT-Prozessor einen Knoten verarbeiten, auch wenn keine passende Vorlagenregel explizit angegeben wurde. Da die integrierte Vorlagenregel nicht explizit im Stylesheet definiert ist, kann dies jedoch zu unerwarteten oder widersprüchlichen Ergebnissen bei der XSL-Transformation führen.  
  
 Der XSLT-Debugger zeigt jetzt den Code von XSLT-Standardvorlagen an. Bei den einzelnen Schritten einer XSL-Transformation zeigt der Debugger, sofern eine Standardvorlage verwendet wird, diese in einem Fenster an. Dadurch können der Code der Standardvorlage schrittweise ausgeführt werden und Haltepunkte für dessen Anweisungen festgelegt werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von XSLT](../xml-tools/debugging-xslt.md)
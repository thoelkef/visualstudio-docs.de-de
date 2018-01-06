---
title: XSLT-Standardvorlagen | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 773dd34e-67d3-4997-8df9-b71e7f880d88
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 4fe1bf4dda6bed505f0892a18825e93f66e13e16
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="xslt-default-templates"></a>XSLT-Standardvorlagen
Eine Standardvorlage wird bei der XSLT-Verarbeitung verwendet, wenn im Stylesheet keine passende explizite Vorlagenregel vorhanden ist. Die Standardvorlage (oder integrierte Vorlagenregel) wird in Abschnitt 5.8 der W3C XSLT 1.0 Recommendation definiert. Mithilfe der Standardvorlage kann der XSLT-Prozessor einen Knoten verarbeiten, auch wenn keine passende Vorlagenregel explizit angegeben wurde. Da die integrierte Vorlagenregel nicht explizit im Stylesheet definiert ist, kann dies jedoch zu unerwarteten oder widersprüchlichen Ergebnissen bei der XSL-Transformation führen.  
  
 Der XSLT-Debugger zeigt jetzt den Code von XSLT-Standardvorlagen an. Bei den einzelnen Schritten einer XSL-Transformation zeigt der Debugger, sofern eine Standardvorlage verwendet wird, diese in einem Fenster an. Dadurch können der Code der Standardvorlage schrittweise ausgeführt werden und Haltepunkte für dessen Anweisungen festgelegt werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von XSLT](../xml-tools/debugging-xslt.md)
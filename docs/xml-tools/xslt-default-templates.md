---
title: XSLT-Standardvorlagen
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 773dd34e-67d3-4997-8df9-b71e7f880d88
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2b50a7457ddbae24f2a00e4c631371cb2aeb1169
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34693954"
---
# <a name="xslt-default-templates"></a>XSLT-Standardvorlagen

Eine Standardvorlage wird bei der XSLT-Verarbeitung verwendet, wenn im Stylesheet keine passende explizite Vorlagenregel vorhanden ist. Die Standardvorlage (oder integrierte Vorlagenregel) wird in Abschnitt 5.8 der W3C XSLT 1.0 Recommendation definiert. Mithilfe der Standardvorlage kann der XSLT-Prozessor einen Knoten verarbeiten, auch wenn keine passende Vorlagenregel explizit angegeben wurde. Da die integrierte Vorlagenregel nicht explizit im Stylesheet definiert ist, kann dies jedoch zu unerwarteten oder widersprüchlichen Ergebnissen bei der XSL-Transformation führen.

Der XSLT-Debugger zeigt jetzt den Code von XSLT-Standardvorlagen an. Bei den einzelnen Schritten einer XSL-Transformation zeigt der Debugger, sofern eine Standardvorlage verwendet wird, diese in einem Fenster an. Dadurch können der Code der Standardvorlage schrittweise ausgeführt werden und Haltepunkte für dessen Anweisungen festgelegt werden.

## <a name="see-also"></a>Siehe auch

- [Debuggen von XSLT](../xml-tools/debugging-xslt.md)
---
title: 'Gewusst wie: Verwenden von Haltepunkten bei XSLT'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 430b7f14f35506b45fe73be47d056cdd7b6a9c95
ms.sourcegitcommit: 697162f54d3c4e30df702fd0289e447e211e3a85
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/25/2018
---
# <a name="how-to-use-breakpoints-with-xslt"></a>Vorgehensweise: Verwenden von Haltepunkten bei XSLT

Sie können Haltepunkte in einem XSLT-Stylesheet oder im XML-Quelldokument festlegen. Wenn Sie einen Haltepunkt für ein Tag festlegen, wird der Haltepunkt beim Starten der Ausführung zur nächsten Anweisung verschoben, die über Quellzeileninformationen verfügt.

Weitere Informationen finden Sie unter [Grundlagen des Debuggens: Haltepunkte](../debugger/using-breakpoints.md).

## <a name="set-a-breakpoint-in-a-style-sheet"></a>Festlegen eines Haltepunkts in einem Stylesheet

Haltepunkte können für Starttags, Endtags und Textknoten eines XSLT-Stylesheets festgelegt werden. Haltepunkte können auch für Code in einem Skriptblock festgelegt werden.

### <a name="to-set-a-breakpoint-in-a-style-sheet"></a>So legen Sie einen Haltepunkt in einem Stylesheet fest

1.  Öffnen Sie ein Stylesheet im XML-Editor.

2.  Positionieren Sie den Cursor auf die Position des Haltepunkts, mit der rechten Maustaste, zeigen Sie auf **Haltepunkt**, und klicken Sie auf **Haltepunkt einfügen**.

3.  Klicken Sie auf die Schaltfläche zum Durchsuchen (**...** ) auf die **Eingabe** Feld Eigenschaftenfenster des Dokuments.

4.  Suchen Sie das XML-Quelldokument, und klicken Sie auf **öffnen**.

     Damit legen Sie die Quelldokumentdatei fest, die für die XSLT-Transformation verwendet wird.

5.  Klicken Sie auf die **XSLT Debuggen** Schaltfläche auf der Symbolleiste des XML-Editors.

## <a name="set-a-breakpoint-in-an-xml-source-document"></a>Festlegen eines Haltepunkts in einem XML-Quelldokument

Haltepunkte können für Elemente, Attribute, Namespaceknoten, Kommentare, Verarbeitungsanweisungen und Textknoten eines XML-Quelldokuments festgelegt werden. Für den Dokumentknoten oder einen Namespaceknoten, der vom übergeordneten Element erbt, kann kein Haltepunkt festgelegt werden.

### <a name="to-set-a-breakpoint-in-an-xml-source-document"></a>So legen Sie einen Haltepunkt in einem XML-Quelldokument fest

1.  Öffnen Sie das XML-Dokument im XML-Editor.

2.  Positionieren Sie den Cursor auf die Position des Haltepunkts, mit der rechten Maustaste, zeigen Sie auf **Haltepunkt**, und klicken Sie auf **Haltepunkt einfügen**.

3.  Klicken Sie auf die Schaltfläche zum Durchsuchen (**...** ) auf die **Stylesheet** Feld Eigenschaftenfenster des Dokuments.

4.  Suchen Sie das XML-Quelldokument, und klicken Sie auf **öffnen**.

     Damit legen Sie die Quelldokumentdatei fest, die für die XSLT-Transformation verwendet wird.

5.  Klicken Sie auf die **XSLT Debuggen** Schaltfläche auf der Symbolleiste des XML-Editors.

## <a name="see-also"></a>Siehe auch

- [Exemplarische Vorgehensweise: Debuggen von XSLT-Stylesheets](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md)
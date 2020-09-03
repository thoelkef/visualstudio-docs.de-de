---
title: 'Gewusst wie: Verwenden von Breakpoints mit XSLT | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: bf7bbc2c-71dc-4cac-a6fc-add6b27d92ed
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0519c3ab19e7d36aa26ea2f462c8a4571b9f8b32
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656306"
---
# <a name="how-to-use-breakpoints-with-xslt"></a>Gewusst wie: Verwenden von Haltepunkten bei XSLT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können Haltepunkte in einem XSLT-Stylesheet oder im XML-Quelldokument festlegen. Wenn Sie einen Haltepunkt für ein Tag festlegen, wird der Haltepunkt beim Starten der Ausführung zur nächsten Anweisung verschoben, die über Quellzeileninformationen verfügt.

 Weitere Informationen finden Sie unter [Grundlagen des Debuggens: Breakpoints](https://msdn.microsoft.com/752a02c2-0ac7-4c8b-aa1b-4b2b3b21152e).

## <a name="set-a-breakpoint-in-a-style-sheet"></a>Festlegen eines Haltepunkts in einem Stylesheet
 Haltepunkte können für Starttags, Endtags und Textknoten eines XSLT-Stylesheets festgelegt werden. Haltepunkte können auch für Code in einem Skriptblock festgelegt werden.

#### <a name="to-set-a-breakpoint-in-a-style-sheet"></a>So legen Sie einen Haltepunkt in einem Stylesheet fest

1. Öffnen Sie ein Stylesheet im XML-Editor.

2. Positionieren Sie den Cursor an der Haltepunkt Position, klicken Sie mit der rechten Maustaste auf, zeigen Sie auf **Breakpoint**, und klicken Sie dann auf halte **Punkt einfügen**.

3. Klicken Sie auf die Schaltfläche zum Durchsuchen (**...**) im **Eingabe** Feld des Dokumenteigenschaften Fensters.

4. Suchen Sie das XML-Quelldokument, und klicken Sie auf **Öffnen**.

     Damit legen Sie die Quelldokumentdatei fest, die für die XSLT-Transformation verwendet wird.

5. Klicken Sie im XML-Editor auf die Schaltfläche **XSL debuggen** .

## <a name="set-a-breakpoint-in-an-xml-source-document"></a>Festlegen eines Haltepunkts in einem XML-Quelldokument
 Haltepunkte können für Elemente, Attribute, Namespaceknoten, Kommentare, Verarbeitungsanweisungen und Textknoten eines XML-Quelldokuments festgelegt werden. Für den Dokumentknoten oder einen Namespaceknoten, der vom übergeordneten Element erbt, kann kein Haltepunkt festgelegt werden.

#### <a name="to-set-a-breakpoint-in-an-xml-source-document"></a>So legen Sie einen Haltepunkt in einem XML-Quelldokument fest

1. Öffnen Sie das XML-Dokument im XML-Editor.

2. Positionieren Sie den Cursor an der Haltepunkt Position, klicken Sie mit der rechten Maustaste auf, zeigen Sie auf **Breakpoint**, und klicken Sie dann auf halte **Punkt einfügen**.

3. Klicken Sie im Feld **Stylesheet** des Fensters Dokumenteigenschaften auf die Schaltfläche zum Durchsuchen (**...**).

4. Suchen Sie das XML-Quelldokument, und klicken Sie auf **Öffnen**.

     Damit legen Sie die Quelldokumentdatei fest, die für die XSLT-Transformation verwendet wird.

5. Klicken Sie im XML-Editor auf die Schaltfläche **XSL debuggen** .

## <a name="see-also"></a>Weitere Informationen
 [Exemplarische Vorgehensweise: Debuggen eines XSLT-Stylesheets](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md)

---
title: Generieren von XML-Dokumentationskommentare - Generierung von Code (Visual Basic) | Microsoft Docs
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d2025bd2-5984-4486-a61c-0a0933a735ea
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1291667c7acb47abe543d275549179abea0c8467
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="generate-xml-documentation-comments-in-visual-basic"></a>Generieren von XML-Dokumentationskommentare in Visual Basic
**Was:** können Sie sofort die Basis generieren XML erforderlich, um das ausgewählte Element zu dokumentieren. 

**Wann:** XML-Dokumentkommentare für die spätere Verarbeitung von einem Dokumentationstool wie Sandburg erstellt werden soll.

**Grund:** Sie manuell den gesamten Kommentarblock auch selbst erstellen, jedoch wird dadurch Zeit sparen und Genauigkeit verbessern, indem Sie die Basisvorlage und zusätzliche Elemente generiert. 

**Vorgehensweise:**

1. Platzieren Sie den Textcursor über dem Element, z. B. eine Methode dokumentiert werden sollen.

   ![Methode zum Dokument](media/doc_highlight.png)

1. Geben Sie als Nächstes **'''** (3 einfachen Anführungszeichen) wird die automatisch die Basisvorlage und alle zusätzlichen Elemente nach Bedarf erstellt.  Z. B. wenn eine Methode zu kommentieren, generiert er die  **\<Zusammenfassung\>**  Tags sowie ein  **\<Param\>**  Tag für jeden Parameter, die an die Methode übergeben und eine  **\<gibt\>**  Tag zu dokumentieren, was die-Methode zurückgibt.

   ![Vorlage](media/doc_preview.png)

1. Schließen Sie die Kommentare, und das fügen Sie eines zusätzlichen Daten, die Sie sich fühlen, erforderlich ist hinzu.

   ![Abgeschlossene Kommentar](media/doc_result.png)

## <a name="see-also"></a>Siehe auch
[Dokumentieren von Code mit XML (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/documenting-your-code-with-xml)  
[Codegenerierung (Visual Basic)](../code-generation-vb.md) 
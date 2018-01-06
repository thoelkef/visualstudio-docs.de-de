---
title: Generieren von XML-Dokumentationskommentare - Generierung von Code (c#) | Microsoft Docs
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d2025bd2-5984-4486-a61c-0a0933a735ea
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: f1c1dfb69c12eb183ecf3435346a543488ebe0e1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="generate-xml-documentation-comments-in-c"></a>Generieren von XML-Dokumentationskommentare in c# #
**Was:** können Sie sofort die Basis generieren XML erforderlich, um das ausgewählte Element zu dokumentieren. 

**Wann:** XML-Dokumentkommentare für die spätere Verarbeitung von einem Dokumentationstool wie Sandburg erstellt werden soll.

**Grund:** Sie manuell den gesamten Kommentarblock auch selbst erstellen, jedoch wird dadurch Zeit sparen und Genauigkeit verbessern, indem Sie die Basisvorlage und zusätzliche Elemente generiert. 

**Vorgehensweise:**

1. Platzieren Sie den Textcursor über dem Element, z. B. eine Methode dokumentiert werden sollen.

   ![Methode zum Dokument](media/doc_highlight.png)

1. Geben Sie als Nächstes  **///**  (3, Schrägstriche) die automatisch die Basisvorlage und alle zusätzlichen Elemente nach Bedarf erstellt werden.  Z. B. wenn eine Methode zu kommentieren, generiert er die  **\<Zusammenfassung\>**  Tags sowie ein  **\<Param\>**  Tag für jeden Parameter, die an die Methode übergeben und eine  **\<gibt\>**  Tag zu dokumentieren, was die-Methode zurückgibt.

   ![Vorlage](media/doc_preview.png)

1. Schließen Sie die Kommentare, und das fügen Sie eines zusätzlichen Daten, die Sie sich fühlen, erforderlich ist hinzu.

   ![Abgeschlossene Kommentar](media/doc_result.png)

## <a name="see-also"></a>Siehe auch
[Codegenerierung (C#)](../code-generation-csharp.md)  
[XML-Dokumentationskommentare (C#-Programmierhandbuch)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)

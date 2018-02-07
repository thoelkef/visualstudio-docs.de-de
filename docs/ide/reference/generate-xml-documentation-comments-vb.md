---
title: "Generieren von XML-Dokumentationskommentaren für Visual Basic | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 2f421553657dfafb265140e44e38a2c7722a7303
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/06/2018
---
# <a name="generate-xml-documentation-comments-in-visual-basic"></a>Generieren von XML-Dokumentationskommentaren für Visual Basic

**Beschreibung**: Hiermit können Sie sofort das XML-Basisdokument generieren, um das ausgewählte Element zu dokumentieren. 

**Hintergrund**: Sie möchten XML-Dokumentkommentare für die spätere Verarbeitung mit einem Dokumentationstool wie Sandcastle erstellen.

**Vorteile**: Sie können den gesamten Kommentarblock auch selbst erstellen, das Generieren der Basisvorlage und zusätzlicher Elemente erspart Ihnen jedoch Zeit und verbessert die Genauigkeit. 

**Vorgehensweise**:

1. Platzieren Sie den Textcursor oberhalb des zu dokumentierenden Elements, z.B. einer Methode.

   ![Zu dokumentierende Methode](media/doc-highlight-vb.png)

1. Geben Sie als Nächstes **'''** (3 einfache Anführungszeichen) ein, die automatisch die Basisvorlage und bei Bedarf alle zusätzlichen Elemente erstellen.  Wenn Sie z.B. eine Methode kommentieren, werden sowohl die **\<summary\>**-Tags als auch ein **\<param\>**-Tag für jeden an die Methode übergebenen Parameter sowie ein **\<returns\>**-Tag generiert, das dokumentiert, was die Methode zurückgibt.

   ![Vorlage](media/doc-preview-vb.png)

1. Vervollständigen Sie die Kommentare, und fügen Sie ggf. erforderliche zusätzliche Informationen hinzu.

   ![Vervollständigter Kommentar](media/doc-result-vb.png)

## <a name="see-also"></a>Siehe auch

[Dokumentieren von Code mit XML (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/documenting-your-code-with-xml)  
[Codegenerierung](../code-generation-in-visual-studio.md)
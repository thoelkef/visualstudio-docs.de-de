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
ms.workload: multiple
ms.openlocfilehash: 2f421553657dfafb265140e44e38a2c7722a7303
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/13/2018
---
# <a name="generate-xml-documentation-comments-in-visual-basic"></a>Generieren von XML-Dokumentationskommentaren für Visual Basic

**Beschreibung**: Hiermit können Sie sofort das XML-Basisdokument generieren, um das ausgewählte Element zu dokumentieren. 

**Hintergrund**: Sie möchten XML-Dokumentkommentare für die spätere Verarbeitung mit einem Dokumentationstool wie Sandcastle erstellen.

**Vorteile**: Sie können den gesamten Kommentarblock auch selbst erstellen, das Generieren der Basisvorlage und zusätzlicher Elemente erspart Ihnen jedoch Zeit und verbessert die Genauigkeit. 

**Vorgehensweise**:

1. Platzieren Sie den Textcursor oberhalb des zu dokumentierenden Elements, z.B. einer Methode.

   ![Zu dokumentierende Methode](media/doc-highlight-vb.png)

1. Geben Sie als Nächstes **'''** (3 einfache Anführungszeichen) ein, die automatisch die Basisvorlage und bei Bedarf alle zusätzlichen Elemente erstellen.  Beispiel: Beim Kommentieren einer Methode werden für jeden Parameter **\<summary\>**-Tags, ein an die Methode übergebenes **\<param\>**-Tag und ein **\<returns\>**-Tag generiert, um die Rückgabe der Methode zu dokumentieren.

   ![Vorlage](media/doc-preview-vb.png)

1. Vervollständigen Sie die Kommentare, und fügen Sie ggf. erforderliche zusätzliche Informationen hinzu.

   ![Vervollständigter Kommentar](media/doc-result-vb.png)

## <a name="see-also"></a>Siehe auch

[Dokumentieren von Code mit XML (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/documenting-your-code-with-xml)  
[Codegenerierung](../code-generation-in-visual-studio.md)
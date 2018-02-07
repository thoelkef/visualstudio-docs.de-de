---
title: "Generieren von XML-Dokumentationskommentaren – Codegenerierung (C#) | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d2025bd2-5984-4486-a61c-0a0933a735ea
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: b0a0ec1db54f57e14ddd412248f7a396336fe009
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/06/2018
---
# <a name="generate-xml-documentation-comments-in-c"></a>Generieren von XML-Dokumentationskommentaren in C# #
**Beschreibung**: Hiermit können Sie sofort das XML-Basisdokument generieren, um das ausgewählte Element zu dokumentieren. 

**Hintergrund**: Sie möchten XML-Dokumentkommentare für die spätere Verarbeitung mit einem Dokumentationstool wie Sandcastle erstellen.

**Vorteile**: Sie können den gesamten Kommentarblock auch selbst erstellen, das Generieren der Basisvorlage und zusätzlicher Elemente erspart Ihnen jedoch Zeit und verbessert die Genauigkeit. 

**Vorgehensweise**:

1. Platzieren Sie den Textcursor oberhalb des zu dokumentierenden Elements, z.B. einer Methode.

   ![Zu dokumentierende Methode](media/doc-highlight-cs.png)

1. Geben Sie als Nächstes **///** (3 Schrägstriche) ein, die automatisch die Basisvorlage und bei Bedarf alle zusätzlichen Elemente erstellen.  Wenn Sie z.B. eine Methode kommentieren, werden sowohl die **\<summary\>**-Tags als auch ein **\<param\>**-Tag für jeden an die Methode übergebenen Parameter sowie ein **\<returns\>**-Tag generiert, das dokumentiert, was die Methode zurückgibt.

   ![Vorlage](media/doc-preview-cs.png)

1. Vervollständigen Sie die Kommentare, und fügen Sie ggf. erforderliche zusätzliche Informationen hinzu.

   ![Vervollständigter Kommentar](media/doc-result-cs.png)

## <a name="see-also"></a>Siehe auch

[Codegenerierung](../code-generation-in-visual-studio.md)  
[XML-Dokumentationskommentare (C#-Programmierhandbuch)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)

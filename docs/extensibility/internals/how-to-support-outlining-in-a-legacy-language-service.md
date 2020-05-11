---
title: 'Gewusst wie: Support-Umriss in einem Legacy-Sprachdienst | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], collapse to definitions command
- language services, supporting Collapse to Definitions command
- hidden text, Collapse to Definitions command
ms.assetid: bb6e74c3-93e4-4ef7-afc7-1c9b342f083b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 28396d513c83ed83e2769e75a6020a98b10251b4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707920"
---
# <a name="how-to-support-outlining-in-a-legacy-language-service"></a>Gewusst wie: Unterstützung von Gliederung in einem älteren Sprachdienst
Die Gliederung wird verwendet, um verschiedene Textbereiche zu erweitern oder zu reduzieren. Die Art und Weise, wie die Gliederung verwendet wird, kann durch verschiedene Sprachen unterschiedlich definiert werden. Weitere Informationen finden Sie unter [Gliedern](../../ide/outlining.md).

 Ältere Sprachdienste werden als Teil eines VSPackage implementiert, aber die neuere Möglichkeit zum Implementieren von Sprachdienstfunktionen besteht darin, MEF-Erweiterungen zu verwenden. Weitere Informationen zur neuen Vorgehensweise zum Implementieren von Gliederung finden Sie unter [Walkthrough: Umreißen](../../extensibility/walkthrough-outlining.md).

> [!NOTE]
> Es wird empfohlen, die neue Editor-API so schnell wie möglich zu verwenden. Dadurch wird die Leistung Ihres Sprachdienstes verbessert und Sie können die neuen Editorfunktionen nutzen.

 Im Folgenden wird veranschaulicht, wie Sie diesen Befehl für Ihren Sprachdienst unterstützen.

## <a name="to-support-outlining"></a>Zur Unterstützung der Gliederung

1. Implementieren <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage> Sie für Ihr Sprachdienstobjekt.

2. Rufen <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> Sie das aktuelle Gliederungssitzungsobjekt auf, um neue Gliederungsbereiche hinzuzufügen.

## <a name="robust-programming"></a>Stabile Programmierung
 Wenn ein Benutzer im **Menü Gliederung** **sausen** <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage.CollapseToDefinitions%2A> auf Definitionen auswählt, ruft die IDE Ihren Sprachdienst auf.

 Wenn diese Methode aufgerufen wird, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> übergibt die IDE einen Zeiger (einen <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession> Zeiger auf einen Textpuffer) und einen (einen Zeiger auf die aktuelle Gliederungssitzung).

 Sie können <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> die Methode für mehrere Gliederungsbereiche aufrufen, indem Sie diese Bereiche im `rgOutlnReg` Parameter angeben. Der `rgOutlnReg` Parameter <xref:Microsoft.VisualStudio.TextManager.Interop.NewOutlineRegion> ist eine Struktur. Mit diesem Prozess können Sie verschiedene Merkmale des ausgeblendeten Bereichs angeben, z. B. ob eine bestimmte Region erweitert oder reduziert wird.

> [!NOTE]
> Achten Sie darauf, neue Zeilenzeichen zu verstecken. Ausgeblendeter Text sollte sich vom Anfang der ersten Zeile bis zum letzten Zeichen der letzten Zeile in einem Abschnitt erstrecken, sodass das letzte Zeilenzeichen sichtbar bleibt.

## <a name="see-also"></a>Weitere Informationen
- [Gewusst wie: Bereitstellen von verdeckter Textunterstützung in einem älteren Sprachdienst](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)
- [Gewusst wie: Erweiterte Umrissunterstützung in einem legacy Sprachdienst bereitstellen](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)

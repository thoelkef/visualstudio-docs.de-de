---
title: Implementieren von Syntaxfarben | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- syntax coloring, implementing
- editors [Visual Studio SDK], colorizing text
- text, colorizing in editors
ms.assetid: 96e762ca-efd0-41e7-8958-fda4897c8c7a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 83ce66dd6a31e3ef852feb91e2ba304e6688a723
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707649"
---
# <a name="implementing-syntax-coloring"></a>Implementieren von Syntaxfarben
Wenn der Sprachdienst Syntaxfarben bereitstellt, konvertiert der Parser eine Textzeile in ein Array von befärbten Elementen und gibt Tokentypen zurück, die diesen farbbaren Elementen entsprechen. Der Parser sollte Tokentypen zurückgeben, die zu einer Liste von befärbbaren Elementen gehören. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]zeigt jedes befärbbare Element im Codefenster entsprechend den Attributen an, die vom Colorizer-Objekt dem entsprechenden Tokentyp zugewiesen wurden.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]gibt keine Parserschnittstelle an, und die Parserimplementierung liegt vollständig bei Ihnen. Im Visual Studio Language Package-Projekt wird jedoch eine Standardparserimplementierung bereitgestellt. Für verwalteten Code bietet das Verwaltete Paketframework (MPF) vollständige Unterstützung für die Farbierung von Text.

 Ältere Sprachdienste werden als Teil eines VSPackage implementiert, aber die neuere Möglichkeit zum Implementieren von Sprachdienstfunktionen besteht darin, MEF-Erweiterungen zu verwenden. Weitere Informationen zur neuen Vorgehensweise zum Implementieren von Syntaxfarben finden Sie unter [Exemplarische Vorgehensweise: Hervorhebung von Text](../../extensibility/walkthrough-highlighting-text.md).

> [!NOTE]
> Es wird empfohlen, die neue Editor-API so schnell wie möglich zu verwenden. Dadurch wird die Leistung Ihres Sprachdienstes verbessert und Sie können die neuen Editorfunktionen nutzen.

## <a name="steps-followed-by-an-editor-to-colorize-text"></a>Schritte Gefolgt von einem Editor zum Kolorieren von Text

1. Der Editor ruft den Colorizer ab, indem er die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> Methode für das <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> Objekt aufruft.

2. Der Editor <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStateMaintenanceFlag%2A> ruft die Methode auf, um zu bestimmen, ob der Colorizer den Status jeder Zeile benötigt, um außerhalb des Colorizers beibehalten zu werden.

3. Wenn der Colorizer erfordert, dass der Status außerhalb <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStartState%2A> des Colorizers beibehalten wird, ruft der Editor die Methode auf, um den Status der ersten Zeile abzubekommen.

4. Für jede Zeile im Puffer ruft <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> der Editor die Methode auf, die die folgenden Schritte ausführt:

    1. Die Textzeile wird an einen Scanner übergeben, um den Text in Token zu konvertieren. Jedes Token gibt den Tokentext und den Tokentyp an.

    2. Der Tokentyp wird in einen Index in eine Liste mit befärbbaren Elementen konvertiert.

    3. Die Tokeninformationen werden verwendet, um ein Array so auszufüllen, dass jedes Element des Arrays einem Zeichen in der Zeile entspricht. Die im Array gespeicherten Werte sind die Indizes in der Liste der befärbbaren Elemente.

    4. Der Status am Ende der Zeile wird für jede Zeile zurückgegeben.

5. Wenn der Colorizer die Aufrechterhaltung des Zustands erfordert, speichert der Editor den Status für diese Zeile zwischen.

6. Der Editor rendert die Textzeile mithilfe <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> der von der Methode zurückgegebenen Informationen. Gehen Sie dazu folgendermaßen vor:

    1. Erhalten Sie für jedes Zeichen in der Zeile den farbbaren Elementindex.

    2. Wenn Sie die standardmäßigen farbbaren Elemente verwenden, greifen Sie auf die Liste der farbbaren Elemente des Editors zu.

    3. Rufen Sie andernfalls die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> Methode des Sprachdienstes auf, um ein befärbbares Element abzurufen.

    4. Verwenden Sie die Informationen im befärbbaren Element, um den Text in die Anzeige zu rendern.

## <a name="managed-package-framework-colorizer"></a>Managed Package Framework Colorizer
 Das Managed Package Framework (MPF) stellt alle Klassen bereit, die zum Implementieren eines Colorizers erforderlich sind. Ihre Sprachdienstklasse sollte die <xref:Microsoft.VisualStudio.Package.LanguageService> Klasse erben und die erforderlichen Methoden implementieren. Sie müssen einen Scanner und einen <xref:Microsoft.VisualStudio.Package.IScanner> Parser bereitstellen, indem Sie <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> die Schnittstelle implementieren, und eine Instanz <xref:Microsoft.VisualStudio.Package.LanguageService> dieser Schnittstelle von der Methode zurückgeben (eine der Methoden, die in der Klasse implementiert werden muss). Weitere Informationen finden Sie unter [Syntax colorizing in a Legacy Language Service](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).

## <a name="see-also"></a>Weitere Informationen
- [Gewusst wie: Verwenden von integrierten einfärbbaren Elementen](../../extensibility/internals/how-to-use-built-in-colorable-items.md)
- [Benutzerdefinierte einfärbbare Elemente](../../extensibility/internals/custom-colorable-items.md)
- [Entwickeln eines Legacysprachdiensts](../../extensibility/internals/developing-a-legacy-language-service.md)
- [Einfärben der Syntax in einem Legacysprachdienst](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)

---
title: Implementieren von Syntax Farben | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- syntax coloring, implementing
- editors [Visual Studio SDK], colorizing text
- text, colorizing in editors
ms.assetid: 96e762ca-efd0-41e7-8958-fda4897c8c7a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cab338e253cca8c7f8457752980e7f3624317d9c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72727027"
---
# <a name="implementing-syntax-coloring"></a>Implementieren von Syntaxfarben
Wenn der Sprachdienst die farbliche Syntax Markierung bereitstellt, konvertiert der Parser eine Textzeile in ein Array von kolorierbaren Elementen und gibt Tokentypen zurück, die diesen färb baren Elementen entsprechen. Der Parser sollte Tokentypen zurückgeben, die zu einer Liste von kolatable-Elementen gehören. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zeigt jedes kolorierbare Element im Code Fenster entsprechend der Attribute an, die vom Farb Zeichenfolgenobjekt dem entsprechenden Tokentyp zugewiesen werden.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] keine parserschnittstelle angibt, und die Parser-Implementierung ist vollständig für Sie. Im Visual Studio-Sprachpaket Projekt wird jedoch eine standardmäßige Parser-Implementierung bereitgestellt. Bei verwaltetem Code bietet das Managed Package Framework (MPF) vollständige Unterstützung für die Farbgebung von Text.

 Legacy Sprachdienste werden als Teil eines VSPackages implementiert, aber die neuere Methode zum Implementieren von Sprachdienst Funktionen ist die Verwendung von MEF-Erweiterungen. Weitere Informationen zur neuen Methode zum Implementieren von Syntax Farben finden Sie unter Exemplarische Vorgehensweise [: Markieren von Text](../../extensibility/walkthrough-highlighting-text.md).

> [!NOTE]
> Es wird empfohlen, dass Sie so bald wie möglich mit der Verwendung der neuen Editor-API beginnen. Dadurch wird die Leistung Ihres sprach Dienstanbieter verbessert, und Sie können die neuen Editor-Features nutzen.

## <a name="steps-followed-by-an-editor-to-colorize-text"></a>Schritte, gefolgt von einem Editor zum Einfärben von Text

1. Der Editor Ruft die Farbgebung durch Aufrufen der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A>-Methode für das <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> Objekt ab.

2. Der Editor Ruft die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStateMaintenanceFlag%2A>-Methode auf, um zu bestimmen, ob die Farbgebung den Zustand der einzelnen Zeilen außerhalb der Farbgebung beibehalten muss.

3. Wenn die Farbgebung erfordert, dass der Zustand außerhalb der Farbgebung beibehalten wird, ruft der Editor die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStartState%2A>-Methode auf, um den Zustand der ersten Zeile zu erhalten.

4. Für jede Zeile im Puffer ruft der Editor die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>-Methode auf, die die folgenden Schritte ausführt:

    1. Die Textzeile wird an einen Scanner übermittelt, um den Text in Token zu konvertieren. Jedes Token gibt den Tokentext und den Tokentyp an.

    2. Der Tokentyp wird in einen Index in eine Liste der färb baren Elemente konvertiert.

    3. Die Tokeninformationen werden verwendet, um ein Array so auszufüllen, dass jedes Element des Arrays einem Zeichen in der Zeile entspricht. Die im Array gespeicherten Werte sind die Indizes in der Liste der färb baren Elemente.

    4. Der Status am Ende der Zeile wird für jede Zeile zurückgegeben.

5. Wenn die Farbgebung erfordert, dass der Zustand beibehalten wird, speichert der Editor den Zustand für diese Zeile zwischen.

6. Der Editor rendert die Textzeile mithilfe der Informationen, die von der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>-Methode zurückgegeben werden. Gehen Sie dazu folgendermaßen vor:

    1. Für jedes Zeichen in der Zeile wird der kolapable Item Index angezeigt.

    2. Wenn Sie die standardmäßigen Kolon-Elemente verwenden, greifen Sie auf die Liste der kolaktivierbaren Elemente des Editors zu

    3. Rufen Sie andernfalls die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>-Methode des sprach dienstanders auf, um ein Kolon-Element zu erhalten.

    4. Verwenden Sie die Informationen im Kolb baren Element, um den Text in der Anzeige zu erzeugen.

## <a name="managed-package-framework-colorizer"></a>Farbauswahl für Managed Package Framework
 Das Managed Package Framework (MPF) stellt alle Klassen bereit, die erforderlich sind, um eine Farbgebung zu implementieren. Ihre Sprachdienst Klasse sollte die <xref:Microsoft.VisualStudio.Package.LanguageService> Klasse erben und die erforderlichen Methoden implementieren. Sie müssen einen Scanner und einen Parser angeben, indem Sie die <xref:Microsoft.VisualStudio.Package.IScanner>-Schnittstelle implementieren und eine Instanz dieser Schnittstelle von der <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>-Methode (eine der Methoden, die in der <xref:Microsoft.VisualStudio.Package.LanguageService>-Klasse implementiert werden müssen) zurückgeben. Weitere Informationen finden Sie unter [Syntax Farbgebung in einem Legacy Sprachdienst](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).

## <a name="see-also"></a>Siehe auch
- [Gewusst wie: Verwenden von integrierten einfärbbaren Elementen](../../extensibility/internals/how-to-use-built-in-colorable-items.md)
- [Benutzerdefinierte einfärbbare Elemente](../../extensibility/internals/custom-colorable-items.md)
- [Entwickeln eines Legacysprachdiensts](../../extensibility/internals/developing-a-legacy-language-service.md)
- [Einfärben der Syntax in einem Legacysprachdienst](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)
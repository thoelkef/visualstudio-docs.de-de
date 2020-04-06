---
title: Syntax-Färbung in einem Legacy-Sprachdienst | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- syntax coloring
- language services, syntax coloring
ms.assetid: f65ff67e-8c20-497a-bebf-5e2a5b5b012f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2589ec24f230287306e0ff7e802d381fb6ab18b7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704756"
---
# <a name="syntax-coloring-in-a-legacy-language-service"></a>Syntaxfarben in einem Legacysprachdienst

Visual Studio verwendet einen Maldienst, um Elemente der Sprache zu identifizieren und sie mit den angegebenen Farben in einem Editor anzuzeigen.

## <a name="colorizer-model"></a>Colorizer-Modell
 Der Sprachdienst implementiert <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> die Schnittstelle, die dann von Editoren verwendet wird. Diese Implementierung ist ein separates Objekt vom Sprachdienst, wie in der folgenden Abbildung dargestellt:

 ![Grafik zur SVC-Farbdarstellung](../../extensibility/internals/media/figlgsvccolorizer.gif)

> [!NOTE]
> Der Syntax-Färbungsdienst ist vom allgemeinen Visual Studio-Mechanismus zum Färben von Text getrennt. Weitere Informationen zum [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] allgemeinen Mechanismus zur Unterstützung der Farbgekoloriierung finden Sie unter [Verwenden von Schriftarten und Farben](/visualstudio/extensibility/using-fonts-and-colors?view=vs-2015).

 Neben dem Colorizer kann der Sprachdienst benutzerdefinierte befärbbare Elemente bereitstellen, die vom Editor verwendet werden, indem er benutzerdefinierte befärbte Elemente bereitstellt. Sie können dies <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> tun, indem Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> Schnittstelle für dasselbe Objekt implementieren, das die Schnittstelle implementiert. Es gibt die Anzahl der benutzerdefinierten befärbbaren Elemente zurück, wenn der Editor <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> die Methode aufruft, und es gibt ein einzelnes benutzerdefiniertes befärbbares Element zurück, wenn der Editor die Methode aufruft.

 Die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> Methode gibt ein Objekt <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> zurück, das die Schnittstelle implementiert. Wenn der Sprachdienst 24-Bit- oder hohe Farbwerte unterstützt, muss er die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> Schnittstelle für dasselbe Objekt wie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> Schnittstelle implementieren.

## <a name="how-a-vspackage-uses-a-language-service-colorizer"></a>Wie ein VSPackage einen Language Service Colorizer verwendet

1. Das VSPackage muss den entsprechenden Sprachdienst abrufen, der den Sprachdienst VSPackage dazu verpflichtet, Folgendes zu tun:

    1. Verwenden Sie ein <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> Objekt, das die Schnittstelle implementiert, um den zu färbenden Text abzubekommen.

         Text wird in der Regel mit <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> einem Objekt angezeigt, das die Schnittstelle implementiert.

    2. Holen Sie sich den Sprachdienst ab, indem Sie den Dienstanbieter des VSPackage nach der Sprachdienst-GUID abfragen. Sprachdienste werden in der Registrierung durch Dateierweiterung identifiziert.

    3. Ordnen Sie den <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> Sprachdienst <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> dem zu, indem Sie seine Methode aufrufen.

2. Das VSPackage kann das Colorizer-Objekt nun wie folgt abrufen und verwenden:

    > [!NOTE]
    > VSPackages, die den Kerneditor verwenden, müssen die Colorizer-Objekte eines Sprachdienstes nicht explizit abrufen. Sobald eine Instanz des Kerneditors einen entsprechenden Sprachdienst erhält, führt sie alle hier gezeigten Farbierungsaufgaben aus.

    1. Rufen Sie das Colorizer-Objekt des Sprachdiensts ab, das <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>die implementiert, und <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2> Schnittstellen, indem Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> Methode für das Objekt des Sprachdiensts <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> aufrufen.

    2. Rufen <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> Sie die Methode auf, um die Colorizer-Informationen für eine bestimmte Textspanne abzurufen.

         <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>gibt ein Array von Werten zurück, einen für jedes Zeichen in der Textspanne, die koloriert wird. Die Werte sind Indizes in einer farbbaren Elementliste, die entweder die standardmäßige farbbare Elementliste ist, die vom Kerneditor verwaltet wird, oder eine benutzerdefinierte farbbare Elementliste, die vom Sprachdienst selbst verwaltet wird.

    3. Verwenden Sie die von <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> der Methode zurückgegebenen Farbinformationen, um den markierten Text anzuzeigen.

> [!NOTE]
> Neben der Verwendung eines Sprachdienst-Farbisierers kann ein VSPackage auch den allgemeinen Visual Studio-Textfärbemechanismus verwenden. Weitere Informationen zu diesem Mechanismus finden Sie unter [Verwenden von Schriftarten und Farben](/visualstudio/extensibility/using-fonts-and-colors?view=vs-2015).

## <a name="in-this-section"></a>In diesem Abschnitt
- [Implementieren von Syntaxfarben](../../extensibility/internals/implementing-syntax-coloring.md)

 Erläutert, wie ein Editor auf die Syntaxfärbung eines Sprachdienstes zugreift und was der Sprachdienst implementieren muss, um die Syntaxfärbung zu unterstützen.

- [Gewusst wie: Verwenden von integrierten einfärbbaren Elementen](../../extensibility/internals/how-to-use-built-in-colorable-items.md)

 Veranschaulicht, wie integrierte farbbare Elemente aus dem Sprachdienst verwendet werden.

- [Benutzerdefinierte einfärbbare Elemente](../../extensibility/internals/custom-colorable-items.md)

 Erläutert das Implementieren benutzerdefinierter befärbbarer Elemente.

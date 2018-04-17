---
title: Syntaxfarben in einen Legacy-Sprachdienst | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- syntax coloring
- language services, syntax coloring
ms.assetid: f65ff67e-8c20-497a-bebf-5e2a5b5b012f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 172f06f4e30f1320b6e17332cb2b54af91f7ed01
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="syntax-coloring-in-a-legacy-language-service"></a>Syntaxfarben in einen Legacy-Sprachdienst

Visual Studio verwendet einen Dienst Färbung identifizieren die Elemente der Sprache und mit den angegebenen Farben in einem Editor angezeigt werden können.

## <a name="colorizer-model"></a>Colorizer-Modell
 Der Language-Dienst implementiert die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> -Schnittstelle, die dann von Editoren verwendet wird. Diese Implementierung ist ein separates Objekt aus der Sprachdienst, wie in der folgenden Abbildung gezeigt:

 ![Grafik zur SVC-Farbdarstellung](../../extensibility/internals/media/figlgsvccolorizer.gif)

> [!NOTE]
>  Der Dienst für die Syntaxfarben wird getrennt von der Visual Studio-Mechanismus für die farbliche Kennzeichnung von Text. Weitere Informationen zu den allgemeinen [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] Mechanismus unterstützen farbliche Kennzeichnung, finden Sie unter [Verwenden von Schriftarten und Farben](../../extensibility/using-fonts-and-colors.md).

 Neben den Colorizer kann der Sprachdienst benutzerdefinierte färbbare Elemente angeben, die von Werbung vom Editor, verwendet werden, dass sie benutzerdefinierte färbbare Elemente bereitstellt. Hierzu können Sie durch die Implementierung der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> Schnittstelle für das gleiche Objekt, das implementiert die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> Schnittstelle. Es gibt die Anzahl der Elemente für benutzerdefinierte färbbare zurück, wenn der Editor Ruft die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> -Methode, und es gibt ein einzelne benutzerdefiniertes färbbare Element zurück, wenn der Editor aufruft die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> Methode.

 Die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> Methode gibt ein Objekt, implementiert die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> Schnittstelle. Der Sprachdienst 24-Bit- oder hohe Farbwerte unterstützt, müssen sie implementieren die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> Schnittstelle auf das gleiche Objekt wie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> Schnittstelle.

## <a name="how-a-vspackage-uses-a-language-service-colorizer"></a>Wie eine VSPackage eine Language Service Colorizer verwendet

1.  Das VSPackage benötigen der entsprechenden Sprachdienst, wofür den Sprachdienst VSPackage, um folgende Aktionen ausführen:

    1.  Verwenden Sie ein Objekt, durch die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> Schnittstelle zum Abrufen des Texts zu farbig hervorgehoben werden.

         Text wird in der Regel angezeigt, mit der ein Objekt, implementiert die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> Schnittstelle.

    2.  Abrufen des Sprachdiensts durch Abfragen den Dienstanbieter des VSPackage für die GUID des Sprachdiensts an. Dienste für Sprachen werden in der Registrierung durch die Dateierweiterung identifiziert.

    3.  Zuordnen der Sprachdienst mit der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> durch Aufrufen seiner <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> Methode.

2.  Das VSPackage kann jetzt abrufen und verwenden stattdessen das Colorizer wie folgt:

    > [!NOTE]
    > VSPackages, die die Core-Editor verwenden, müssen Sie einer anderen Sprache des Diensts Colorizer Objekte erhalten, die explizit nicht. Als eine Instanz des Editors Core die von einer entsprechenden Sprachdienst abgerufen werden, werden alle farbliche Kennzeichnung von Tasks, die hier gezeigten ausgeführt.

    1.  Abrufen der Sprachdienst Colorizer-Objekt, das implementiert die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>, und <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2> Schnittstellen, die durch Aufrufen der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> Methode auf der Sprachdienst <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> Objekt.

    2.  Rufen Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> Methode, um die Colorizer Informationen für einen bestimmten Zeitraum abgerufen.

         <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> Gibt ein Array von Werten, eine für jedes Zeichen in den Textabschnitt farbig hervorgehoben wird. Die Werte werden Indizes in einer Liste von färbbare Element, die die vom Editor Core verwaltet färbbare Element Standardliste oder eine benutzerdefinierte färbbare Element-Liste, die von der Sprachdienst selbst verwaltet wird.

    3.  Verwenden Sie die farbliche Kennzeichnung Informationen zurückgegeben werden, indem Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> Methode, um den ausgewählten Text anzuzeigen.

> [!NOTE]
>  Zusätzlich zur Verwendung einer anderen Sprache Dienst Colorizer, kann eine VSPackage auch die allgemeinen Visual Studio-Text Farbgebung Mechanismus verwenden. Weitere Informationen zu diesen Mechanismus, finden Sie unter [Verwenden von Schriftarten und Farben](../../extensibility/using-fonts-and-colors.md).

## <a name="in-this-section"></a>In diesem Abschnitt
 [Implementieren die Syntax Farbgebung](../../extensibility/internals/implementing-syntax-coloring.md) erläutert, wie ein Editor zugreift, eines Sprachdiensts Syntaxfarben und welche der Sprachdienst implementieren muss, um Farben für Syntax zu unterstützen.

 [Vorgehensweise: Verwenden integrierter Färbbare Elemente](../../extensibility/internals/how-to-use-built-in-colorable-items.md) veranschaulicht, wie integrierte färbbare Elemente aus der Sprachdienst.

 [Benutzerdefinierte Färbbare Elemente](../../extensibility/internals/custom-colorable-items.md) erläutert, wie benutzerdefinierte färbbare Elemente zu implementieren.

## <a name="see-also"></a>Siehe auch

- [Verwenden von Schriftarten und Farben](../../extensibility/using-fonts-and-colors.md)
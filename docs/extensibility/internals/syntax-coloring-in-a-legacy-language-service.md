---
title: Syntaxfarben in einen Legacy-Sprachdienst | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- syntax coloring
- language services, syntax coloring
ms.assetid: f65ff67e-8c20-497a-bebf-5e2a5b5b012f
caps.latest.revision: "22"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 88af397feba9b06eabd73ec23dcf1204ebe755e6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="syntax-coloring-in-a-legacy-language-service"></a>Syntaxfarben in einen Legacy-Sprachdienst
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]verwendet einen Dienst Färbung identifizieren die Elemente der Sprache und mit den angegebenen Farben in einem Editor angezeigt werden können.  
  
## <a name="colorizer-model"></a>Colorizer-Modell  
 Der Language-Dienst implementiert die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> -Schnittstelle, die dann von Editoren verwendet wird. Diese Implementierung ist ein separates Objekt aus der Sprachdienst, wie in der folgenden Abbildung dargestellt.  
  
 ![Grafik zur SVC-Farbdarstellung](../../extensibility/internals/media/figlgsvccolorizer.gif "FigLgSvcColorizer")  
Einfache Colorizer-Modell  
  
> [!NOTE]
>  Der Dienst für die Syntaxfarben ist unabhängig von den allgemeinen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Mechanismus für die farbliche Kennzeichnung von Text. Weitere Informationen zu den allgemeinen [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] Mechanismus unterstützen farbliche Kennzeichnung, finden Sie unter [Verwenden von Schriftarten und Farben](../../extensibility/using-fonts-and-colors.md).  
  
 Neben den Colorizer kann der Sprachdienst benutzerdefinierte färbbare Elemente angeben, die von Werbung vom Editor verwendet werden, dass sie benutzerdefinierte färbbare Elemente bereitstellt. Hierzu können Sie durch die Implementierung der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> Schnittstelle für das gleiche Objekt, das implementiert die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> Schnittstelle. Es gibt die Anzahl der Elemente für benutzerdefinierte färbbare zurück, wenn der Editor Ruft die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> -Methode, und es gibt ein einzelne benutzerdefiniertes färbbare Element zurück, wenn der Editor aufruft die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> Methode.  
  
 Die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> Methode gibt ein Objekt, implementiert die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> Schnittstelle. Der Sprachdienst 24-Bit- oder hohe Farbwerte unterstützt, müssen sie implementieren die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> Schnittstelle auf das gleiche Objekt wie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> Schnittstelle.  
  
## <a name="how-a-vspackage-uses-a-language-service-colorizer"></a>Wie eine VSPackage eine Language Service Colorizer verwendet  
  
1.  Das VSPackage benötigen der entsprechenden Sprachdienst, wofür den Sprachdienst VSPackage, um folgende Aktionen ausführen:  
  
    1.  Verwenden Sie ein Objekt, durch die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> Schnittstelle zum Abrufen des Texts zu farbig hervorgehoben werden.  
  
         Text wird in der Regel angezeigt, mit der ein Objekt, implementiert die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> Schnittstelle.  
  
    2.  Abrufen des Sprachdiensts durch Abfragen den Dienstanbieter des VSPackage für die GUID des Sprachdiensts an. Dienste für Sprachen werden in der Registrierung durch die Dateierweiterung identifiziert.  
  
    3.  Zuordnen der Sprachdienst mit der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> durch Aufrufen seiner <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> Methode.  
  
2.  Das VSPackage kann jetzt abrufen und verwenden stattdessen das Colorizer wie folgt:  
  
    > [!NOTE]
    >  VSPackages, die die Core-Editor verwendet keiner anderen Sprache des Diensts Colorizer Objekte explizit zu erhalten. Als eine Instanz des Editors Core die von einer entsprechenden Sprachdienst abgerufen werden, werden alle farbliche Kennzeichnung von Tasks, die hier gezeigten ausgeführt.  
  
    1.  Abrufen der Sprachdienst Colorizer-Objekt, das implementiert die `T:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer`, und <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2> Schnittstellen, die durch Aufrufen der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> Methode auf der Sprachdienst <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> Objekt.  
  
    2.  Rufen Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> Methode, um die Colorizer Informationen für einen bestimmten Zeitraum abgerufen.  
  
         <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>Gibt ein Array von Werten, eine für jedes Zeichen in den Textabschnitt farbig hervorgehoben wird. Die Werte werden Indizes in einer Liste von färbbare Element, die die vom Editor Core verwaltet färbbare Element Standardliste oder eine benutzerdefinierte färbbare Element-Liste, die von der Sprachdienst selbst verwaltet wird.  
  
    3.  Verwenden Sie die farbliche Kennzeichnung Informationen zurückgegeben werden, indem Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> Methode, um den ausgewählten Text anzuzeigen.  
  
> [!NOTE]
>  Zusätzlich zur Verwendung einer anderen Sprache Dienst Colorizer, eine VSPackage können auch die allgemeine [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Farbgebung Mechanismus Text. Weitere Informationen zu diesen Mechanismus, finden Sie unter [Verwenden von Schriftarten und Farben](../../extensibility/using-fonts-and-colors.md).  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Implementieren von Syntaxfarben](../../extensibility/internals/implementing-syntax-coloring.md)  
 Erläutert, wie ein Editor zugreift, eines Sprachdiensts Syntaxfarben und welche der Sprachdienst müssen implementieren, um die Syntax zu unterstützen, Farbgebung.  
  
 [Gewusst wie: Verwenden von integrierten einfärbbaren Elementen](../../extensibility/internals/how-to-use-built-in-colorable-items.md)  
 Veranschaulicht, wie integrierte färbbare Elemente aus der Sprachdienst.  
  
 [Benutzerdefinierte einfärbbare Elemente](../../extensibility/internals/custom-colorable-items.md)  
 Erläutert das benutzerdefinierte färbbare Elemente zu implementieren.  
  
## <a name="see-also"></a>Siehe auch  
 [Verwenden von Schriftarten und Farben](../../extensibility/using-fonts-and-colors.md)
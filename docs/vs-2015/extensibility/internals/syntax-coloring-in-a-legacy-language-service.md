---
title: Syntaxfarben in einem Legacysprachdienst | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- syntax coloring
- language services, syntax coloring
ms.assetid: f65ff67e-8c20-497a-bebf-5e2a5b5b012f
caps.latest.revision: 23
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8f57d4c8b3c606fa5f954755d6a7f07c2ab00a89
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49253838"
---
# <a name="syntax-coloring-in-a-legacy-language-service"></a>Syntaxfarben in einem Legacysprachdienst
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] verwendet einen Farben-Dienst identifizieren die Elemente der Sprache und mit den angegebenen Farben in einem Editor anzeigen.  
  
## <a name="colorizer-model"></a>Farbauswahl-Modell  
 Der Language-Dienst implementiert die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> -Schnittstelle, die dann von Editoren verwendet wird. Diese Implementierung ist ein separates Objekt aus der Sprachdienst an, wie in der folgenden Abbildung dargestellt.  
  
 ![Grafik zu SVC-Farbdarstellung](../../extensibility/internals/media/figlgsvccolorizer.gif "FigLgSvcColorizer")  
Einfache Farbauswahl-Modell  
  
> [!NOTE]
>  Der Dienst für die Syntaxfarben unterscheidet sich von den allgemeinen [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Mechanismus zum farbigen Anzeigen von Text. Weitere Informationen zu den allgemeinen [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] Mechanismus unterstützen die farbliche Kennzeichnung, finden Sie unter [Verwenden von Schriftarten und Farben](../../extensibility/using-fonts-and-colors.md).  
  
 Neben der Farbauswahl kann der Sprachdienst benutzerdefinierte kolorierbare Elemente bereitstellen, die vom Editor durch Werbung dienen, dass sie benutzerdefinierte kolorierbare Elemente bereitstellt. Implementieren Sie hierzu die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> Schnittstelle für das gleiche Objekt, das implementiert die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> Schnittstelle. Es gibt die Anzahl der benutzerdefinierten kolorierbaren Elemente zurück, wenn der Editor aufruft der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> -Methode, und es gibt ein einzelne benutzerdefiniertes kolorierbare Element zurück, wenn der Editor Ruft die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> Methode.  
  
 Die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> -Methode gibt ein Objekt, das implementiert die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> Schnittstelle. Wenn der Sprachdienst 24-Bit-oder eine hohe Werte unterstützt, müssen sie implementieren die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> Schnittstelle auf dasselbe Objekt wie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> Schnittstelle.  
  
## <a name="how-a-vspackage-uses-a-language-service-colorizer"></a>Wie eine VSPackage eine Sprachendienst-Farbauswahl verwendet  
  
1.  Das VSPackage muss entsprechende Sprachdiensts, zum Abrufen den Sprachdienst VSPackage, um die folgenden Schritte ausführen müssen:  
  
    1.  Verwenden Sie ein Objekt, das die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> Schnittstelle zum Abrufen des Texts, die eingefärbt werden.  
  
         Text wird in der Regel mithilfe eines Objekts, das implementiert die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> Schnittstelle.  
  
    2.  Den Sprachdienst durch Abfragen den Dienstanbieter des VSPackage für die der Sprachdienst-GUID zu erhalten. Dienste für Sprachen werden in der Registrierung über die Dateierweiterung identifiziert.  
  
    3.  Zuordnen den Sprachdienst mit der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> durch Aufrufen der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> Methode.  
  
2.  Das VSPackage kann jetzt abrufen und verwenden die Farbauswahl-Objekt wie folgt:  
  
    > [!NOTE]
    >  VSPackages, die den Kern-Editor verwenden keiner Sprache des Diensts Farbauswahl Objekte explizit abrufen. Sobald eine Instanz von der Kern-Editor eine entsprechende Sprachdienst erhält, führt es alle hier gezeigten farbliche Kennzeichnung von Aufgaben.  
  
    1.  Abrufen der Sprachdienst Farbauswahl-Objekt, das implementiert die `T:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer`, und <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2> Schnittstellen, die durch Aufrufen der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> Methode auf des Sprachdiensts <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> Objekt.  
  
    2.  Rufen Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> Methode, um die Farbauswahl-Informationen für einen bestimmten Bereich des Texts zu erhalten.  
  
         <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> Gibt ein Array von Werten, eines für jedes Zeichen im Textabschnitt farbig hervorgehoben wird. Die Werte sind Indizes in einer Liste von kolorierbaren Elements, die entweder den kolorierbaren Elements Standardliste vom kerneditor beibehalten oder eine benutzerdefinierte färbbare Elementliste verwaltet vom Sprachdienst selbst ist.  
  
    3.  Verwenden Sie die farbliche Kennzeichnung von Informationen zurückgegeben werden, indem die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> Methode, um den ausgewählten Text anzuzeigen.  
  
> [!NOTE]
>  Neben der Verwendung einer Sprachendienst-Farbauswahl können eine VSPackage können Sie auch die allgemeine [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Farben Mechanismus Text. Weitere Informationen zu diesen Mechanismus, finden Sie unter [Verwenden von Schriftarten und Farben](../../extensibility/using-fonts-and-colors.md).  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Implementieren von Syntaxfarben](../../extensibility/internals/implementing-syntax-coloring.md)  
 Erläutert, wie ein Editor zugreift, einer editortooloptionsseite des Sprachdiensts farbige syntaxmarkierung und welche der Sprachdienst müssen implementieren, um Syntax zu unterstützen färben.  
  
 [Gewusst wie: Verwenden von integrierten einfärbbaren Elementen](../../extensibility/internals/how-to-use-built-in-colorable-items.md)  
 Veranschaulicht, wie mit integrierten kolorierbaren Elemente des sprachdienstes.  
  
 [Benutzerdefinierte einfärbbare Elemente](../../extensibility/internals/custom-colorable-items.md)  
 Erläutert, wie benutzerdefinierte kolorierbare Elemente implementieren.  
  
## <a name="see-also"></a>Siehe auch  
 [Verwenden von Schriftarten und Farben](../../extensibility/using-fonts-and-colors.md)


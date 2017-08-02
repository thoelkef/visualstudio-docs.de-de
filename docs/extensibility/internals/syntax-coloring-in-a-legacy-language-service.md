---
title: "Syntaxfarben in eine Legacy-Sprachdienst | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Syntaxfarben"
  - "Sprachdienste, Farben für Syntax"
ms.assetid: f65ff67e-8c20-497a-bebf-5e2a5b5b012f
caps.latest.revision: 22
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 22
---
# Syntaxfarben in eine Legacy-Sprachdienst
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] verwendet einen Farbton für, um Elemente der Sprache zu identifizieren und mit den angegebenen Farben in einem Editor anzuzeigen.  
  
## Modell der farbigen Darstellung  
 Der Sprachdienst implementiert die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>\-Schnittstelle, die dann von Editoren verwendet wird.  Diese Implementierung ist ein separates Objekt aus dem Sprachdienst, wie in der folgenden Abbildung gezeigt.  
  
 ![Grafik zur SVC&#45;Farbdarstellung](~/extensibility/internals/media/figlgsvccolorizer.gif "FigLgSvcColorizer")  
Einfaches Modell der farbigen Darstellung  
  
> [!NOTE]
>  Der Syntaxfarben ist getrennt von dem für [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Darfarbig allgemeinen Mechanismus zum Erstellen des Texts.  Weitere Informationen zu den allgemeinen Mechanismus [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] , der das Darfarbig unterstützt werden, finden Sie unter [Verwenden von Schriftarten und Farben](../../extensibility/using-fonts-and-colors.md).  
  
 Neben dem farbigen Darstellung kann der Sprachdienst benutzerdefinierte färbbare Elemente enthalten, die vom Editor verwendet werden, indem sie benutzerdefinierte färbbare Elemente dieser Beschreibung ein, ankündigt.  Dazu können Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems>\-Schnittstelle für dasselbe Objekt implementieren, das die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>\-Schnittstelle implementiert.  Sie gibt die Anzahl der benutzerdefinierten färbbaren Elementen zurück, wenn der Editor die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A>\-Methode aufruft und gibt ein einzelnes benutzerdefiniertes färbbares Element zurück, wenn der Editor die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>\-Methode aufgerufen wird.  
  
 Die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>\-Methode gibt ein Objekt zurück, das die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>\-Schnittstelle implementiert.  Wenn der Sprachdienst 24\-Bit oder hohe Farbwerte unterstützt, muss er die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem>\-Schnittstelle für dasselbe Objekt wie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>\-Schnittstelle implementieren.  
  
## Wie ein VSPackage über eine Sprachendienst\-farbige Darstellung verwendet  
  
1.  VSPackage muss den entsprechenden Sprachdienst abrufen, der den Sprachdienst VSPackage für folgende Aufgaben:  
  
    1.  Verwenden Sie ein Objekt, das die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>\-Schnittstelle implementiert, um die getönt werden soll, Text abgerufen.  
  
         Text wird in der Regel mithilfe eines Objekts angezeigt, das die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>\-Schnittstelle implementiert.  
  
    2.  Rufen Sie den Sprachdienst, indem Sie den Dienstanbieter VSPackages für den Sprachdienst GUIDs abfragen.  Sprachendienste werden in der Registrierung durch Dateierweiterung identifiziert.  
  
    3.  Ordnen Sie den Sprachdienst mit <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> zu, indem Sie seine <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A>\-Methode aufrufen.  
  
2.  Jetzt kann ein VSPackage abrufen und das Objekt der farbigen Darstellung verwenden wie folgt:  
  
    > [!NOTE]
    >  VSPackages, die den Kern des Editors verwenden, müssen nicht explizit erhalten Objekte der farbigen Darstellung des Sprachdiensts.  Sobald eine Instanz des zentralen editors ein entsprechender Sprachdienst erhält, listet sie alle Farbauftrag Aufgaben aus, die hier angezeigt werden.  
  
    1.  Rufen Sie das Objekt der farbigen Darstellung des Sprachdiensts, das `T:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer`implementiert, und <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2>\-Schnittstellen, indem sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A>\-Methode auf dem <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>\-Objekt des Sprachdiensts aufrufen.  
  
    2.  Rufen Sie die Methode an <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> zum Abrufen der Informationen der farbigen Darstellung für einen bestimmten Textabschnitt.  
  
         <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> gibt ein Array von Werten, einen für jedes Zeichen im Textabschnitt zurück, der getönt werden soll.  Die Werte sind Indizes in eine Elementliste färbbare, die entweder die standardmäßige färbbare Elementliste darstellt, die vom Kern des Editors übernommen werden oder eine benutzerdefinierte färbbare Elementliste, die vom Sprachdienst selbst ausgeführt wird.  
  
    3.  Verwenden Sie die Farbauftrag Informationen, die von der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>\-Methode zurückgegeben werden, um den ausgewählten Text anzuzeigen.  
  
> [!NOTE]
>  Neben der Verwendung einer Sprachdienst farbigen kann ein VSPackage die allgemeine Darstellung [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Text auch Mechanismus zur farbton verwenden.  Weitere Informationen zu diesem Verfahren finden Sie unter [Verwenden von Schriftarten und Farben](../../extensibility/using-fonts-and-colors.md).  
  
## In diesem Abschnitt  
 [Implementieren von Farben für Syntax](../../extensibility/internals/implementing-syntax-coloring.md)  
 Erläutert, wie ein Editor eine Syntaxfarbe des Sprachdiensts zugreift und was der Sprachdienst implementieren muss, um Syntaxfarbe zu unterstützen.  
  
 [Gewusst wie: Verwenden von integrierten Färbbare Elemente](../../extensibility/internals/how-to-use-built-in-colorable-items.md)  
 Veranschaulicht, wie eine integrierte färbbare Elemente aus dem Sprachdienst verwendet.  
  
 [Benutzerdefinierte Färbbare Elemente](../../extensibility/internals/custom-colorable-items.md)  
 Erläutert, wie benutzerdefinierte färbbare Elemente implementiert.  
  
## Siehe auch  
 [Verwenden von Schriftarten und Farben](../../extensibility/using-fonts-and-colors.md)
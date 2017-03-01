---
title: "Gliederung-Unterstützung in eine Sprachdienst bereitstellen | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], outlining support
- language services, supporting outlining
- outlining, supporting
ms.assetid: df759e89-8193-418c-8038-6626304d387b
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: d5bc147592bfc36247c35f23ac2885055d096af3
ms.openlocfilehash: fc502e4430a49284cffe14386249999d82085f1c
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-provide-expanded-outlining-support-in-a-legacy-language-service"></a>Gewusst wie: unterstützen erweiterte Gliederung in eine Legacy-Sprachdienst
Es gibt zwei Optionen zur Erweiterung der Gliederung Unterstützung für Ihre Sprache unterstützen die **Definitionen** Befehl. Sie können Editor-gesteuerten Gliederungsbereiche hinzufügen und Hinzufügen von Client-gesteuerten Gliederungsbereiche.  
  
## <a name="adding-editor-controlled-outline-regions"></a>Editor-gesteuerten Gliederungsbereiche hinzufügen  
 Mithilfe dieser Vorgehensweise erstellen einen Gliederungsbereich und lassen Sie den Editor zu behandeln, ob der Bereich erweitert wird, reduziert, und so weiter. Diese Option ist der beiden Optionen für den Gliederungsrand Support die am wenigsten robuste. Bei dieser Option erstellen Sie eine neue Gliederungsbereich über einen angegebenen Zeitraum Text mit <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A>.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> Nachdem dieser Region erstellt wird, wird das Verhalten vom Editor gesteuert. Verwenden Sie das folgende Verfahren, um Editor-gesteuerten Gliederungsbereiche implementieren.  
  
#### <a name="to-implement-an-editor-controlled-outline-region"></a>Implementieren Sie einen Editor-gesteuerten Gliederungsbereich  
  
1.  Rufen Sie `QueryService` für<xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager></xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>  
  
     Gibt einen Zeiger <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>  
  
2.  Rufen Sie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>und übergeben eines Zeigers für einen angegebenen Textpuffer.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A> Gibt einen Zeiger auf die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>Objekt für den Puffer.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>  
  
3.  Rufen Sie <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A>für <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>einen Zeiger zu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession>.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> </xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A>  
  
4.  Rufen Sie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A>Fügen Sie eine oder mehrere neue Bereiche gleichzeitig gliedern.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A>  
  
     Diese Methode können Sie an der Textabschnitt Gliederung, ob vorhandene Gliederungsbereiche entfernt oder beibehalten werden und gibt an, ob die Gliederungsbereich erweitert oder reduziert werden, in der Standardeinstellung ist.  
  
## <a name="adding-client-controlled-outline-regions"></a>Hinzufügen von Client-gesteuerten Gliederungsbereiche  
 Verwenden Sie diesen Ansatz zur Gliederung implementieren Client gesteuerter (oder klug) installieren möchten, die von verwendet die [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] und [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] Sprachdienste. Ein Language-Dienst, der verwaltet einen eigenen Gliederung überwacht der Pufferinhalt Text, um alte Gliederungsbereiche zerstört, wenn sie ungültig und neue Gliederungsbereiche Bedarf zu erstellen.  
  
#### <a name="to-implement-a-client-controlled-outline-region"></a>Ein vom Client gesteuerter Gliederungsbereich implementieren  
  
1.  Rufen Sie `QueryService` <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>.</xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> Gibt einen Zeiger <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>  
  
2.  Rufen Sie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>und übergeben eines Zeigers für einen angegebenen Textpuffer.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A> Bestimmt, ob die Sitzung ausgeblendeten Text bereits für den Puffer vorhanden ist.  
  
3.  Wenn eine Text-Sitzung bereits vorhanden ist, Sie müssen nicht zum Erstellen eines und einen Zeiger auf die vorhandene <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>Objekt zurückgegeben wird.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> Verwenden Sie zum Auflisten und Gliederungsbereiche erstellen this-Zeiger. Rufen Sie andernfalls <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A>zum Erstellen einer Sitzung ausgeblendeten Text für den Puffer.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> Ein Zeiger auf die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>-Objekt zurückgegeben wird.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>  
  
    > [!NOTE]
    >  Beim Aufruf von <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A>, Sie können angeben, dass einen Client ausgeblendeten Text (d. h. ein <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient>Objekt).</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> Dieser Client benachrichtigt, wenn eine ausgeblendeten Text oder Gliederungsbereich erweitert oder reduziert werden, indem der Benutzer ist.  
  
4.  Rufen Sie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A>Struktur) Parameter: Geben Sie den Wert <xref:Microsoft.VisualStudio.TextManager.Interop.HIDDEN_REGION_TYPE>in den `iType` Mitglied der <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>Struktur, um anzugeben, dass Sie einen Gliederungsbereich, anstatt einen ausgeblendeten Bereich erstellen.</xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> </xref:Microsoft.VisualStudio.TextManager.Interop.HIDDEN_REGION_TYPE> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> Angeben, ob der Bereich ist der Client gesteuerter oder Editor gesteuert, in der `dwBehavior` Mitglied der <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>Struktur.</xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> Die intelligente Gliederungsrand Implementierung kann eine Mischung aus Editor und Client gesteuerter Gliederungsbereiche enthalten. Geben Sie den Bannertext, der angezeigt wird, wenn Ihre Gliederungsbereich, z. B. "...", in reduziert wird die `pszBanner` Mitglied der <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>Struktur.</xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> Die Editor Banner Standardtext für einen ausgeblendeten Bereich ist "...".

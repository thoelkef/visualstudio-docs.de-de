---
title: Geben Sie die Unterstützung in einen Sprachdienst | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], outlining support
- language services, supporting outlining
- outlining, supporting
ms.assetid: df759e89-8193-418c-8038-6626304d387b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6467a1e3386daedc4a67aa420c06cf01187b8d22
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31132144"
---
# <a name="how-to-provide-expanded-outlining-support-in-a-legacy-language-service"></a>Vorgehensweise: Erweiterte Gliederung in bieten Unterstützung für ein Legacy-Sprachdienst
Es gibt zwei Optionen zur Erweiterung Gliederungsmodus Unterstützung für Ihre Sprache nicht nur Unterstützung für die **Definitionen** Befehl. Sie können hinzufügen-Editor-gesteuerten Gliederungsbereiche und Client-gesteuerten Gliederungsbereiche.  
  
## <a name="adding-editor-controlled-outline-regions"></a>Editor-gesteuerten Gliederungsbereiche hinzufügen  
 Verwenden Sie diesen Ansatz, um einen Gliederungsbereich erstellen, und lassen Sie den Editor zu behandeln, ob der Bereich erweitert wird, reduziert, usw. Der beiden Optionen für Gliederungsmodus Support bereitstellen ist diese Option am wenigsten robuste. Bei dieser Option erstellen Sie eine neue Gliederungsbereich über eine angegebene Spanne von Text mit <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A>. Nachdem dieser Region erstellt wird, wird das Verhalten vom Editor gesteuert. Verwenden Sie das folgende Verfahren, um-Editor-gesteuerten Gliederungsbereiche implementieren.  
  
#### <a name="to-implement-an-editor-controlled-outline-region"></a>Um einen Editor-gesteuerten Gliederungsbereich zu implementieren.  
  
1.  Rufen Sie `QueryService` für <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>  
  
     Dies gibt einen Zeiger auf <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>.  
  
2.  Rufen Sie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>, und übergeben Sie einen Zeiger für einen angegebenen Text-Puffer. Dies gibt einen Zeiger auf die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> Objekt für den Puffer.  
  
3.  Rufen Sie <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> auf <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> für einen Zeiger auf <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession>.  
  
4.  Rufen Sie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> fügen Sie einen oder mehrere neue Bereiche zu einem Zeitpunkt werden kann.  
  
     Diese Methode ermöglicht Ihnen die Angabe den Textabschnitt Kontur, gibt an, ob vorhandene Gliederungsbereiche entfernt oder beibehalten werden und gibt an, ob die Gliederungsbereich erweitert oder reduziert werden, in der Standardeinstellung ist.  
  
## <a name="adding-client-controlled-outline-regions"></a>Hinzufügen von Client-gesteuerten Gliederungsbereiche  
 Mithilfe dieser Ansatz hinsichtlich der Gliederung implementieren Client gesteuert (oder Smartcard) installieren möchten, die verwendet werden, indem Sie die [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] und [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] Sprachdienste. Ein Sprachdienst, der verwaltet einen eigenen Gliederung überwacht der Inhalt des Puffers an, um alte Gliederungsbereiche zerstört, wenn sie verliert seine Gültigkeit und neue Gliederungsbereiche nach Bedarf erstellen.  
  
#### <a name="to-implement-a-client-controlled-outline-region"></a>Um eine Client-gesteuerten Gliederungsbereich zu implementieren.  
  
1.  Rufen Sie `QueryService` für <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>. Dies gibt einen Zeiger auf <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>.  
  
2.  Rufen Sie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>, und übergeben Sie einen Zeiger für einen angegebenen Text-Puffer. Dies bestimmt, ob bereits eine Sitzung für ausgeblendeten Text für den Puffer vorhanden ist.  
  
3.  Wenn bereits eine Sitzung für Text vorhanden ist, Sie müssen nicht zum Erstellen einer und einen Zeiger auf den vorhandenen <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> Objekt wird zurückgegeben. Mit diesem Zeiger können aufgelistet, und erstellen Gliederungsbereiche. Rufen Sie andernfalls <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> zur Erstellung einer Sitzung ausgeblendetem Text für den Puffer. Ein Zeiger auf die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> Objekt wird zurückgegeben.  
  
    > [!NOTE]
    >  Beim Aufruf <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A>, Sie können angeben, dass einen Client ausgeblendetem Text (d. h. ein <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient> Objekt). Dieser Client benachrichtigt Sie bei einem ausgeblendeten Text oder Gliederungsbereich erweitert oder reduziert, die vom Benutzer.  
  
4.  Rufen Sie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> Struktur) Parameter: Geben Sie den Wert <xref:Microsoft.VisualStudio.TextManager.Interop.HIDDEN_REGION_TYPE> in der `iType` Mitglied der <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> Struktur, um anzugeben, dass Sie einen Gliederungsbereich, anstatt einen ausgeblendeten Bereich erstellen. Gibt an, ob der Bereich ist der Client gesteuert oder Editor gesteuert, in der `dwBehavior` Mitglied der <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> Struktur. Die intelligente Gliederungsmodus Implementierung darf eine Mischung aus Gliederungsbereiche Editor und der Client gesteuert. Geben Sie den Bannertext an, die angezeigt wird, wenn Ihre Gliederungsbereich, z. B. "..." im reduziert ist die `pszBanner` Mitglied der <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> Struktur. Der Editor Banner Standardtext für einen ausgeblendeten Bereich ist "..." aus.
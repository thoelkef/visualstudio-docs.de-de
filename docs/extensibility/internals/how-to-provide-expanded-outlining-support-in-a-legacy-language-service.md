---
title: Geben Sie die Unterstützung in einem Sprachdienst | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], outlining support
- language services, supporting outlining
- outlining, supporting
ms.assetid: df759e89-8193-418c-8038-6626304d387b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 13bfa8abacbd8f9bd4b604c5a2389981c192b86e
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66312131"
---
# <a name="how-to-provide-expanded-outlining-support-in-a-legacy-language-service"></a>Vorgehensweise: Geben Sie die Unterstützung für erweiterten Gliederungen in einem legacy-Sprachdienst
Es gibt zwei Optionen zum Erweitern der Gliederung Unterstützung für Ihre Sprache zu unterstützen, die **reduzieren auf Definitionen** Befehl. Sie können editorgesteuert Gliederungsbereiche hinzufügen und Hinzufügen von Client-gesteuerten Gliederungsbereiche.

## <a name="adding-editor-controlled-outline-regions"></a>Hinzufügen von editorgesteuert Gliederungsbereiche
 Verwenden Sie diesen Ansatz, um einen Gliederungsbereich erstellen, und lassen Sie den Editor zu verarbeiten, ob der Bereich erweitert wird, reduziert, und so weiter. Diese Option ist der beiden Optionen für die Bereitstellung Gliederung Support die am wenigsten robuste. Bei dieser Option erstellen Sie ein neuen Gliederungsbereichs über eine angegebene Spanne von Text mit <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A>. Nachdem dieser Region erstellt wird, wird das Verhalten vom Editor gesteuert. Verwenden Sie das folgende Verfahren, um editorgesteuert Gliederungsbereiche zu implementieren.

### <a name="to-implement-an-editor-controlled-outline-region"></a>Um einen editorgesteuert Gliederungsbereich zu implementieren.

1. Rufen Sie `QueryService` für <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>

     Gibt einen Zeiger auf <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>.

2. Rufen Sie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>, und übergeben Sie einen Zeiger für einen angegebenen Textpuffer. Gibt einen Zeiger auf die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> Objekt für den Puffer.

3. Rufen Sie <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> auf <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> für einen Zeiger auf <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession>.

4. Rufen Sie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> auf ein oder mehrere neue Regionen zu einem Zeitpunkt beschrieben.

     Diese Methode ermöglicht Ihnen die Angabe der Textabschnitt, Gliederung, gibt an, ob vorhandene Gliederungsbereiche entfernt oder beibehalten werden, und gibt an, ob die Gliederungsbereich erweitert oder wird, wird standardmäßig reduziert der.

## <a name="add-client-controlled-outline-regions"></a>Fügen Sie die Client-gesteuerten Gliederungsbereiche
 Dieser Ansatz zu implementieren, die Client-gesteuert (oder klug) zu gliedern, die von verwendet, z. B. Verwenden der [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] und [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] Sprachdienste. Ein Sprachdienst, der verwaltet einen eigenen Gliederung überwacht den Textinhalt der Puffer, um alte Gliederungsbereiche zerstört, wenn sie ungültig werden und neue Gliederungsbereiche nach Bedarf erstellen.

### <a name="to-implement-a-client-controlled-outline-region"></a>Um einen Client gesteuerter Gliederungsbereich zu implementieren.

1. Rufen Sie `QueryService` für <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>. Gibt einen Zeiger auf <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>.

2. Rufen Sie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>, und übergeben Sie einen Zeiger für einen angegebenen Textpuffer. Dadurch wird bestimmt, ob bereits eine Sitzung des ausgeblendeten Textes für den Puffer vorhanden ist.

3. Wenn eine Sitzung des Textes bereits vorhanden ist, Sie müssen nicht zum Erstellen einer und einen Zeiger auf die vorhandene <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> Objekt zurückgegeben. Verwenden Sie diesen Zeiger, auflisten und erstellen Gliederungsbereiche. Rufen Sie andernfalls <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> um eine Sitzung des ausgeblendeten Textes für den Puffer zu erstellen. Ein Zeiger auf die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> Objekt zurückgegeben.

    > [!NOTE]
    > Beim Aufruf <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A>, Sie können einen ausgeblendeten textclient angeben (d. h. eine <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient> Objekt). Dieser Client benachrichtigt, wenn eine ausgeblendeten Text oder Gliederungsbereich erweitert oder reduziert wird, durch den Benutzer.

4. Rufen Sie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> Struktur) Parameter: Geben Sie den Wert <xref:Microsoft.VisualStudio.TextManager.Interop.HIDDEN_REGION_TYPE> in die `iType` Mitglied der <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> Struktur, um anzugeben, dass Sie einen Gliederungsbereich, anstatt einen ausgeblendeten Bereich erstellen. Gibt an, ob der Bereich ist die Client-gesteuert oder Editor gesteuert werden, in der `dwBehavior` Mitglied der <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> Struktur. Die intelligente Gliederung Implementierung kann eine Mischung aus und Client-editorgesteuert Gliederungsbereiche enthalten. Geben Sie den Bannertext, der angezeigt wird, wenn Ihre Gliederungsbereich, z. B. "...", in reduziert ist die `pszBanner` Mitglied der <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> Struktur. Die Anmerkung der Redaktion Banner Standardtext für einen ausgeblendeten Bereich ist "...".
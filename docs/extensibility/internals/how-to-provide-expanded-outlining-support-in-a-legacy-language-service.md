---
title: Bereitstellen von Umrissunterstützung in einem Sprachdienst | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], outlining support
- language services, supporting outlining
- outlining, supporting
ms.assetid: df759e89-8193-418c-8038-6626304d387b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 37deafa92477289a2124ecee101dd254e68ef01d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707968"
---
# <a name="how-to-provide-expanded-outlining-support-in-a-legacy-language-service"></a>Gewusst wie: Erweiterte Umrissunterstützung in einem legacy Sprachdienst bereitstellen
Es gibt zwei Möglichkeiten, die Umrissunterstützung für Ihre Sprache über die Unterstützung des **Befehls "Auf Definitionen reduzieren"** hinaus zu erweitern. Sie können editorgesteuerte Gliederungsbereiche und clientgesteuerte Gliederungsbereiche hinzufügen.

## <a name="adding-editor-controlled-outline-regions"></a>Hinzufügen von editorgesteuerten Gliederungsbereichen
 Verwenden Sie diesen Ansatz, um einen Gliederungsbereich zu erstellen, und lassen Sie dann dem Editor zu, ob die Region erweitert, reduziert usw. ist. Von den beiden Optionen für die Bereitstellung von Unterstützung ist diese Option die am wenigsten robuste. Für diese Option erstellen Sie einen neuen Gliederungsbereich über einen angegebenen Textbereich mit <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A>. Nachdem dieser Bereich erstellt wurde, wird sein Verhalten vom Editor gesteuert. Verwenden Sie das folgende Verfahren, um editorgesteuerte Gliederungsbereiche zu implementieren.

### <a name="to-implement-an-editor-controlled-outline-region"></a>So implementieren Sie eine editorgesteuerte Gliederungsregion

1. Call `QueryService` for<xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>

     Dadurch wird ein <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>Zeiger auf zurückgegeben.

2. Rufen <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>Sie auf, und übergeben Sie einen Zeiger für einen bestimmten Textpuffer. Dadurch wird ein Zeiger <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> auf das Objekt für den Puffer zurückgegeben.

3. Rufen Sie <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> einen Zeiger <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession>auf an. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>

4. Rufen <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> Sie auf, um jeweils eine oder mehrere neue Gliederungsbereiche hinzuzufügen.

     Mit dieser Methode können Sie die zu umreißende Textspanne angeben, ob vorhandene Gliederungsbereiche entfernt oder beibehalten werden und ob der Gliederungsbereich standardmäßig erweitert oder reduziert wird.

## <a name="add-client-controlled-outline-regions"></a>Hinzufügen von clientgesteuerten Gliederungsbereichen
 Verwenden Sie diesen Ansatz, um clientgesteuerte (oder intelligente) Gliederungen wie die von den [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] und [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] Sprachdiensten verwendeten zu implementieren. Ein Sprachdienst, der seine eigene Gliederung verwaltet, überwacht den Textpufferinhalt, um alte Gliederungsbereiche zu zerstören, wenn sie ungültig werden, und um bei Bedarf neue Gliederungsbereiche zu erstellen.

### <a name="to-implement-a-client-controlled-outline-region"></a>So implementieren Sie eine clientgesteuerte Gliederungsregion

1. Rufen `QueryService` <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>Sie nach . Dadurch wird ein <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>Zeiger auf zurückgegeben.

2. Rufen <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>Sie auf, und übergeben Sie einen Zeiger für einen bestimmten Textpuffer. Dadurch wird bestimmt, ob bereits eine ausgeblendete Textsitzung für den Puffer vorhanden ist.

3. Wenn bereits eine Textsitzung vorhanden ist, müssen Sie keine Textsitzung <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> erstellen, und es wird ein Zeiger auf das vorhandene Objekt zurückgegeben. Verwenden Sie diesen Zeiger, um Gliederungsbereiche aufzuzählen und zu erstellen. Rufen Sie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> andernfalls auf, um eine ausgeblendete Textsitzung für den Puffer zu erstellen. Ein Zeiger auf <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> das Objekt wird zurückgegeben.

    > [!NOTE]
    > Wenn Sie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A>aufrufen, können Sie einen versteckten <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient> Textclient (d. h. ein Objekt) angeben. Dieser Client benachrichtigt Sie, wenn ein ausgeblendeter Text oder Gliederungsbereich vom Benutzer erweitert oder reduziert wird.

4. Parameter <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> Aufrufstruktur): Geben Sie <xref:Microsoft.VisualStudio.TextManager.Interop.HIDDEN_REGION_TYPE> einen `iType` Wert <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> von im Element der Struktur an, um anzugeben, dass Sie einen Gliederungsbereich anstelle eines ausgeblendeten Bereichs erstellen. Geben Sie an, ob die Region im `dwBehavior` Element <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> der Struktur clientgesteuert oder editorgesteuert ist. Ihre smartoutline-Implementierung kann eine Mischung aus Editor- und clientgesteuerten Gliederungsbereichen enthalten. Geben Sie den Bannertext an, der `pszBanner` angezeigt wird, wenn der Gliederungsbereich im Element der <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> Struktur reduziert wird, z. B. "...". Der Standardbannertext des Editors für einen ausgeblendeten Bereich ist "...".

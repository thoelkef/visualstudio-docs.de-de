---
title: Bereitstellung von verdeckter Textunterstützung im Legacy-Sprachdienst
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- hidden text, supporting
- editors [Visual Studio SDK], hidden text
- language services, implementing hidden text regions
ms.assetid: 1c1dce9f-bbe2-4fc3-a736-5f78a237f4cc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8a9d5fe85932f87eb68b6b5a0f5868ebbf8f2b5f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707932"
---
# <a name="how-to-provide-hidden-text-support-in-a-legacy-language-service"></a>Gewusst wie: Bereitstellen von verdeckter Textunterstützung in einem älteren Sprachdienst
Sie können ausgeblendete Textbereiche zusätzlich zu Gliederungsbereichen erstellen. Ausgeblendete Textbereiche können clientgesteuert oder editorgesteuert sein und werden verwendet, um einen Textbereich vollständig auszublenden. Der Editor zeigt einen ausgeblendeten Bereich als horizontale Linien an. Ein Beispiel hierfür ist die **Nur-Skript-Ansicht** im HTML-Editor.

## <a name="to-implement-a-hidden-text-region"></a>So implementieren Sie einen ausgeblendeten Textbereich

1. Rufen `QueryService` <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>Sie nach .

     Dadurch wird ein <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>Zeiger auf zurückgegeben.

2. Rufen <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>Sie auf, und übergeben Sie einen Zeiger für einen bestimmten Textpuffer. Dadurch wird bestimmt, ob bereits eine ausgeblendete Textsitzung für den Puffer vorhanden ist.

3. Wenn bereits eines vorhanden ist, müssen Sie keins erstellen, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> und es wird ein Zeiger auf das vorhandene Objekt zurückgegeben. Verwenden Sie diesen Zeiger, um ausgeblendete Textbereiche aufzuzählen und zu erstellen. Rufen Sie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> andernfalls auf, um eine ausgeblendete Textsitzung für den Puffer zu erstellen.

     Ein Zeiger auf <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> das Objekt wird zurückgegeben.

    > [!NOTE]
    > Wenn Sie `CreateHiddenTextSession`aufrufen, können Sie einen ausgeblendeten Textclient angeben (d. h., <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient>) Der ausgeblendete Textclient benachrichtigt Sie, wenn ausgeblendeter Text oder Diegliederung vom Benutzer erweitert oder reduziert wird.

4. Rufen <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> Sie auf, um jeweils einen oder mehrere neue Gliederungsbereiche hinzuzufügen, und geben Sie die folgenden Informationen im Parameter `reHidReg` (<xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>) an:

    1. Geben Sie `hrtConcealed` einen `iType` Wert von <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> im Element der Struktur an, um anzugeben, dass Sie einen ausgeblendeten Bereich und nicht einen Gliederungsbereich erstellen.

        > [!NOTE]
        > Wenn verdeckte Bereiche ausgeblendet sind, zeigt der Editor automatisch Zeilen um die ausgeblendeten Bereiche an, um deren Anwesenheit anzuzeigen.

    2. Geben Sie an, ob die Region in `dwBehavior` den <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> Membern der Struktur clientgesteuert oder editorgesteuert ist. Ihre smarte Gliederungsimplementierung kann eine Mischung aus Editor- und Client-gesteuerten Umriss- und ausgeblendeten Textbereichen enthalten.

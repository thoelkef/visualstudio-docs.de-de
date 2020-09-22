---
title: 'Vorgehensweise: Bereitstellen von ausgeblendeter Text Unterstützung in einem Legacy Sprachdienst | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- hidden text, supporting
- editors [Visual Studio SDK], hidden text
- language services, implementing hidden text regions
ms.assetid: 1c1dce9f-bbe2-4fc3-a736-5f78a237f4cc
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 82b8ae72fec0d13eb9da9226945d9a55b60ce186
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841040"
---
# <a name="how-to-provide-hidden-text-support-in-a-legacy-language-service"></a>Gewusst wie: Unterstützen von ausgeblendetem Text in einem Legacysprachdienst
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Sie können neben Gliederungs Bereiche auch ausgeblendete Textbereiche erstellen. Ausgeblendete Textbereiche können vom Client gesteuert oder Editor gesteuert werden, und Sie werden verwendet, um einen Textbereich vollständig auszublenden. Der Editor zeigt einen ausgeblendeten Bereich als horizontale Linien an. Ein Beispiel hierfür ist die nur Skript Ansicht im HTML-Editor.  
  
## <a name="procedure"></a>Prozedur  
  
#### <a name="to-implement-a-hidden-text-region"></a>So implementieren Sie einen ausgeblendeten Textbereich  
  
1. Wird `QueryService` für aufgerufen <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> .  
  
     Dies gibt einen Zeiger auf zurück <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager> .  
  
2. Ruft <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A> auf und übergibt einen Zeiger für einen angegebenen Text Puffer. Hiermit wird bestimmt, ob für den Puffer bereits eine ausgeblendete Text Sitzung vorhanden ist.  
  
3. Wenn bereits eine vorhanden ist, müssen Sie keine erstellen, und es wird ein Zeiger auf das vorhandene <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> Objekt zurückgegeben. Verwenden Sie diesen Zeiger, um ausgeblendete Textbereiche aufzulisten und zu erstellen. Andernfalls rufen <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> Sie auf, um eine ausgeblendete Text Sitzung für den Puffer zu erstellen.  
  
     Ein Zeiger auf das- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> Objekt wird zurückgegeben.  
  
    > [!NOTE]
    > Wenn Sie aufgerufen `CreateHiddenTextSession` haben, können Sie einen ausgeblendeten Text Client angeben (d <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient> . h.). Der verborgene Text Client benachrichtigt Sie, wenn ausgeblendeter Text oder Gliederung vom Benutzer erweitert oder reduziert wird.  
  
4. Aufrufen <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> , um eine oder mehrere neue Gliederungs Bereiche gleichzeitig hinzuzufügen. dabei werden die folgenden Informationen im `reHidReg` <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> Parameter () angegeben:  
  
    1. Geben `hrtConcealed` Sie den Wert im- `iType` Member der- <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> Struktur an, um anzugeben, dass Sie einen ausgeblendeten Bereich anstelle eines Gliederungs Bereichs erstellen.  
  
        > [!NOTE]
        > Wenn verborgene Bereiche ausgeblendet sind, zeigt der Editor automatisch Zeilen um die ausgeblendeten Bereiche an, um deren Anwesenheit anzuzeigen.  
  
    2. Geben Sie an, ob der Bereich in den Elementen der Struktur vom Client gesteuert oder vom Editor gesteuert wird `dwBehavior` <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> . Ihre intelligente Gliederungs Implementierung kann eine Mischung aus Editor-und Client gesteuerter Kontur und ausgeblendeten Textbereichen enthalten.

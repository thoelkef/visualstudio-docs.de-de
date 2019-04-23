---
title: 'Vorgehensweise: Unterstützen der Gliederung in einem Legacysprachdienst | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], collapse to definitions command
- language services, supporting Collapse to Definitions command
- hidden text, Collapse to Definitions command
ms.assetid: bb6e74c3-93e4-4ef7-afc7-1c9b342f083b
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f15499d4075491c8eab8660fb51fba49b983f77a
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60103530"
---
# <a name="how-to-support-outlining-in-a-legacy-language-service"></a>Vorgehensweise: Unterstützen der Gliederung in einem Legacysprachdienst
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Gliederung wird zum Erweitern oder reduzieren die verschiedene Regionen des Texts. Die Möglichkeit Gliederung wird verwendet, kann durch verschiedene Sprachen unterschiedlich definiert werden. Weitere Informationen finden Sie unter [Gliedern](../../ide/outlining.md).  
  
 Legacy-Sprachdienste werden als Teil eines VSPackage implementiert, aber die neuere Methode zum Implementieren von Sprache-Service-Features ist die Verwendung von MEF-Erweiterungen. Um mehr über die neue Methode zum Implementieren der Gliederung zu suchen, finden Sie unter [Exemplarische Vorgehensweise: Gliedern](../../extensibility/walkthrough-outlining.md).  
  
> [!NOTE]
>  Es wird empfohlen, dass Sie nun den neuen Editor API so bald wie möglich zu verwenden. Dies verbessert die Leistung des Sprachdiensts und können Sie neue Features im Editor nutzen.  
  
 Das folgende Beispiel veranschaulicht, wie Sie mit diesem Befehl für den Sprachdienst zu unterstützen.  
  
### <a name="to-support-outlining"></a>Zur Unterstützung der Gliederung  
  
1. Implementieren <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage> auf das sprachendienstobjekt.  
  
2. Rufen Sie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> auf das aktuelle gliederungssitzungsobjekt neue Gliederungsbereiche hinzufügen.  
  
## <a name="robust-programming"></a>Stabile Programmierung  
 Wenn ein Benutzer auswählt **reduzieren auf Definitionen** auf die **Gliedern** Menü, die IDE-Aufrufe <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage.CollapseToDefinitions%2A> auf den Sprachdienst.  
  
 Wenn diese Methode aufgerufen wird, übergibt die IDE in einer <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> Zeiger (einen Zeiger auf einen Textpuffer) und ein <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession> (einen Zeiger auf die aktuelle Sitzung für die Gliederung).  
  
 Rufen Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> -Methode für mehrere Gliederungsbereiche durch Angeben dieser Regionen in den `rgOutlnReg` Parameter. Die `rgOutlnReg` -Parameter ist ein <xref:Microsoft.VisualStudio.TextManager.Interop.NewOutlineRegion> Struktur. So können Sie zum Angeben von verschiedenen Merkmale des ausgeblendeten Bereichs, z. B., ob eine bestimmte Region erweitert oder reduziert ist.  
  
> [!NOTE]
>  Achten Sie darauf, dass zum Ausblenden von neue-Zeile-Zeichen. Ausgeblendeten Text sollten ab dem Anfang der ersten Zeile bis zum letzten Zeichen der letzten Zeile in einem Abschnitt, sodass das abschließende neue-Zeile-Zeichen sichtbar erweitern.  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Unterstützen der ausgeblendeten Text in einem Legacysprachdienst](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)   
 [Vorgehensweise: Geben Sie die Unterstützung für erweiterte Gliederungen in einem Legacysprachdienst](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)

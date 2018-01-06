---
title: "Vorgehensweise: unterstützen Gliederung im ein Legacy-Sprachdienst | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], collapse to definitions command
- language services, supporting Collapse to Definitions command
- hidden text, Collapse to Definitions command
ms.assetid: bb6e74c3-93e4-4ef7-afc7-1c9b342f083b
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: fa57b0d09cb8422a9dde1f70306d2f3808b0384e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-support-outlining-in-a-legacy-language-service"></a>Vorgehensweise: unterstützen Gliederung im ein Legacy-Sprachdienst
Gliederung dient zum Erweitern oder reduzieren die verschiedenen Bereiche des Texts. Die Weise Gliederung wird verwendet, kann von verschiedenen Sprachen unterschiedlich definiert werden. Weitere Informationen finden Sie unter [Gliedern](../../ide/outlining.md).  
  
 Dienste für Legacy-Sprachen werden als Teil eines VSPackage implementiert, aber die neuere Methode zum Implementieren von Dienstfunktionen Sprache ist die Verwendung von MEF-Erweiterungen. Weitere Informationen über die neue Methode zum Implementieren, Gliederung, finden Sie unter [Exemplarische Vorgehensweise: Gliedern](../../extensibility/walkthrough-outlining.md).  
  
> [!NOTE]
>  Es wird empfohlen, dass Sie beginnen, den neuen Editor API so bald wie möglich verwenden. Dies verbessert die Leistung des Sprachdiensts und können Sie neue Features im Editor nutzen.  
  
 Das folgende Beispiel zeigt, wie mit diesem Befehl für den Sprachdienst unterstützt.  
  
### <a name="to-support-outlining"></a>Zur Unterstützung der Gliederung  
  
1.  Implementieren <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage> in Ihrer Sprache Dienstobjekt.  
  
2.  Rufen Sie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> für das aktuelle Gliederungsmodus Sitzungsobjekt neue Gliederungsbereiche hinzufügen.  
  
## <a name="robust-programming"></a>Stabile Programmierung  
 Wenn ein Benutzer wählt **nur Definitionen** auf die **Gliedern** Menü, ruft die IDE <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage.CollapseToDefinitions%2A> für Ihren Sprachdienst.  
  
 Wenn diese Methode aufgerufen wird, werden in die IDE übergeben ein <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> Zeiger (ein Zeiger auf einen Textpuffer) und ein <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession> (ein Zeiger auf die aktuelle Sitzung Gliederung).  
  
 Sie erreichen die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> Methode für mehrere Gliederungsbereiche durch Angeben dieser Regionen in den `rgOutlnReg` Parameter. Die `rgOutlnReg` Parameter ist ein <xref:Microsoft.VisualStudio.TextManager.Interop.NewOutlineRegion> Struktur. So können Sie zum Angeben von verschiedenen Merkmale des ausgeblendeten Region, z. B., ob eine bestimmte Region erweitert oder reduziert ist.  
  
> [!NOTE]
>  Achten Sie darauf, dass zum Ausblenden von neue-Zeile-Zeichen. Ausgeblendeten Text sollte ab dem Anfang der ersten Zeile bis zum letzten Zeichen der letzten Zeile in einem Abschnitt, sodass das endgültige neue-Zeile-Zeichen angezeigt sein.  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: unterstützen ausgeblendetem Text in einen Legacy-Sprachdienst](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)   
 [Gewusst wie: Bereitstellen von Unterstützung für erweiterte Gliederungen in einem Legacysprachdienst](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)
---
title: Syntaxfarben in benutzerdefinierten Editoren | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], custom - syntax coloring
ms.assetid: 74900b9a-baef-432a-8231-4568fb5e19ad
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6a2165d51f77103ad7f6e69a20b5b73ef04429db
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47511597"
---
# <a name="syntax-coloring-in-custom-editors"></a>Syntaxfarben in benutzerdefinierten Editoren
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Syntax Syntaxfarben in benutzerdefinierten Editoren](https://docs.microsoft.com/visualstudio/extensibility/syntax-coloring-in-custom-editors).  
  
Visual Studio-Umgebung SDK-Editoren, einschließlich der Kern-Editor, verwenden Sie Sprachdienste bestimmte syntaktische Elemente zu identifizieren und mit angegebenen Farben für eine angegebene Dokumentenansicht anzeigen.  
  
## <a name="colorization-requirements"></a>Farbliche Kennzeichnung von Anforderungen  
 Alle Editoren, die einer editortooloptionsseite des Sprachdiensts Farbauswahl implementieren müssen:  
  
1.  Verwenden Sie ein Objekt, das <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> zum Verwalten der Text, der einzufärbenden und ein Objekt, das <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> zum Dokument anzeigen des Texts.  
  
2.  Erhalten Sie eine Schnittstelle zu einem bestimmten Sprachdienst, durch die VSPackage Dienstanbieter, die mit den Sprachen des Diensts identifizierende GUID Abfragen.  
  
3.  Rufen Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> Methode die objektimplementierung <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>. Diese Methode ordnet den Sprachdienst mit der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> -Implementierung, die das VSPackage verwendet, um den Text zu verwalten, die farbig markiert werden.  
  
## <a name="core-editor-usage-of-a-language-services-colorizer"></a>Verwendung einer Editortooloptionsseite des Sprachdiensts Farbauswahl-Kern-Editor  
 Wenn ein Sprachdienst mit einem Farbauswahl von einer Instanz von der Kern-Editor, für die Analyse und Rendern von Text von einer editortooloptionsseite des Sprachdiensts Farbauswahl abgerufen wird, wird automatisch ohne weiteren Eingriff Ihrerseits.  
  
 Die IDE transparent:  
  
-   Ruft die Farbauswahl je nach Bedarf zu analysieren, Text zu analysieren, da sie hinzugefügt oder werden, in der Implementierung von geändert <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>.  
  
-   Stellt sicher, dass die Anzeige der Dokumentenansicht gebotenen vom die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> -Implementierung wird aktualisiert und neu gezeichnet, anhand der Informationen, die von der Farbauswahl zurückgegeben.  
  
## <a name="non-core-editor-usage-of-a-language-services-colorizer"></a>Nicht zum Kern-Editor-Nutzung einer Editortooloptionsseite des Sprachdiensts Farbauswahl  
 Nicht-Kern-Editor-Instanzen können sich auch auf einer editortooloptionsseite des Sprachdiensts Syntax farbliche Kennzeichnung von Dienst, aber sie müssen explizit abgerufen werden, und des Diensts Farbauswahl gelten, und neu zu zeichnen ihren Ansichten des Dokuments selbst.  
  
 Zu diesem Zweck müssen einen nicht zum Kern-Editor zum:  
  
1.  Abrufen einer editortooloptionsseite des Sprachdiensts Farbauswahl-Objekt (implementiert `T:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer` und <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2>). Das VSPackage wird durch Aufrufen der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> -Methode für den Sprachdienst-Schnittstelle.  
  
2.  Rufen Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> Methode, um anzufordern, dass es sich bei ein bestimmter Textabschnitt farbig markiert werden.  
  
     Die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> Methode gibt ein Array von Werten zurück, eine für jeden Buchstaben im Text umfassen farbig hervorgehoben wird. Er gibt außerdem den Textabschnitt als einen bestimmten Typ kolorierbaren Elements, z. B. einen Kommentar, Schlüsselwort oder Datentyp.  
  
3.  Verwenden Sie die farbliche Kennzeichnung von Informationen vom <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> neu zu zeichnen und den Text anzuzeigen.  
  
> [!NOTE]
>  Zusätzlich zur Verwendung einer editortooloptionsseite des Sprachdiensts Farbauswahl, können eine VSPackage die allgemeinen Text syntaxkennzeichnung Mechanismus für Visual Studio-Umgebung SDK verwenden. Weitere Informationen zu diesen Mechanismus, finden Sie unter [Verwenden von Schriftarten und Farben](../extensibility/using-fonts-and-colors.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Syntaxfarben in einem Legacysprachdienst](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)   
 [Implementieren von Syntaxfarben](../extensibility/internals/implementing-syntax-coloring.md)   
 [Vorgehensweise: Verwenden Sie die integrierten kolorierbaren Elemente](../extensibility/internals/how-to-use-built-in-colorable-items.md)   
 [Benutzerdefinierte einfärbbare Elemente](../extensibility/internals/custom-colorable-items.md)


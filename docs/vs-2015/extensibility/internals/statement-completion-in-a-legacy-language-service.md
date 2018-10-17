---
title: Anweisungsvervollständigung in einem Legacysprachdienst | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- statement completion
- language services, statement completion
ms.assetid: 617439dc-3f0e-4e5f-b346-3e4e7fcf3c1b
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ab481ff516cb6b10a4330b4255ea3e75a333f3da
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49175057"
---
# <a name="statement-completion-in-a-legacy-language-service"></a>Anweisungsvervollständigung in einem Legacysprachdienst
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Anweisungsvervollständigung wird mit dem der Sprachdienst Benutzern, die abgeschlossen wird hilft, ein Programmiersprachen-Schlüsselwort oder das Element, das sie begonnen haben, in der Kern-Editor eingeben. In diesem Thema wird erläutert, wie Anweisungsvervollständigung funktioniert und wie er in den Sprachdienst implementiert.  
  
 Legacy-Sprachdienste werden als Teil eines VSPackage implementiert, aber die neuere Methode zum Implementieren von Sprache-Service-Features ist die Verwendung von MEF-Erweiterungen. Weitere Informationen zu die neue Methode zum Implementieren der Anweisungsvervollständigung finden Sie unter [Exemplarische Vorgehensweise: Anzeigen von Anweisungsvervollständigung](../../extensibility/walkthrough-displaying-statement-completion.md).  
  
> [!NOTE]
>  Es wird empfohlen, dass Sie nun den neuen Editor API so bald wie möglich zu verwenden. Dies verbessert die Leistung des Sprachdiensts und können Sie neue Features im Editor nutzen.  
  
## <a name="implementing-statement-completion"></a>Implementieren von Anweisungsvervollständigung  
 Im Kern-Editor wird aktiviert, Anweisungsvervollständigung eine spezielle Benutzeroberfläche, die interaktiv hilft Ihnen, noch einfacher und schnell Code zu schreiben. Anweisungsvervollständigung hilft mit relevanten Objekte oder Klassen, wenn sie benötigt werden, wodurch Sie bestimmte Elemente daran erinnern zu müssen, oder müssen in einem Hilfethema für den Verweis nachgeschlagen werden vermieden werden.  
  
 Um Anweisungsvervollständigung zu implementieren, müssen Ihre Sprache einen Trigger für die Buildfertigstellung Anweisung analysiert werden kann. Z. B. [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] verwendet einen Operator Punkt (.), während [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] verwendet einen Pfeil (->)-Operator. Ein Sprachdienst kann mehr als ein Trigger verwenden, um Anweisungsvervollständigung initiieren zu können. Diese Trigger werden im Befehlsfilter so programmiert.  
  
## <a name="command-filters-and-triggers"></a>-Befehlsfilter und Trigger  
 Befehl Filter fangen Vorkommen der Auslöser oder Trigger. Um die Ansicht der Befehlsfilter hinzuzufügen, implementieren die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Schnittstelle, und fügen Sie es an die Ansicht durch Aufrufen der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> Methode. Sie können den gleichen Befehlsfilter (<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>) für alle Aspekte des Sprachdiensts, wie Anweisungsvervollständigung, fehlermarker und methodentipps. Weitere Informationen finden Sie unter [Befehlen von Legacysprachdiensten abfangen](../../extensibility/internals/intercepting-legacy-language-service-commands.md).  
  
 Wenn der Trigger im Editor eingegeben wird – insbesondere den Textpuffer, der Sprachdienst ruft dann die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> Methode. Dies bewirkt, dass den Editor in der Benutzeroberfläche anzuzeigen, damit der Benutzer die Anweisung Abschluss Kandidaten auswählen kann. Diese Methode müssen Sie implementieren <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> und <xref:Microsoft.VisualStudio.TextManager.Interop.UpdateCompletionFlags> Flags, die als Parameter. In einem Listenfeld Scrollen wird die Liste der Vervollständigungselemente angezeigt. Wie der Benutzer eingeben weiterhin, wird die Auswahl innerhalb des Listenfelds aktualisiert, um widerzuspiegeln, dass die bestmögliche Übereinstimmung auf die letzten Zeichen eingegeben. Der Kern-Editor implementiert, die Benutzeroberfläche für die Anweisungsvervollständigung, jedoch muss der Sprachdienst implementieren die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> Schnittstelle, um einen Satz von kandidatenelemente als Abschluss für die Anweisung zu definieren.  
  
## <a name="see-also"></a>Siehe auch  
 [Abfangen von Befehlen von Legacysprachdiensten](../../extensibility/internals/intercepting-legacy-language-service-commands.md)


---
title: "Anweisungsvervollständigung im ein Legacy-Sprachdienst | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- statement completion
- language services, statement completion
ms.assetid: 617439dc-3f0e-4e5f-b346-3e4e7fcf3c1b
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 7208d38966e2caa9f9510c48c34952742d06c1b3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="statement-completion-in-a-legacy-language-service"></a>Anweisungsvervollständigung im ein Legacy-Sprachdienst
Anweisungsvervollständigung ist der Prozess, durch den der Sprachdienst hilft Benutzern, die abgeschlossen wird, ein Schlüsselwort oder ein Element, die sie die Eingabe im Editor Core gestartet wurden. In diesem Thema wird erläutert, wie Anweisungsvervollständigung funktioniert und wie es in Ihrem Sprachdienst implementiert.  
  
 Dienste für Legacy-Sprachen werden als Teil eines VSPackage implementiert, aber die neuere Methode zum Implementieren von Dienstfunktionen Sprache ist die Verwendung von MEF-Erweiterungen. Weitere Informationen über die neue Methode für die Anweisungsvervollständigung implementieren, finden Sie unter [Exemplarische Vorgehensweise: Anzeigen von Anweisungsvervollständigung](../../extensibility/walkthrough-displaying-statement-completion.md).  
  
> [!NOTE]
>  Es wird empfohlen, dass Sie beginnen, den neuen Editor API so bald wie möglich verwenden. Dies verbessert die Leistung des Sprachdiensts und können Sie neue Features im Editor nutzen.  
  
## <a name="implementing-statement-completion"></a>Implementieren von Anweisungsvervollständigung  
 Im Editor Core aktiviert Anweisungsvervollständigung eine spezielle Benutzeroberfläche, die interaktiv können Sie leichter und schnell Code schreiben. Dies hilft Anweisungsvervollständigung Anzeigen von relevanten Objekte oder Klassen, wenn sie benötigt werden, wodurch Sie vermieden werden müssen, die in einem Hilfethema für den Verweis gesucht oder bestimmte Elemente merken müssen.  
  
 Um Anweisungsvervollständigung zu implementieren, benötigen Ihre Sprache einen Anweisung Abschluss Trigger analysiert werden kann. Beispielsweise [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] verwendet einen Operator Punkt (.) während [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] verwendet einen Pfeil (->)-Operator. Ein Sprachdienst kann mehrere Trigger verwenden, um Anweisungsvervollständigung zu initiieren. Diese Trigger werden im Befehlsfilter programmiert.  
  
## <a name="command-filters-and-triggers"></a>-Befehlsfilter und Trigger  
 Befehl Filter abfangen Vorkommen der Trigger oder Trigger. Um die Ansicht den Befehlsfilter hinzuzufügen, implementieren die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Schnittstelle, und fügen Sie es an die Ansicht durch Aufrufen der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> Methode. Sie können den gleichen Befehlsfilter (<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>) für alle Aspekte des Sprachdiensts, wie z. B. Fehler Marker, Anweisungsvervollständigung und Methode Tipps. Weitere Informationen finden Sie unter [abfangen Legacy-Dienst Sprachbefehle](../../extensibility/internals/intercepting-legacy-language-service-commands.md).  
  
 Bei der Eingabe des Triggers im Editor – insbesondere den Textpuffer – Ihre Sprachdienst ruft dann die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> Methode. Dies bewirkt, dass den Editor, um die Benutzeroberfläche zu öffnen, damit der Benutzer aus der Anweisung Abschluss Kandidaten auswählen kann. Diese Methode erfordert, dass Sie implementieren <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> und <xref:Microsoft.VisualStudio.TextManager.Interop.UpdateCompletionFlags> Flags als Parameter. Die Liste der Elemente der Abschluss des Vorgangs wird in einem fortlaufenden Listenfeld angezeigt. Auf, da der Benutzer eingeben weiterhin, wird die Auswahl im Listenfeld aktualisiert, um widerzuspiegeln, dass die bestmögliche Übereinstimmung mit den neuesten Zeichen eingegeben. Die Core-Editor implementiert die Benutzeroberfläche für die Anweisungsvervollständigung, aber der Sprachdienst muss implementieren die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> Schnittstelle, um einen Satz von Kandidaten Abschluss Elemente für die Anweisung zu definieren.  
  
## <a name="see-also"></a>Siehe auch  
 [Abfangen von Befehlen von Legacysprachdiensten](../../extensibility/internals/intercepting-legacy-language-service-commands.md)
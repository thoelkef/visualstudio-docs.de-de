---
title: "Abschluss der Anweisung in eine Legacy-Sprachdienst | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Anweisungsvervollständigung"
  - "Language Services Anweisungsabschluss"
ms.assetid: 617439dc-3f0e-4e5f-b346-3e4e7fcf3c1b
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Abschluss der Anweisung in eine Legacy-Sprachdienst
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Anweisungsabschluss ist der Prozess, durch den der Sprachdienst hilft Benutzern, die abgeschlossen wird, ein Schlüsselwort oder ein Element, die sie eingeben, die im primären Editor gestartet wurden. In diesem Thema wird erläutert, wie Anweisungsabschluss funktioniert und wie es im Language\-Dienst implementiert.  
  
 Ältere Sprache Services werden als Teil eines VSPackage implementiert, aber der neuere Weg zum Implementieren von Language Service ist die Verwendung von MEF\-Erweiterungen. Weitere Informationen über die neue Methode zum Implementieren der Anweisungsabschluss finden Sie unter [Exemplarische Vorgehensweise: Anzeigen von Anweisungsabschluss](../../extensibility/walkthrough-displaying-statement-completion.md).  
  
> [!NOTE]
>  Es wird empfohlen, dass Sie beginnen, den neuen Editor\-API so bald wie möglich zu verwenden. Dies verbessert die Leistung des Sprachdiensts und können Sie die neue Editorfunktionen nutzen.  
  
## Implementieren der Anweisungsabschluss  
 Im Kern\-Editor aktiviert Anweisungsabschluss eine spezielle Benutzeroberfläche, die interaktiv können Sie einfacher und schneller Code schreiben. Anweisungsabschluss hilft mit relevanten Objekte oder Klassen bei Bedarf, wodurch Sie zum Nachschlagen in einem Verweis Hilfethema müssen oder bestimmte Elemente merken müssen vermieden werden.  
  
 Zum Abschluss der Anweisung zu implementieren, müssen Ihre Sprache einen Anweisung Abschluss Trigger analysiert werden kann. Z. B. [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] verwendet einen Punkt \(.\) Operator, während [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] verwendet einen Pfeil \(\-\>\)\-Operator. Mehrere Trigger können eine Sprachdienst Anweisungsabschluss initiieren. Diese Trigger werden im Befehlsfilter programmiert.  
  
## Befehlsfilter und Trigger  
 Befehl Filter fängt Vorkommen der oder die Trigger. Um die Ansicht den Befehlsfilter hinzuzufügen, implementieren die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Schnittstelle, und fügen Sie es an die Ansicht durch Aufrufen der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> Methode. Können Sie den gleichen Befehlsfilter \(<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>\) für alle Aspekte des Sprachdiensts, z. B. Anweisungsabschluss, Fehler Marker und Methode Tipps. Weitere Informationen finden Sie unter [Abfangen von Legacy\-Dienst Sprachbefehle](../../extensibility/internals/intercepting-legacy-language-service-commands.md).  
  
 Wenn der Trigger im Editor eingegeben wird – insbesondere Textpuffer – der Sprachdienst ruft dann die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> Methode. Dadurch wird den Editor, um die Benutzeroberfläche anzuzeigen, damit der Benutzer aus der Anweisung Abschluss Kandidaten auswählen kann. Diese Methode erfordert, dass Sie implementieren <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> und die <xref:Microsoft.VisualStudio.TextManager.Interop.UpdateCompletionFlags> Flags als Parameter. Die Liste der Elemente der Abschluss des Vorgangs wird in einem fortlaufenden Listenfeld angezeigt. Wie der Benutzer eingeben weiterhin, wird die Auswahl im Listenfeld aktualisiert am ehesten entspricht dem letzten Zeichen eingegeben. Die Core\-Editor wird die Benutzeroberfläche für den Anweisungsabschluss implementiert, aber der Sprachdienst muss implementieren die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> Schnittstelle, um einen Satz von Kandidaten Abschluss Elementen für die Anweisung zu definieren.  
  
## Siehe auch  
 [Abfangen von Legacy\-Dienst Sprachbefehle](../../extensibility/internals/intercepting-legacy-language-service-commands.md)
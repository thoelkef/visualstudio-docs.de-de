---
title: Word-Abschluss in einen Legacy-Sprachdienst | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], IntelliSense Complete Word
- IntelliSense, Complete Word
- Complete Word
ms.assetid: 0ace5ac3-f9e1-4e6d-add4-42967b1f96a6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 72ddf4e7c755fdecf562f4c190abfb145e6f9819
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="word-completion-in-a-legacy-language-service"></a>Wortvervollständigung in einen Legacy-Sprachdienst
Wortvervollständigung füllt die fehlenden Zeichen für eine teilweise typisiertes Wort. Ist nur eine mögliche Abschluss, ist das Wort abgeschlossen, wenn die Beendigung Zeichen eingegeben wird. Wenn die partielle Wort mehr als eine Möglichkeit übereinstimmt, wird eine Liste von möglichen Abschlüssen angezeigt. Ein Abschluss Zeichen kann jedes Zeichen sein, die nicht für Bezeichner verwendet wird.  
  
 Dienste für Legacy-Sprachen werden als Teil eines VSPackage implementiert, aber die neuere Methode zum Implementieren von Dienstfunktionen Sprache ist die Verwendung von MEF-Erweiterungen. Wenn Sie mehr erfahren möchten, finden Sie unter [Erweiterung des Editors und des Sprachdienste](../../extensibility/extending-the-editor-and-language-services.md).  
  
> [!NOTE]
>  Es wird empfohlen, dass Sie beginnen, den neuen Editor API so bald wie möglich verwenden. Dies verbessert die Leistung des Sprachdiensts und können Sie neue Features im Editor nutzen.  
  
## <a name="implementation-steps"></a>Implementierungsschritten  
  
1.  Wenn der Benutzer wählt **Wort vervollständigen** aus der **IntelliSense** im Menü der <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> Befehl an der Sprachdienst gesendet wird.  
  
2.  Die <xref:Microsoft.VisualStudio.Package.ViewFilter> Klasse fängt den Befehl und ruft die <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> Methode mit dem Grund der Analyse von <xref:Microsoft.VisualStudio.Package.ParseReason>.  
  
3.  Die <xref:Microsoft.VisualStudio.Package.Source> -Klasse dann ruft der <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Methode zum Abrufen der Liste der möglichen Word Abschlüssen und klicken Sie dann angezeigt, die die Wörter in einer QuickInfo Liste mit den <xref:Microsoft.VisualStudio.Package.CompletionSet> Klasse.  
  
     Es ist nur ein übereinstimmendes Wort, das <xref:Microsoft.VisualStudio.Package.Source> Klasse abgeschlossen ist, das Wort.  
  
 Alternativ können Sie der Scanner der Triggerwert zurück <xref:Microsoft.VisualStudio.Package.TokenTriggers> , wenn das erste Zeichen eines Bezeichners typisiert ist, die <xref:Microsoft.VisualStudio.Package.Source> Klasse erkennt dies und ruft die <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> Methode mit dem Grund der Analyse von <xref:Microsoft.VisualStudio.Package.ParseReason>. In diesem Fall muss der Parser das Vorhandensein eines Elements Auswahl Zeichens erkennen und geben Sie eine Liste von Elementen.  
  
## <a name="enabling-support-for-the-complete-word"></a>Aktivieren der Unterstützung für das Wort vervollständigen  
 Zum Aktivieren der Unterstützung für Word Abschluss Satz der `CodeSense` benannter Parameter übergeben, um die <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> Benutzerattribut, die die deutschsprachige Paket zugeordnet. Dadurch wird die <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> Eigenschaft auf die <xref:Microsoft.VisualStudio.Package.LanguagePreferences> Klasse.  
  
 Der Parser muss eine Liste der Deklarationen zurückgeben, als Antwort auf den Analyse-ursachenwert <xref:Microsoft.VisualStudio.Package.ParseReason>, für wortvervollständigung ausgeführt werden.  
  
## <a name="implementing-complete-word-in-the-parsesource-method"></a>Implementieren Wort vervollständigen in der ParseSource-Methode  
 Für ' wortvervollständigung die <xref:Microsoft.VisualStudio.Package.Source> -Klasse ruft die <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A> Methode für die <xref:Microsoft.VisualStudio.Package.AuthoringScope> Klasse, um eine Liste der möglichen Word Übereinstimmungen abzurufen. Sie müssen die Liste implementieren, in einer Klasse, die abgeleitet ist die <xref:Microsoft.VisualStudio.Package.Declarations> Klasse. Finden Sie unter der <xref:Microsoft.VisualStudio.Package.Declarations> Klasse Weitere Informationen zu den Methoden, die Sie implementieren müssen.  
  
 Wenn die Liste nur ein einzelnes Wort enthält die <xref:Microsoft.VisualStudio.Package.Source> Klasse fügt automatisch das Wort anstelle des partiellen Worts. Wenn die Liste mehr als ein Wort, enthält die <xref:Microsoft.VisualStudio.Package.Source> -Klasse stellt einen Tipp-Toolliste, in dem der Benutzer die geeignete Auswahl auswählen kann.  
  
 Betrachten Sie das Beispiel auch eine <xref:Microsoft.VisualStudio.Package.Declarations> klassenimplementierung in [Member-Abschluss in einen Legacy-Sprachdienst](../../extensibility/internals/member-completion-in-a-legacy-language-service.md).
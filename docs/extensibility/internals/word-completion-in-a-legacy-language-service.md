---
title: Word-Abschluss in einem Legacysprachdienst | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], IntelliSense Complete Word
- IntelliSense, Complete Word
- Complete Word
ms.assetid: 0ace5ac3-f9e1-4e6d-add4-42967b1f96a6
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b65c1d7494e126dd9e3ee7f3d819fda66a55a3ba
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63431039"
---
# <a name="word-completion-in-a-legacy-language-service"></a>Wortvervollständigung in einem Legacysprachdienst
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Wortvervollständigung füllt das fehlenden Zeichen in eine teilweise eingegebenen Wort. Wenn nur eine mögliche abgeschlossen ist, ist das Wort abgeschlossen, wenn das Abschluss Zeichen eingegeben wird. Wenn die Wortteil mehr als eine Möglichkeit übereinstimmt, wird eine Liste der möglichen vervollständigungen angezeigt. Ein Vervollständigungszeichen kann es sich um eine beliebige Zeichen handeln, die nicht für Bezeichner verwendet wird.  
  
 Legacy-Sprachdienste werden als Teil eines VSPackage implementiert, aber die neuere Methode zum Implementieren von Sprache-Service-Features ist die Verwendung von MEF-Erweiterungen. Wenn Sie mehr erfahren möchten, finden Sie unter [Erweitern des Editors und Sprachdienste](../../extensibility/extending-the-editor-and-language-services.md).  
  
> [!NOTE]
> Es wird empfohlen, dass Sie nun den neuen Editor API so bald wie möglich zu verwenden. Dies verbessert die Leistung des Sprachdiensts und können Sie neue Features im Editor nutzen.  
  
## <a name="implementation-steps"></a>Implementierungsschritte  
  
1. Wenn der Benutzer auswählt **Wort vervollständigen** aus der **IntelliSense** im Menü der <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> Befehl gesendet wird, auf den Sprachdienst.  
  
2. Die <xref:Microsoft.VisualStudio.Package.ViewFilter> Klasse fängt die Befehls- und Aufrufe der <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> -Methode mit der Analyse Grund des <xref:Microsoft.VisualStudio.Package.ParseReason>.  
  
3. Die <xref:Microsoft.VisualStudio.Package.Source> -Klasse anschließend ruft der <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> -Methode zum Abrufen der Liste der möglichen Word vervollständigungen und zeigt dann, die die Wörter in einer QuickInfo Liste mit den <xref:Microsoft.VisualStudio.Package.CompletionSet> Klasse.  
  
    Es ist nur ein Wort nach übereinstimmendes und die <xref:Microsoft.VisualStudio.Package.Source> -Klasse abgeschlossen, wird das Wort.  
  
   Alternativ, wenn die Überprüfung der Triggerwert zurückgegeben wird <xref:Microsoft.VisualStudio.Package.TokenTriggers> , wenn das erste Zeichen eines Bezeichners typisiert ist, die <xref:Microsoft.VisualStudio.Package.Source> -Klasse erkennt dies und ruft die <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> -Methode mit der Analyse Grund des <xref:Microsoft.VisualStudio.Package.ParseReason>. In diesem Fall muss der Parser erkennen, ob ein Member-Auswahl-Zeichen vorhanden, und geben Sie eine Liste von Elementen.  
  
## <a name="enabling-support-for-the-complete-word"></a>Aktivieren der Unterstützung für das vollständige Wort  
 Aktivieren der Unterstützung für Word Vervollständigungssatz der `CodeSense` benannter Parameter, die an die <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> Benutzerattribut das Language Pack zugeordnet. Hiermit wird die <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> Eigenschaft für die <xref:Microsoft.VisualStudio.Package.LanguagePreferences> Klasse.  
  
 Der Parser muss eine Liste der Deklarationen zurückgeben, als Reaktion auf den ursachenwert Analyse <xref:Microsoft.VisualStudio.Package.ParseReason>, für wortvervollständigung ausgeführt werden.  
  
## <a name="implementing-complete-word-in-the-parsesource-method"></a>Implementieren in der Methode ParseSource Wort vervollständigen  
 Für wortvervollständigung die <xref:Microsoft.VisualStudio.Package.Source> -Klasse ruft die <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A> Methode für die <xref:Microsoft.VisualStudio.Package.AuthoringScope> Klasse zum Abrufen einer Liste der möglichen Wort übereinstimmt. Sie müssen die Liste implementieren, in eine abgeleitete Klasse, aus der <xref:Microsoft.VisualStudio.Package.Declarations> Klasse. Finden Sie unter den <xref:Microsoft.VisualStudio.Package.Declarations> -Klasse Weitere Informationen zu den Methoden, die Sie implementieren müssen.  
  
 Wenn die Liste nur ein einzelnes Wort, enthält die <xref:Microsoft.VisualStudio.Package.Source> Klasse fügt automatisch das Wort anstelle der partiellen Worts. Wenn die Liste mehr als ein Wort, enthält die <xref:Microsoft.VisualStudio.Package.Source> -Klasse stellt einen Tipp-Toolliste in dem der Benutzer die richtige Wahl auswählen kann.  
  
 Betrachten Sie das Beispiel auch eine <xref:Microsoft.VisualStudio.Package.Declarations> -klassenimplementierung in [Membervervollständigung in einem Legacysprachdienst](../../extensibility/internals/member-completion-in-a-legacy-language-service.md).

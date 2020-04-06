---
title: Word-Abschluss in einem Legacy-Sprachdienst | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], IntelliSense Complete Word
- IntelliSense, Complete Word
- Complete Word
ms.assetid: 0ace5ac3-f9e1-4e6d-add4-42967b1f96a6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 948751cde5b6b710d911a30ca26a61e5411bba4d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703172"
---
# <a name="word-completion-in-a-legacy-language-service"></a>Wortvervollständigung in einem Legacysprachdienst
Die Word-Vervollständigung füllt die fehlenden Zeichen für ein teilweise eingegebenes Wort aus. Wenn es nur einen möglichen Abschluss gibt, wird das Wort abgeschlossen, wenn das Vervollständigungszeichen eingegeben wird. Wenn das Teilwort mit mehr als einer Möglichkeit übereinstimmt, wird eine Liste möglicher Vervollständigungen angezeigt. Ein Vervollständigungszeichen kann ein beliebiges Zeichen sein, das nicht für Bezeichner verwendet wird.

 Ältere Sprachdienste werden als Teil eines VSPackage implementiert, aber die neuere Möglichkeit zum Implementieren von Sprachdienstfunktionen besteht darin, MEF-Erweiterungen zu verwenden. Weitere Informationen finden Sie unter [Erweitern des Editors und der Sprachdienste](../../extensibility/extending-the-editor-and-language-services.md).

> [!NOTE]
> Es wird empfohlen, die neue Editor-API so schnell wie möglich zu verwenden. Dadurch wird die Leistung Ihres Sprachdienstes verbessert und Sie können die neuen Editorfunktionen nutzen.

## <a name="implementation-steps"></a>Implementierungsschritte

1. Wenn der Benutzer Im **Menü IntelliSense** <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> **"Word abschließen"** auswählt, wird der Befehl an den Sprachdienst gesendet.

2. Die <xref:Microsoft.VisualStudio.Package.ViewFilter> Klasse fängt den <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> Befehl ab und ruft <xref:Microsoft.VisualStudio.Package.ParseReason>die Methode mit dem Parse-Grund von auf.

3. Die <xref:Microsoft.VisualStudio.Package.Source> Klasse ruft <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> dann die Methode auf, um die Liste möglicher Wortvervollständigungen <xref:Microsoft.VisualStudio.Package.CompletionSet> abzuspeichern, und zeigt dann die Wörter in einer QuickInfoliste mithilfe der Klasse an.

    Wenn nur ein übereinstimmendes <xref:Microsoft.VisualStudio.Package.Source> Wort vorhanden ist, schließt die Klasse das Wort ab.

   Wenn der Scanner den Triggerwert <xref:Microsoft.VisualStudio.Package.TokenTriggers> zurückgibt, wenn das erste Zeichen <xref:Microsoft.VisualStudio.Package.Source> eines Bezeichners <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> eingegeben wird, erkennt <xref:Microsoft.VisualStudio.Package.ParseReason>die Klasse dies und ruft die Methode mit dem Analysegrund von auf. In diesem Fall muss der Parser das Vorhandensein eines Memberauswahlzeichens erkennen und eine Liste der Mitglieder bereitstellen.

## <a name="enabling-support-for-the-complete-word"></a>Aktivieren der Unterstützung für das vollständige Wort
 Um die Unterstützung für `CodeSense` die Wortvervollständigung <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> zu aktivieren, legen Sie den benannten Parameter fest, der an das Benutzerattribut übergeben wird, das dem Sprachpaket zugeordnet ist. Dadurch wird <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> die <xref:Microsoft.VisualStudio.Package.LanguagePreferences> Eigenschaft für die Klasse festgelegt.

 Der Parser muss eine Liste von Deklarationen <xref:Microsoft.VisualStudio.Package.ParseReason>als Antwort auf den Analysegrundwert zurückgeben, damit die Wortvervollständigung ausgeführt werden kann.

## <a name="implementing-complete-word-in-the-parsesource-method"></a>Implementieren von Complete Word in der ParseSource-Methode
 Zur Wortvervollständigung <xref:Microsoft.VisualStudio.Package.Source> ruft <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A> die Klasse <xref:Microsoft.VisualStudio.Package.AuthoringScope> die Methode für die Klasse auf, um eine Liste möglicher Wortübereinstimmungen zu erhalten. Sie müssen die Liste in einer Klasse <xref:Microsoft.VisualStudio.Package.Declarations> implementieren, die von der Klasse abgeleitet ist. Weitere <xref:Microsoft.VisualStudio.Package.Declarations> Informationen zu den Methoden, die Sie implementieren müssen, finden Sie in der Klasse.

 Wenn die Liste nur ein einzelnes Wort enthält, fügt die <xref:Microsoft.VisualStudio.Package.Source> Klasse dieses Wort automatisch anstelle des Teilworts ein. Wenn die Liste mehr als <xref:Microsoft.VisualStudio.Package.Source> ein Wort enthält, stellt die Klasse eine QuickInfo-Liste dar, aus der der Benutzer die entsprechende Auswahl auswählen kann.

 Sehen Sie sich auch <xref:Microsoft.VisualStudio.Package.Declarations> das Beispiel einer Klassenimplementierung in [Member Completion in einem Legacy Language Service](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)an.
